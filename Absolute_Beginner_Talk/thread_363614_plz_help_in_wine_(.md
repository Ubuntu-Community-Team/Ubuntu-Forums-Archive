---
title: "plz help in wine :("
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-02-17
hello all 

i want to configure wine so can i work with .exe files i download it and itis libs. by using synaptics and when i want to lunch a program i got this errors help plz :( :( 


[PHP]adam@adam-laptop:/media/hda1/Program Files/Messenger$ wine msmsgs.exe 
err:module:import_dll Library gdiplus.dll (which is needed by L"Z:\\media\\hda1\\Program Files\\Messenger\\msmsgs.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\hda1\\Program Files\\Messenger\\msmsgs.exe" failed, status c0000135
[/PHP]

---

### Post by black_ice on 2007-02-17
iam really lost :confused: :confused: :confused: :confused: :confused:

---

### Post by duality on 2007-02-17
I think you need GDIPLUS.DLL which you can get from here [http://www.fineprint.com/support/gdiplus.dll](http://www.fineprint.com/support/gdiplus.dll)

put it in /home/<yourusername>/.wine/drive_c/windows/system32/


But I recommend using some of the open source alternatives to msn messenger, for ex. Kopete, GAIM, amsn

---

### Post by black_ice on 2007-02-17
thanx for your replay but i did what u said and i put the file in the right path 

[PHP] root@adam-laptop:/home/adam/.wine/drive_c/windows/system32# ls | grep gd
gdi32.dll
gdiplus.dll
[/PHP]

and the problem still :( 

[PHP] root@adam-laptop:/media/hda1/Program Files/Messenger# wine msmsgs.exe 
err:module:import_dll Library gdiplus.dll (which is needed by L"Z:\\media\\hda1\\Program Files\\Messenger\\msmsgs.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\hda1\\Program Files\\Messenger\\msmsgs.exe" failed, status c0000135
[/PHP]

---

### Post by duality on 2007-02-17
Strange that it didnt pickup the dll.

[http://appdb.winehq.org/appview.php?iVersionId=5264](http://appdb.winehq.org/appview.php?iVersionId=5264)

heres the entry for msn messenger with wine. gl

---

### Post by black_ice on 2007-02-17
after i get confused i downloaded the last version of msn messenger and i install it 
and seems to be installed 
[PHP]adam@adam-laptop:~$ wine Install_Messenger.exe 
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"adam" (nil) 0x33e8b0 (nil) 0x33e8ac 0x33e8b8 - stub
fixme:advapi:LookupAccountNameW (null) L"adam" 0x174140 0x33e8b0 0x174158 0x33e8ac 0x33e8b8 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:shell:URL_ParseUrl failed to parse L""
err:msi:msi_dialog_oncommand button click from nowhere 0x1a3700 67108864 0x1003e
err:msi:msi_dialog_oncommand button click from nowhere 0x1a3700 67108864 0x1003e
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
err:richedit:ReadStyleSheet ReadStyleSheet: skipping optional destination
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 7 ignored L"Upgrade" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 7 ignored L"Upgrade" table values
fixme:msidb:ALTER_execute 0x6e73b0 (nil)
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:msi_unimplemented_action_stub StopServices -> 2 ignored L"ServiceControl" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 2 ignored L"ServiceControl" table values
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:ole:CoGetClassObject class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
err:ole:create_server class {4e14fba2-2e22-11d1-9964-00c04fbbb345} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4e14fba2-2e22-11d1-9964-00c04fbbb345} could be created for context 0x15
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msxml:domdoc_put_preserveWhiteSpace 
fixme:msxml:domdoc_put_resolveExternals 
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:advapi:CheckTokenMembership ((nil) 0x170760 0x33fc94) stub!
fixme:setupapi:CMP_WaitNoPendingInstallEvents 100
fixme:advapi:CheckTokenMembership ((nil) 0x170760 0x33fa88) stub!
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x50 0x33f320 0x33f994 0
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x50 0x33f320 0x33f994 0
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:advapi:CheckTokenMembership ((nil) 0x170760 0x33fa88) stub!
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x50 0x33f320 0x33f994 0
fixme:wintrust:CryptCATAdminCalcHashFromFileHandle 0x50 0x33f320 0x33f994 0
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ITERATE_InstallService Dependency list unhandled!
fixme:msi:msi_unimplemented_action_stub MsiPublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:create_server class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x17
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:advapi:LookupAccountNameW (null) (null) (nil) 0x7e29a954 (nil) 0x7e29a950 (nil) - stub
fixme:crypt:CRYPT_PhysOpenStoreW (0, 00011002, L"Root\\.LocalMachine"): stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
adam@adam-laptop:~$ err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library ContactsUX.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe" failed, status c0000135
[/PHP]

and i got an icon on Desktop named with windows Live Messenger.lnk
and the shell stopped ! 

any one can help me ? !

---

