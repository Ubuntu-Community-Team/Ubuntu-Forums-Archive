---
title: "Wine"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-03-20
I have Wine installed on my system but I can't locate it anywhere and there is not file anywhere! How can I find it?

---

### Post by Sutekh on 2006-03-20
If wine is installed, then the executable will be in something like /usr/bin.  This is not how you use wine though...


To use it you must call wine then use the location of the .exe you want to run using wine.

```
wine /<somefolder>/<somefile>.exe
```
An example would be
```
wine /media/cdrom0/setup.exe
```

First you should run ```
winecfg
``` and set things up.


Maybe have a read of the Wine Users Guide to help you with anymore questions

[Wine User's Guide](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by Qrk on 2006-03-20
Use synaptic to find it, by right clicking on the "wine" packages and selecting Properties --> Installed files

But this is probably not what you are looking for. If you are having problems getting wine to work run "winecfg" in a terminal. You should be able to set a lot of it up there. Next download winetools or a similar program to help you get started with a usable virtual windows setup.

---

### Post by Reggaeton King on 2006-03-20
I have wine working now but I installed Dreamweaver and it make a fake windows directory. I am able to access it and installed Dreamweaver but then Dreamweaver.msi and DW_Client_Installer.exe are the only things I can run that and it seems to be an error.
```

cledet@RKing:~/Desktop/Macromedia$ wine DW_Client_Installer.exe
fixme:advapi:CheckTokenMembership ((nil) 0x7fdc6c68 0x7fb0e794) stub!
fixme:msi:MsiInstallProductW L"Z:\\home\\cledet\\Desktop\\Macromedia\\Macromedia _Dreamweaver_8.msi" L""
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7e15e644,0x7e15e648), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7e15e640,0x7e15e644), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafedf0,0x7fafedf4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafecb0,0x7fafecb4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafed74,0x7fafed78), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafe820,0x7fafe824), stub!
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:deformat_environment Unknown environment variable L"ALLUSERSPROFILE"
fixme:rpc:RpcImpersonateClient (0x7da5c2c0): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1b0000001c
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7e049f8c,0x7e049f90), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7e049ed0,0x7e049ed4), stub!
fixme:msi:MsiInstallProductW L"/x{5546CDB5-2CE2-498B-B059-5B3BF81FC41F}" (null)
err:msi:copy_package_to_temp failed to copy package to temp path L"C:\\windows\\temp\\MSI377e.tmp"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7faff614,0x7faff618), stub!
fixme:rpc:RpcRevertToSelfEx (0x7da5c2c0): stub
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7de22644,0x7de22648), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7de22640,0x7de22644), stub!
fixme:win:SetWindowTextA setting text "TITLE_CAPTIONBAR" of other process window (nil) should not use SendMessage
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafedf0,0x7fafedf4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafecb0,0x7fafecb4), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafed74,0x7fafed78), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7fafe820,0x7fafe824), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7de22630,0x7de22634), stub!
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"DisableRollback"
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"
fixme:msi:msi_dialog_set_control_condition Unhandled action L"Default"


```

---

### Post by Sutekh on 2006-03-20
That's way over my head.

You should check out the [Wine Application Database](http://appdb.winehq.org/)

Here's the entry they have for Dreamweaver, you should be able to check out how well your version runs in Wine and see what problems and solutions other people have.

[Wine AppDB - Dreamweaver]("http://appdb.winehq.org/appview.php?appId=183")

---

