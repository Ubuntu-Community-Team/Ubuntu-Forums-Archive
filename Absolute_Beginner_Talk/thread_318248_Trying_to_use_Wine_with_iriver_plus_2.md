---
title: "Trying to use Wine with iriver plus 2"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-13
Hello, I'm new to xubuntu and wine, and have been trying to use wine to install and run iRiver's Plus 2 music jukebox so I can sync my iRiver T30 (firmware has been changed to 1.71 ums).

I have added the newest versions of mfc42.dll and mfc42u.dll to /.wine/drive_c/windows/system32

I have also configure my Audio in winecfg by going to Audio-->--Hardware Accelerator-->-- and switching it to "Emulation".

It is using the default OSS.

I am able to get the iriver plus 2 install working to the point where it is supposed to Finish and run, then it shows the music jukebox app the exact way it appears on Windows Xp, but the cursor isn't able to click on any of the buttons and it just freezes there.

It also shows as the frozen app on all 4 of my Beryl workspaces. 

I have all of my error messages saved if it might help to configure it correctly.

---

### Post by crimesaucer on 2006-12-13
I googled part of this error (error 0x80040111) and couldn't find any help other than it was related to WMP 9 and mysql?


blah@blah-blah:~$ wine /home/blah/iriver2_setup_full.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:process:IsWow64Process (0xffffffff 0x33fa10) stub!
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_RTLREADING 
err:ole:get_inproc_class_object DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {cfc399af-d876-11d0-9c10-00c04fc99c8e} could be created for context 0x1
libGL warning: 3D driver claims to not support visual 0x5b
blah@blah-blah:~$ libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
err:systray:delete_icon invalid tray icon ID specified: 200d
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.



fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:win:RegisterDeviceNotificationW (hwnd=0x4002a, filter=0x34f004,flags=0x00000000), STUB!
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 3 lpiArray 0xb79528
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 3 lpiArray 0xb79528
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 11 lpiArray 0xb95040
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 11 lpiArray 0xb95040
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 1
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option 7 STUB
fixme:wininet:InternetSetOptionExW Flags 00000000 ignored
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_DATA_RECEIVE_TIMEOUT (20000): STUB
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
fixme:wininet:InternetSetFilePointer stub
fixme:wininet:InternetSetFilePointer stub
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer

I think I'm gonna give up on this issue and just use windows to properly sync my iRiver device. If anybody has an answer on how to fix wine to use the iRiver Plus 2, then that would be cool.

---

### Post by crimesaucer on 2006-12-13
Do I need to set an override in my libraries for the .dll?

I have added the program to Applications and configured it to work with xp.

Any wine help, anybody?

---

