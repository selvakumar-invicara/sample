### Table of Contents

-   [Types][1]
    -   [Project][2]
        -   [Properties][3]
    -   [UserCriteria][4]
        -   [Properties][5]
    -   [User][6]
        -   [Properties][7]
    -   [UserGroup][8]
        -   [Properties][9]
    -   [NamedUserItem][10]
        -   [Properties][11]
    -   [NamedUserItem][12]
        -   [Properties][13]
    -   [NamedUserItemCriteria][14]
        -   [Properties][15]
        -   [Examples][16]
    -   [NamedUserCollection][17]
    -   [NamedFileCollection][18]
    -   [NamedUserItemVersion][19]
        -   [Properties][20]
    -   [Script][21]
        -   [Properties][22]
    -   [ScriptVersion][23]
        -   [Properties][24]
    -   [UserConfig][25]
        -   [Properties][26]
    -   [UserConfigVersion][27]
        -   [Properties][28]
    -   [RelatedItem][29]
        -   [Properties][30]
    -   [FileItem][31]
        -   [Properties][32]
    -   [Ctx][33]
        -   [Properties][34]
-   [iaf-bimGfcLdr][35]
    -   [loadGraphicsStream][36]
        -   [Parameters][37]
-   [IafFile][38]
    -   [RootContainerName][39]
    -   [createContainer][40]
        -   [Parameters][41]
        -   [Examples][42]
    -   [uploadFile][43]
        -   [Parameters][44]
        -   [Examples][45]
    -   [getFileItem][46]
        -   [Parameters][47]
        -   [Examples][48]
-   [IafProj][49]
    -   [getProjects][50]
        -   [Parameters][51]
        -   [Examples][52]
    -   [create][53]
        -   [Parameters][54]
        -   [Examples][55]
    -   [addScript][56]
        -   [Parameters][57]
        -   [Examples][58]
    -   [updateScript][59]
        -   [Parameters][60]
        -   [Examples][61]
    -   [updateScriptVersion][62]
        -   [Parameters][63]
        -   [Examples][64]
    -   [deleteScript][65]
        -   [Parameters][66]
    -   [addUserConfig][67]
        -   [Parameters][68]
        -   [Examples][69]
    -   [getUserConfigs][70]
        -   [Parameters][71]
        -   [Examples][72]
    -   [updateUserConfig][73]
        -   [Parameters][74]
        -   [Examples][75]
    -   [updateUserConfigVersion][76]
        -   [Parameters][77]
        -   [Examples][78]
    -   [deleteUserConfig][79]
        -   [Parameters][80]
    -   [getCurrent][81]
        -   [Parameters][82]
    -   [getById][83]
        -   [Parameters][84]
    -   [switchProject][85]
        -   [Parameters][86]
    -   [delete][87]
        -   [Parameters][88]
    -   [getUserGroups][89]
        -   [Parameters][90]
    -   [getScripts][91]
        -   [Parameters][92]
        -   [Examples][93]
    -   [getUsers][94]
        -   [Parameters][95]
    -   [getModels][96]
        -   [Parameters][97]
-   [IafScripts][98]
-   [IafUserGroup][99]
    -   [addUserToGroup][100]
        -   [Parameters][101]

## Types




### Project

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** project UUID
-   `_description` **[String][103]** project description
-   `_name` **[String][103]** project name
-   `_shortName` **[String][103]** short name
-   `_namespaces` **[Array][104]&lt;[String][103]>** namespaces
-   `_userAttributes` **[JSON][105]** optional, custom fields

### UserCriteria

Type: [Object][102]

#### Properties

-   `query` **[String][103]** a string used to apply startsWith filter in firstname or lastname or email

### User

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** user id UUID
-   `_firstname` **[String][103]** user's first name
-   `_lastname` **[String][103]** user's last name
-   `_email` **[String][103]** user's email
-   `_isSocial` **[boolean][106]** true if the user created via social login
-   `_disabled` **[boolean][106]** true if user is disabled

### UserGroup

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** user group UUID
-   `_description` **[String][103]** user group description
-   `_name` **[String][103]** user group name
-   `_shortName` **[String][103]** short name
-   `_namespaces` **[Array][104]&lt;[String][103]>** namespaces
-   `_userAttributes` **[JSON][105]** optional, custom fields

### NamedUserItem

Type: [Object][102]

#### Properties

-   `noAuth` **[boolean][106]** optional, true when no authentication required
-   `authToken` **[String][103]** required when authentication is needed
-   `_namespaces` **[Array][104]&lt;[String][103]>** required when nsfilter is needed
-   `storage` **[JSON][105]** optional, session storage

### NamedUserItem

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** id
-   `_name` **[String][103]** name
-   `_description` **[String][103]** description
-   `_shortName` **[String][103]** short name
-   `_userType` **[String][103]** user type
-   `_version` **[NamedUserItemVersion][107]** version

### NamedUserItemCriteria

Type: [Object][102]

#### Properties

-   `query` **[JSON][105]** mongodb query

#### Examples

```javascript
// simple filter examples
let query = {"_usertype":"project_setup","_name":"projectSetup"}
let query = {"_id":{"$in":["5c9328e8b834740001cd95d4","5c9328e8b834740001cd95d4"]}}

// complex query
let query = {"$and":[{"_userType":"file_container","_name":"Root Container"}],"$or":[{"_tipVersion":1},{"_id":{"$in":["5c9328e8b834740001cd95d4","5d31574411efe92d8832c21c"]}}]}
```

### NamedUserCollection

Type: [NamedUserItem][108]

### NamedFileCollection

Type: [NamedUserCollection][109]

### NamedUserItemVersion

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** id
-   `_userAttributes` **[JSON][105]** custom fields
-   `_version` **[Number][110]** version number, auto generated, not editable
-   `_userItemId` **[String][103]** refers \_userItemId in  NamedUserItem
-   `_itemClass` **[String][103]** refers  \_itemClass in NamedUserItem
-   `_userItemDbId` **[String][103]** refers \_id in NamedUserItem

### Script

Type: [NamedUserItem][108]

#### Properties

-   `_version` **[ScriptVersion][111]** version

### ScriptVersion

Type: [NamedUserItemVersion][107]

#### Properties

-   `_userData` **[String][103]** Script content

### UserConfig

Type: [NamedUserItem][108]

#### Properties

-   `_version` **[UserConfigVersion][112]** version

### UserConfigVersion

Type: [NamedUserItemVersion][107]

#### Properties

-   `_userData` **[String][103]** User config content

### RelatedItem

Type: [Object][102]

#### Properties

-   `_id` **[String][103]** id

### FileItem

Type: [RelatedItem][113]

#### Properties

-   `_fileId` **[String][103]** file id refers to the id in file service
-   `_fileVersionId` **[String][103]** file version id refers to the version id in file service

### Ctx

Type: [Object][102]

#### Properties

-   `noAuth` **[boolean][106]** optional, true when no authentication required
-   `authToken` **[String][103]** required when authentication is needed
-   `_namespaces` **[Array][104]&lt;[String][103]>** required when nsfilter is needed
-   `storage` **[JSON][105]** optional, session storage

## iaf-bimGfcLdr

A namespace.

### loadGraphicsStream

Loads the 3D BIM Graphics for an imported BIM model.

#### Parameters

-   `model_id`  The model id of the imported BIM model.
-   `target`  The viewer or other consumer of the BIM Graphics Data.

Returns **[Promise][114]&lt;[boolean][106]>** 

## IafFile

### RootContainerName

### createContainer

Use to create the root container and subsequent containers

#### Parameters

-   `parentContainer` **[NamedFileCollection][115]** parent container
-   `containerInfo` **[NamedFileCollection][115]** container information to be created
-   `ctx` **[Ctx][116]** context
-   `options` **[JSON][105]** optional parameters such as \_offset and \_pageSize. By default 0 and 10 respectively

#### Examples

```javascript
// Create Root container



//Create child container
```

Returns **[NamedFileCollection][115]** Created file container

### uploadFile

Use to create the root container and subsequent containers

#### Parameters

-   `container` **[NamedFileCollection][115]** container or folder
-   `file` **[Object][102]** file object
-   `tags` **[Array][104]&lt;[String][103]>** tags to be associated to the file\*
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
// Upload file
```

Returns **[FileItem][117]** created file item

### getFileItem

#### Parameters

-   `container` **[NamedFileCollection][115]** container or folder
-   `fileItem` **[FileItem][117]** file item, id is enough
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
// get File Item
let fileItem = IafFile.getFileItem(container,{_id:'5c931fddb834740001251982',ctx}
```

Returns **[FileItem][117]** file item

## IafProj

### getProjects

Retrieves all the projects for session user filter by criteria, if no criteria is present then return all the projects for the user

#### Parameters

-   `criteria` **[Project][118]** projects filter
-   `ctx` **[Ctx][116]** context
-   `options` **[JSON][105]** optional parameters such as \_offset and \_pageSize. By default 0 and 10 respectively

#### Examples

```javascript
// Retrieves by project name.
let projects = await IafProj.getProjects({_name:'test-project'},{_namespaces:["test_nhM0Nala"]});


//Retrieves with particular offset and pageSize
let options = {_offset: 10, _pageSize: 50}
let projects = await IafProj.getProjects({_name:'test-project'},{_namespaces:["test_nhM0Nala"]},options);
```

Returns **[Array][104]&lt;[Project][118]>** array of projects

### create

creates a new project

#### Parameters

-   `project` **[Project][118]** project object
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
// Create a new project
let projectObj = {
   "_description": "account workspace",
   "_name": "Account Workspace",
   "_shortName": "aw",
   "_userAttributes": {"usergroups":[]}
}

let project = await IafProj.create(projectObj,ctx);
```

Returns **[Project][118]** created project

### addScript

Add script into the project

#### Parameters

-   `project` **[Project][118]** project object
-   `script` **[Script][119]** script object
-   `ctx` **ctx** context

#### Examples

```javascript
//Create script
let scriptObj = {
     "_name": "Project setup script",
     "_shortName": "prjSetup",
     "_userType": "project_setup_script".
     "_version":{"_userData":"[{$defscript: {}}]"}
}

let script = await IafProj.addScript(project,scriptObj,ctx);
```

Returns **[Script][119]** created script

### updateScript

Update existing script in the project, Use updateScriptVersion to update script content

#### Parameters

-   `project` **[Project][118]** project object
-   `script` **[Script][119]** script object to update
-   `ctx` **ctx** context

#### Examples

```javascript
//Update script
let scriptObj = {
     "_id": "5c931fddb834740001251982",
     "_name": "Project setup script",
     "_shortName": "prjSetup",
     "_userType": "project_setup_script_updated"
}

let script = await IafProj.updateScript(project,scriptObj,ctx);
```

Returns **[Script][119]** updated script

### updateScriptVersion

Update existing version for a script. It is used to update the script content for a given version

#### Parameters

-   `script` **[Script][119]** script obj
-   `version` **[ScriptVersion][111]** script version object to update
-   `ctx` **ctx** context

#### Examples

```javascript
//Update script version
let script = { "_id": "5c931fddb834740001251982"}
let scriptVersionObj = {
     "_id": "5c9328e8b834740001cd95d4",
     "_userData":"[{$defscript: {}}]",
     "_userAttributes": {"key":"value"}
}

let scriptVersion = await IafProj.updateScriptVersion(script,scriptVersionObj,ctx);
```

Returns **[ScriptVersion][111]** updated script version

### deleteScript

Deletes a script

#### Parameters

-   `project` **[Project][118]** project object
-   `script` **[Script][119]** script to be deleted
-   `ctx` **[Ctx][116]** Context

Returns **[String][103]** 'ok: 204'

### addUserConfig

Add user config to the project

#### Parameters

-   `project` **[Project][118]** project object
-   `userConfig` **[UserConfig][120]** user config to be created
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
//Create user config
let userconfigObj = {
     "_name": "Project setup config",
     "_shortName": "prjSetupConfig",
     "_userType": "project_setup_config".
     "_version":{"_userData":"{"handlers":{}}"}
}

let userconfig = await IafProj.addUserConfig(project,userconfigObj,ctx);
```

Returns **[UserConfig][120]** created userConfig

### getUserConfigs

Get userconfigs for the project

#### Parameters

-   `project` **[Project][118]** project object
-   `filters` **[NamedUserItemCriteria][121]** filter
-   `ctx` **[Ctx][116]** Context

#### Examples

```javascript
// Get user configs without filter
let userconfigs = IafProj.getUserConfigs(project,{},ctx)

// Get user configs with filter, refer {NamedUserItemCriteria} for more examples
let filters =  {"query": {"_userType": "cde_user_config"}}
let userconfigs = IafProj.getUserConfigs(project,filters,ctx)
```

Returns **any** Array&lt;UserConfig} - array of user configs

### updateUserConfig

Update user config,  Use updateUserConfigVersion to update script content

#### Parameters

-   `project` **[Project][118]** project object
-   `userConfig` **[UserConfig][120]** user config to be updated
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
// Update user config
let userConfigObj = {
     "_id": "5c931fddb834740001251982",
     "_name": "Project setup userconfig",
     "_shortName": "prjuserconfig",
     "_userType": "project_setup_userconfig_updated"
}

let userconfig = await IafProj.updateUserConfig(project,userConfigObj,ctx);
```

Returns **[UserConfig][120]** updated user config

### updateUserConfigVersion

Update user config version, it is used to update user config content

#### Parameters

-   `userConfig` **[UserConfig][120]** user config
-   `version` **[UserConfigVersion][112]** user config version to be updated
-   `ctx` **[Ctx][116]** context

#### Examples

```javascript
//Update user config version
let userConfig = { "_id": "5c931fddb834740001251982"}
let userConfigVersionObj = {
     "_id": "5c9328e8b834740001cd95d4",
     "_userData":"[{$defscript: {}}]",
     "_userAttributes": {"key":"value"}
}

let userConfigVersion = await IafProj.updateUserConfigVersion(userConfig,userConfigVersionObj,ctx);
```

Returns **[UserConfigVersion][112]** updated user config version

### deleteUserConfig

Deletes a user config

#### Parameters

-   `project` **[Project][118]** project object
-   `userConfig` **[UserConfig][120]** user config to be deleted
-   `ctx` **[Ctx][116]** context

Returns **[String][103]** 'ok: 204'

### getCurrent

Get current project either from browser's session Storage or ctx

#### Parameters

-   `ctx` **[Ctx][116]** context

Returns **[Project][118]** 

### getById

Get project by Id

#### Parameters

-   `id` **[String][103]** project UUID
-   `ctx` **[Ctx][116]** context

Returns **[Project][118]** 

### switchProject

Set the project as current project either in session storage or ctx

#### Parameters

-   `id` **[String][103]** project UUID
-   `ctx` **[Ctx][116]** context

Returns **[Project][118]** 

### delete

Soft deletes the project

#### Parameters

-   `project` **[Project][118]** project obj
-   `ctx` **[Ctx][116]** context

Returns **[String][103]** 'ok: 204'

### getUserGroups

Get user groups associated for the project, which current user has access

#### Parameters

-   `project` **[Project][118]** project object
-   `ctx` **[Ctx][116]** context

Returns **any** Array{UserGroup} - array of user groups

### getScripts

-   **See: NamedUserItemCriteria**
-   **See: [NamedUserItemCriteria][14]**

Get scripts for the project

#### Parameters

-   `project` **[Project][118]** project object
-   `filters` **[NamedUserItemCriteria][121]** filter
-   `ctx` **[Ctx][116]** Context

#### Examples

```javascript
// Get scripts without filter
let scripts = IafProj.getScripts(project,{},ctx)

// Get scripts with filter, refer {NamedUserItemCriteria} for more examples
let filters =  {"query": {"_userType": "cde_script"}}
let scripts = IafProj.getScripts(project,filters,ctx)

// For more examples
```

Returns **[Array][104]&lt;[Script][119]>** array of scripts

### getUsers

Get all the users from user groups which are associated to the project

#### Parameters

-   `project` **[Project][118]** 
-   `query` **[UserCriteria][122]** //TODO: apply query
-   `ctx` **[Ctx][116]** context

Returns **[Array][104]&lt;[User][123]>** array of users

### getModels

#### Parameters

-   `project` **[Project][118]** project object
-   `ctx` **ctx** context
-   `options` **[JSON][105]** 

Returns **[Array][104]** array of models

## IafScripts

## IafUserGroup

### addUserToGroup

#### Parameters

-   `userGroup`  
-   `user`  
-   `ctx`  

Returns **[Promise][114]&lt;void>** 

[1]: #types

[2]: #project

[3]: #properties

[4]: #usercriteria

[5]: #properties-1

[6]: #user

[7]: #properties-2

[8]: #usergroup

[9]: #properties-3

[10]: #nameduseritem

[11]: #properties-4

[12]: #nameduseritem-1

[13]: #properties-5

[14]: #nameduseritemcriteria

[15]: #properties-6

[16]: #examples

[17]: #namedusercollection

[18]: #namedfilecollection

[19]: #nameduseritemversion

[20]: #properties-7

[21]: #script

[22]: #properties-8

[23]: #scriptversion

[24]: #properties-9

[25]: #userconfig

[26]: #properties-10

[27]: #userconfigversion

[28]: #properties-11

[29]: #relateditem

[30]: #properties-12

[31]: #fileitem

[32]: #properties-13

[33]: #ctx

[34]: #properties-14

[35]: #iaf-bimgfcldr

[36]: #loadgraphicsstream

[37]: #parameters

[38]: #iaffile

[39]: #rootcontainername

[40]: #createcontainer

[41]: #parameters-1

[42]: #examples-1

[43]: #uploadfile

[44]: #parameters-2

[45]: #examples-2

[46]: #getfileitem

[47]: #parameters-3

[48]: #examples-3

[49]: #iafproj

[50]: #getprojects

[51]: #parameters-4

[52]: #examples-4

[53]: #create

[54]: #parameters-5

[55]: #examples-5

[56]: #addscript

[57]: #parameters-6

[58]: #examples-6

[59]: #updatescript

[60]: #parameters-7

[61]: #examples-7

[62]: #updatescriptversion

[63]: #parameters-8

[64]: #examples-8

[65]: #deletescript

[66]: #parameters-9

[67]: #adduserconfig

[68]: #parameters-10

[69]: #examples-9

[70]: #getuserconfigs

[71]: #parameters-11

[72]: #examples-10

[73]: #updateuserconfig

[74]: #parameters-12

[75]: #examples-11

[76]: #updateuserconfigversion

[77]: #parameters-13

[78]: #examples-12

[79]: #deleteuserconfig

[80]: #parameters-14

[81]: #getcurrent

[82]: #parameters-15

[83]: #getbyid

[84]: #parameters-16

[85]: #switchproject

[86]: #parameters-17

[87]: #delete

[88]: #parameters-18

[89]: #getusergroups

[90]: #parameters-19

[91]: #getscripts

[92]: #parameters-20

[93]: #examples-13

[94]: #getusers

[95]: #parameters-21

[96]: #getmodels

[97]: #parameters-22

[98]: #iafscripts

[99]: #iafusergroup

[100]: #addusertogroup

[101]: #parameters-23

[102]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[103]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[104]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array

[105]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON

[106]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean

[107]: #nameduseritemversion

[108]: #nameduseritem

[109]: #namedusercollection

[110]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number

[111]: #scriptversion

[112]: #userconfigversion

[113]: #relateditem

[114]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise

[115]: #namedfilecollection

[116]: #ctx

[117]: #fileitem

[118]: #project

[119]: #script

[120]: #userconfig

[121]: #nameduseritemcriteria

[122]: #usercriteria

[123]: #user
