---
title: "Adobe CS3 almost working in Wine"
date: 2008-08-25
forum: Art &amp; Design
---

### Post by liquidfire_24 on 2008-08-25
----Edit---
 the reason for the  licensing error is due to a service fill not starting (FNPLicensingService.exe). I have no idea on how to write the service/startup script for it. That is the only problem i can find when the apps load everythign in the windows appear to be working  everything looks correct. they just load really slowly and dont show splash screens.
-----------

OK i have adobe masters suite fully working under wine .. just one problem the reg isnt working correctly. thus you load up and then it give you  the error  


>  (title bar : licensing for this product has stopped working)You cannot use this program at this time. You must fix the problem by uninstalling and reinstalling this product or contacting your IT adim or contacting Adobe customer support for help

Any ideas on how to get past the reg error?

Steps to get where i am now
```

 must have dual boot system
-- install cs3 master suite in windows,  ( i fully activated the software in windows)

--In your Windowx box, type &#8220;regedit&#8221; in the command-line and export the whole &#8220;HKEY_LOCAL_MACHINE/Software/Macromedia/&#8221; to &#8220;macromedia.reg&#8221;,and "HKEY_LOCAL_MACHINE/Software/Adobe/" to Adobe.reg.... Safe in copaibilty with  98/NT  then copy it to your your Ubuntu

-- boot up ubuntu
   * Copy the whole Macromedia folder from &#8220;c:\Program Files\&#8221; to &#8220;/home/YOURNAME/.wine/drive_c/Program Files/&#8221;

    * Copy the whole Macromedia folder from &#8220;c:\Documents and settings\All users\Application Data&#8221; to &#8220;/home/YOURNAME/.wine/drive_c/window/profile/all users/&#8221;

    * Copy the whole Macromed (No mistake with the &#8220;ai&#8221;) from &#8220;c:\Windows\system32\&#8221; to &#8220;/home/YOURNAME/.wine/drive_c/window/system32/&#8221;

    * Finally, copy the whole Macromedia folder from &#8220;c:\Program Files\Common Files&#8221; to &#8220;/home/YOURNAME/.wine/drive_c/Program Files/Common Files/&#8221;

Open terminal
 type regedit
 click on registry/import registry file. navigate to your .reg files and import.


```

 Thats all i have so far. Also sorry if there is a topic about this already i searched but found nothing. Please post any ideas or suggestions.



Errors 
> fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 300, std (d/m/y): 2/11/2008, dlt (d/m/y): 9/03/2008
fixme:system:SetProcessDPIAware stub!
err:shell:HCR_GetFolderAttributes HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x165af4 0x165b00 0x1658a0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1658f4 0x165900 0x1606a8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x165c34 0x165c40 0x165d08 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x165c34 0x165c40 0x165d08 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x167f74 0x167f80 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x167f74 0x167f80 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x168e1c 0x168e28 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x168e1c 0x168e28 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x168e1c 0x168e28 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x168e1c 0x168e28 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x168e1c 0x168e28 0x165d58 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dc40 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dc40 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dc40 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dc40 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Documents and Settings\\All Users\\Application Data/FLEXnet/adobe_00080000_event.log" 1 4 (nil) (nil) 0x4edb0d8 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dbc0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dbc0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dbc0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x16db6c 0x16db78 0x16dbc0 (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:imm:ImmReleaseContext (0x8003e, 0x151a30): stub


---

### Post by Orlsend on 2008-08-26
I cant even GET CS2 to work, My Boss bougth for me the whole CS3 Suite... Ihate to tell him that the old one is not even running in Linux...Oh well I can load Windows XP when i need PS

---

### Post by liquidfire_24 on 2008-08-26
Any ideas if a cracked exe would work better?

---

### Post by Crafty Kisses on 2008-08-26
It wouldn't make a difference, seeing as how many people have tried to get Photoshop CS3 running in Linux.

Photoshop 7 works perfectly in Wine.

---

### Post by liquidfire_24 on 2008-08-26
well the problems seems to lie within the flexnet files. ( required to validate adobe products)..in theory if can get the  service files to boot in  ubuntu then i can get adobe cs3 to work ..  jsut i cant get the file to run

---

### Post by Crafty Kisses on 2008-08-26
If the error reads correctly, sure. In **theory** it could work. Take this guy for example > [http://wine-review.blogspot.com/2008/03/photoshop-cs3-on-linux-with-wine.html](http://wine-review.blogspot.com/2008/03/photoshop-cs3-on-linux-with-wine.html)

---

### Post by liquidfire_24 on 2008-08-26
I think ill set this project aside until I am more advanced in using Ubuntu .. this is my fifth day using it haha. great stuff tho. there is a work around and i will find it  :D

---

### Post by Crafty Kisses on 2008-08-26
If you do, please let us now.

---

### Post by liquidfire_24 on 2008-08-27
oh definitional. im running it all in virtual box now ..

---

### Post by Crafty Kisses on 2008-08-27
> **liquidfire_24 said:**
> oh definitional. im running it all in virtual box now ..

Nice, I'm glad you can finally use it.

---

### Post by liquidfire_24 on 2008-08-27
Sweet after a lot of digging today i found a list of about ..say um 40 files (dll,nsl,exe) that adobe tries to hid from you that it uses :D... so once i get done sorting out this list and getting all the files that are need ill post again with hopefully good news :D

---

### Post by Crafty Kisses on 2008-08-28
I'd hope so. :)

---

### Post by billstei on 2008-08-28
liquidfire_24:  I hope that you have success getting CS3 to run under Wine, but I am wondering, do you use a graphics tablet, and if yes, does it work (well) inside virtualbox?

Bill

---

### Post by liquidfire_24 on 2008-08-28
I dont. but i can look into geting one and seeing what happens.In about the next two hours ill know whats going on with  CS3 + wine.  There are lots of steps that have to be taken ( if this will even work) and im still unsure how stable CS3 will be in wine. 

Also can you find drivers for you tablet? thats going to be the biggest issue. If you cant find drivers it wont work simple, what table do you have and ill see what info i can dig up on it.

---

### Post by billstei on 2008-08-28
I don't have a tablet (yet), but I have been doing a lot of research, and even though wacom prices are higher, the quality is worth it, and the linux support is the best for wacom tablets.  For example see:

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
[http://linuxwacom.sourceforge.net](http://linuxwacom.sourceforge.net)
[http://www.gimptalk.com/forum/install-guide-getting-wacom-drawing-tablets-to-work-in-gimp-t17992.html](http://www.gimptalk.com/forum/install-guide-getting-wacom-drawing-tablets-to-work-in-gimp-t17992.html)

Bill

---

### Post by liquidfire_24 on 2008-08-28
yeah you should have no problems then. Also  with Vbox you run windows inside of  Ubuntu so you should have no problems there anyways. non that i can think of anyways i know there is issues with games but i belive tablets should would just be sure to enable usb support.

---

### Post by liquidfire_24 on 2008-08-28
Well some good news i have gotten  Fireworks, and Flash working both CS3 in the master suite


now for some bad news .. premiere , dream weaver, photoshop, Soundbooth, contribute,after effects, wont load due to manifest issues. its not constructing the .dll correctly and give a runtime error . Anyone got any ideas on how to fix this ?

Flash is a little iffy
[http://tsmithgraphics.com/pic/flash.png]("http://tsmithgraphics.com/pic/flash.png")
Fireworks looks good tho 
[http://tsmithgraphics.com/pic/fireworks.png]("http://tsmithgraphics.com/pic/fireworks.png")

---

