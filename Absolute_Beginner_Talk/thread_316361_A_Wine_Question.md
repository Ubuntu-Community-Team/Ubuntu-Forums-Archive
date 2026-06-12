---
title: "A Wine Question"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-10
Hello, I'm trying to use Wine for my first time. This is my terminal procedures as I changed directory to cut and paste the proper wine /home/blah/iriverFirmwareUpdater[2]/IRiverFirmwareUpdater.exe

blah@blah-blah:~$ cd /home/blah/iriverFirmwareUpdater[2]/
blah@blah-blah:~/iriverFirmwareUpdater[2]$ ls
IRiverFirmwareUpdater.exe
blah@blah-blah:~/iriverFirmwareUpdater[2]$ cd ~
blah@blah-blah:~$ wine /home/blah/iriverFirmwareUpdater[2]/IRiverFirmwareUpdater.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\blah\\iriverFirmwareUpdater[2]\\IRiverFirmwareUpdater.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\blah\\iriverFirmwareUpdater[2]\\IRiverFirmwareUpdater.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\blah\\iriverFirmwareUpdater[2]\\IRiverFirmwareUpdater.exe" failed, status c0000135
blah@blah-blah:~$ 

So do I need to install two Librarys of MFC42.DLL and MSVCP60.DLL in order for my firmware updater to work?

When I searched for these Librarys on Synaptic I could not find anything, and the search for iRiver on Synaptic didn't have anything saying iRiver T30 in the list.

Any help would be cool. Thanks.
-c.

---

### Post by crimesaucer on 2006-12-10
I also tried to install the iRiver plus2 music jukebox to use for syncing my device and music transfers.

I tried this:

blah@blah-blah:~$ pwd
/home/blah
blah@blah-blah:~$ wine /home/blah/iriver2_setup_full.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
blah@blah-blah:~$ 

I canceled the install because I am using Beryl AiGLX and I wasn't sure if it was safe because of the warnings.

I am still a beginner and don't want to ruin my system that is working so perfectly, so any info would make me a little more confidant on using wine.

---

### Post by claydoh on 2006-12-10
The two *.DLL files are windows libraries and won't be found in synaptic, though you may have them if you have a windows machine handy or search for them online. It won't guarantee success however. It would be safer for your hardware to do the update from windows, or look to see if there is a manual way to update the firmware

---

### Post by crimesaucer on 2006-12-10
I went ahead and switched over to my Xp partition to reinstall my firmware.

As for installing the iRiver plus2 music jukebox using wine, is this error I'm getting normal for wine installs:

libGL warning: 3D driver claims to not support visual 0x5b

Because of the warnings I aborted the install. But there was a windows looking dialog box that I could of installed from. I just didn't want to ruin Beryl since it has been working so good.

What is "visual 0x5b"?

*****so, after googling a bit, I was able to see that that error is pretty common with Intel 915, Beryl, and X11, so running Berly AiGLX on xfce4 xubuntu edgy and an Intel 910 celeron m chipset and Intel Accelerator 900 graphics card is probably my problem with wine and this iRiver install exe.

---

### Post by crimesaucer on 2006-12-10
Bump...

Still wondering if it is ok to run the iRiver install exe. with the warning about the "visual 0x5b".

Also, I have installed it on my Windows Xp partition, is there a way I can run that one using wine? It's located in Programs File.

---

### Post by claydoh on 2006-12-10
Its a warning, but it looks like the only thing that could happen is it won't run or maybe it will lock up your desktop, but it won't hurt your system (unless you are silly and run wine with sudo :) )

As beryl is a new thing, I would just try turning it off if you get poor results with an app.

But I seriously doubt the jukebox software will run in wine. Search around here for if and how folks do it with linux software, you might be surprised

---

### Post by crimesaucer on 2006-12-10
What happens when you run wine as sudo?

---

### Post by kebes on 2006-12-11
> **crimesaucer said:**
> What happens when you run wine as sudo?

"sudo" runs things as 'root' (the 'superuser' or administrator account). So when you run a program using "sudo" you are giving it permission to do whatever it wants (can modify system files, reboot the machine, etc.). Generally you never use sudo to run a program or command unless you are sure that's it's safe. (You need sudo to install programs and make system changes from the commandline.)

The point is that if you were running wine using "sudo" it could crash your system or make system changes. However if you just run wine normally (runs as a normal user process), then it can't affect system files. It's just a matter of safety and security.

But I think there is no danger in running your installer program using wine (without sudo!)... the worst that will happen is it won't install properly, but it won't be able to break your Linux install or your Bery install.

---

### Post by crimesaucer on 2006-12-11
Thanks, I am very new to xubuntu, and I like to use terminal as much as I can.

I just asked the sudo wine question because I kept trying to run some Windows apps that I had in my media hda1 partition.

Every time I would try to run wine using this command: 

wine /media/hda1/Program\Files/iRiver/iRiver\Plus\2/iPlus2.exe

That would always say there was no folder, so I would try it with the sudo in front of it and get the same reaction.

I haven't really ran a program on wine yet, so I wasn't sure on how to do it.

After reading a bit about it, I realize I need to learn how to run winecfg and install new windows apps into the /home/blah/.wine/C\drive folder to run them.

I had originally thought that wine could access your windows apps on you dual boot partition and create new windows apps in a folder on linux if they weren't on windows. I guess I'm wrong on that one.

I was reading about wine versions in a utorrent forum yesterday, and it said to make sure you have the latest version of wine, and that usually the one offered in your repository wasn't the latest. Is "budgetdedicated" mirroring the latest release 0.9.27?

As for that "libGL warning", I think it also had to do with translucent windows. I have nothing configured as translucent on Beryl so I'm thinking it might be safe to run that iRiver Plus2 install, anyway, thanks for letting me know I won't break my system's window manager, or anything having to do with Beryl. I'm going to try the install right now.

Thanks for the help.


***I see that they have upgraded the budgetdedicated repository to the latest version today.

---

### Post by kebes on 2006-12-11
> 
After reading a bit about it, I realize I need to learn how to run winecfg and install new windows apps into the /home/blah/.wine/C\drive folder to run them.

Yes indeed. Although I've found that nowadays the default Wine install is "pretty much right" and you usually don't even have to run "winecfg". However to use Windows software, the easier way is to install the software into the "drive_c" that wine uses. So basically just put the installer executable somehwere where you can find it and go:

$ wine setup.exe

And then follow the steps (just like on windows). Wine will, however, put the installation into the folder:
/home/user/.wine/drive_c/

This folder acts as a "pretend" c:\ drive, as far as the Windows apps are concerned. Once the app is installed you can go to it, and run it:
$ cd /home/user/.wine/drive_c/Progam Files/app/
$ wine appname.exe


> 
I had originally thought that wine could access your windows apps on you dual boot partition and create new windows apps in a folder on linux if they weren't on windows. I guess I'm wrong on that one.

For some apps it works, but doing an install usually works better, if you still have the install executable handy.

> 
I was reading about wine versions in a utorrent forum yesterday, and it said to make sure you have the latest version of wine, and that usually the one offered in your repository wasn't the latest. Is "budgetdedicated" mirroring the latest release 0.9.27?

Newer Wine is always better. (In contrast to the stuff you drink, mind you.) The best way is to add the official Wine debian repository to your "/etc/apt/source.list" file. See here:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by crimesaucer on 2006-12-11
Thanks for the info on wine, maybe I'll find an app that I need wine for, but it seems that the iRiver Plus 2 requires two .Dll libraries and wasn't allowing it run.

Maybe I'll mess with it some more.

---

### Post by crimesaucer on 2006-12-11
This is my install error:

blah@blah-blah:~$ wine /home/blah/iriver2_setup_full.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\Skinlib.dll") not found
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:process:IsWow64Process (0xffffffff 0x33fa10) stub!
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_RTLREADING 
err:ole:get_inproc_class_object DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {cfc399af-d876-11d0-9c10-00c04fc99c8e} could be created for context 0x1
libGL warning: 3D driver claims to not support visual 0x5b
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\Program Files\\iriver\\iriver plus 2\\iDuetM.dll") not found
err:module:import_dll Library iDuetM.dll (which is needed by L"C:\\Program Files\\iriver\\iriver plus 2\\iPlus2.exe") not found
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\Program Files\\iriver\\iriver plus 2\\iPlus2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\iriver\\iriver plus 2\\iPlus2.exe" failed, status c0000135
blah@blah-blah:~$ err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\Program Files\\iriver\\iriver plus 2\\iAgent2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\iriver\\iriver plus 2\\iAgent2.exe" failed, status c0000135


...is it possible to install these missing libraries so this program can work, or would this require a lot more work?

Would I be able to get these libraries from some where: MFC42u.DLL and iDuetM.dll, and then add them to /home/blah/.wine/drive_c/windows/system 32 ??

Would this maybe stop the process from failing?

---

### Post by crimesaucer on 2006-12-11
I found the MFC42.DLL download on a web and downloaded and extracted the executable to my /home/blah/.wine/drive_c/windows/system32 file.

then I tried to install again with: wine /home/blah/iriver2_setup_full.exe

I got this repeating error that showed the splash of the iriver plus 2 app, but it got stuck and never loaded and was unable to be xkill(ed) off of my screen.

blah@blah-blah:~$ wine /home/blah/iriver2_setup_full.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\Skinlib.dll") not found
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:process:IsWow64Process (0xffffffff 0x33fa10) stub!
fixme:propsheet:PROPSHEET_UnImplementedFlags PSH_RTLREADING 
err:ole:get_inproc_class_object DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {cfc399af-d876-11d0-9c10-00c04fc99c8e} could be created for context 0x1
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
blah@blah-blah:~$ fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 1
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 2
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 3
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 4
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 5
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 6
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 7
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 1
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 2
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 3
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 4
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 5
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 6
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 7
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 1
err:aspi:SCSI_GetDeviceName ...............repeated to Target Id 7........

.........to.....\Logical Unit Id 5
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 6
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 7
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:exec:SHELL_execute flags ignored: 0x00000400
fixme:win:RegisterDeviceNotificationW (hwnd=0x2003a, filter=0x34f008,flags=0x00000000), STUB!
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
err:systray:delete_icon invalid tray icon ID specified: 200d
fixme:win:RegisterDeviceNotificationW (hwnd=0x3002a, filter=0x34fd98,flags=0x00000000), STUB!
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer
err:treeview:TREEVIEW_HandleTimer got unknown timer

***did I maybe put the .DLL in the wrong place or is this app just looking unusable on xubuntu?

---

### Post by kebes on 2006-12-12
I think you've copied the DLLs to the right place. Sometimes you have to change the wine configuration so that it knows to use the supplied DLL instead of trying to use a "wine native" DLL. More info on the wine page:

[http://www.winehq.com/site/docs/wineusr-guide/config-wine-main#AEN217](http://www.winehq.com/site/docs/wineusr-guide/config-wine-main#AEN217)

However, in my (limited) experience with wine, if it doesn't work straight-away, it usually won't work even with alot of tweaking. You can try if you want, but I have not had good luck with it in the past.

Maybe someone with more Wine know-how has more insight. You could also post your question on the Wine forums/mailing-lists.

---

### Post by crimesaucer on 2006-12-13
Ok, I started to mess with it a bit.

the first thing I did was to go to winecfg and switch my Audio-->--"hardware accelerator"-->--to "emulation". Apply-->--OK.

Then I copied my .dll file form /.wine/windows/system32/mfc42.dll to /.wine/windows/system/mfc42.dll

and then I tried to run the install again and I got this error:

blah@blah-blah:~$ wine /home/blah/iriver2_setup_full.exe
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
[: 221: ==: unexpected operator
libGL warning: 3D driver claims to not support visual 0x5b
blah@blah-blah:~$ fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 1
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 2
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 0\Logical Unit Id 3.......to......

err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 6
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 7
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:exec:SHELL_execute flags ignored: 0x00000400
fixme:win:RegisterDeviceNotificationW (hwnd=0x6002c, filter=0x34f008,flags=0x00000000), STUB!
libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:win:RegisterDeviceNotificationW (hwnd=0x4003e, filter=0x34fd98,flags=0x00000000), STUB!
wine: Call from 0xfb3948 to unimplemented function MFC42.DLL.6467, aborting
wine: Unimplemented function MFC42.DLL.6467 called at address 0xfb3948 (thread 002b), starting debugger...

What is an "unimplemented function? Can I fix this?

---

