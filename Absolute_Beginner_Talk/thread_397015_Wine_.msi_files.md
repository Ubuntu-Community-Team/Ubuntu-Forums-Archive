---
title: "Wine .msi files ?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-03-30
Hi i am trying to install a .msi file through wine but i don't really know how this works this is what i type..

> chris@chris-laptop:~/Desktop$ msiexec SiloSetup.msi
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron


Does anybody know how i can get this file to install ? :(

---

### Post by cowlip on 2007-03-30
I would think

wine SiloSetup.msi

should work but I might be missing something..sometimes .msis are just giant zip files, so you can uncompress them to get .exes out.

---

### Post by david_kt on 2007-03-30
> **mech7 said:**
> Hi i am trying to install a .msi file through wine but i don't really know how this works this is what i type..



Does anybody know how i can get this file to install ? :(

Try:

[INDENT]msiexec /i SiloSetup.msi[/INDENT]

DK

---

### Post by mech7 on 2007-03-30
Thanks that works but it gets an error on the install.. so i tried to copy the entire dir over from windows and it works it asks for serial but then i get this error?

[IMG]http://img295.imageshack.us/img295/8092/errorjg3.png[/IMG]

Does anybody know if this can be fixed ?

---

### Post by david_kt on 2007-03-30
Go to your windows box again, this time go to:

C:/windows/system32

and copy MSVCP80.dll. Put it in your linux box, same folder. And then try again. If it still complaint about MSVCP80.dll, change the name to all lower case (msvcp80.dll).

DK

---

### Post by mech7 on 2007-03-30
Thanks it works.. but now it is asking for another dll so i copied that over too.. and now i get this :(

[IMG]http://img470.imageshack.us/img470/7387/screenshoterrorry3.png[/IMG]

---

### Post by david_kt on 2007-03-30
Do you mean you have copied MSVCR80.dll to your linux box and it still complain about it? Have you tried to change the name to all lower case? Could you try to run in terminal and post the error in terminal?

You could try to run winecfg, add your exe program there, and add dlloverrides, play it (native,builtin) (builtin,native) and whatever option you have there and see whether or not it help. 

Or, may be give a link to donwload your software (does it have trial version?) and I try to run it in my box.

DK

---

### Post by mech7 on 2007-03-30
Yes i copied the file over i tried lower / upper case.. i am not sure how to run in terminal?

I am trying to install silo: [http://www.silo3d.com/forum/showthread.php?t=9659](http://www.silo3d.com/forum/showthread.php?t=9659)
for the beta you need to have a key though :(

---

### Post by david_kt on 2007-03-30
> **mech7 said:**
> Yes i copied the file over i tried lower / upper case.. i am not sure how to run in terminal?

I am trying to install silo: [http://www.silo3d.com/forum/showthread.php?t=9659](http://www.silo3d.com/forum/showthread.php?t=9659)
for the beta you need to have a key though :(

I have donwloaded the program, run it in window xp, and transfer it to linux box (as  the installer could not run in linux). I run the program in linux  and it prompt me for user name and password. I could not continue. May be you could email me the user name and password, and I will use it just to help you to run this program. But no promise I could manage to run it or not, just will give it a try for you. But is your call whether or not you will email me the user name and password.

DK

---

### Post by david_kt on 2007-03-30
After I think again, looks like your program is still running when you copied the second dll. What you can do is to log out and log in again, and after that try to run. Other choice is to open terminal and run this command:

[INDENT]killall wine
killall wineserver
killall wine-preloader[/INDENT]

before your try your program again. But make sure you have closed all program running with wine before you run the above command.

Other method that I could think off right now is:

Run your program in windows, including registration. So, not just run the installer but make sure the program can run in windows. After that, copy the program over to linux, and copy below three file from system32 as well:

[INDENT]
msvcm80.dll
msvcp80.dll
msvcr80.dll[/INDENT]

and copy them to your linux box. And then try to run it in linux, and see what happen.

DK

---

### Post by mech7 on 2007-03-31
Ok i copied those files over and now i get this..

[IMG]http://img490.imageshack.us/img490/9687/screenshotmicrosoftvisuwj6.png[/IMG]

Also there are a dozen of the same dll files am not sure if i took the right ones 0_o

---

### Post by garybrlow on 2007-03-31
Not all windows programs will run on wine. It needs the Microsoft Visual C++ runtime installed and related DLLs to be copied from windows in wine but there is still no guarantee that it will run but you can always try.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by david_kt on 2007-03-31
> **mech7 said:**
> Ok i copied those files over and now i get this..

[IMG]http://img490.imageshack.us/img490/9687/screenshotmicrosoftvisuwj6.png[/IMG]

Also there are a dozen of the same dll files am not sure if i took the right ones 0_o

There are two options you could try now:

1. The best bet is to use winetools. But you should downgrade your wine to version 0.9.1, 0.9.2, 0.9.3 or 0.9.5. It might not work with other wine. Winetools is making sure that your wine setting is as closed as possible to windows 98. But legally you should have winodws 98 license on your computer. Follow below instruction (except don't upgrade wine):

[http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585)

You could download wine here:
[http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.3-winehq-1_i386.deb](http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.3-winehq-1_i386.deb)
[http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.4-winehq-1_i386.deb](http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.4-winehq-1_i386.deb)
[http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb](http://heanet.dl.sourceforge.net/sourceforge/wine/wine_0.9.5-winehq-1_i386.deb)

Other old wine browse it here:
[http://heanet.dl.sourceforge.net/sourceforge/wine/](http://heanet.dl.sourceforge.net/sourceforge/wine/)


2. Other possibility is to install VB runtime on your current setting:

[http://download.microsoft.com/download/vb50pro/Utility/1/WIN98/EN-US/MSVBVM50.EXE](http://download.microsoft.com/download/vb50pro/Utility/1/WIN98/EN-US/MSVBVM50.EXE)
[http://download.microsoft.com/download/vb60pro/Redist/sp5/WIN98Me/EN-US/vbrun60sp5.exe](http://download.microsoft.com/download/vb60pro/Redist/sp5/WIN98Me/EN-US/vbrun60sp5.exe)

Run above 2 file on your current setting, and see whether or not it help. I am not sure about the license. VB runtime.

DK

---

### Post by mech7 on 2007-04-02
THanks i tried option 2 but it does not work.. dont really want to downgrade any software i think :(

also when i run it through the terminal i get these messages..about a 1000 time :p

> wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
wine: Call from 0x15c0c8c to unimplemented function MSVCR80.dll._except_handler4_common, aborting
err:seh:setup_exception stack overflow 260 bytes in thread 000b eip b7d5e573 esp 00240efc stack 0x241000-0x350000


---

### Post by david_kt on 2007-04-02
So far I found 3 solutions for this problem (unimplemented function MSVCR80.dll)

1. There is no fonts in your wine program.
Try to copy all your fonts from windows (c:/windows/font) to linux (~./wine/drive_c/windows/fonts) and see whether or not this will solve MSVCR80.dll problem. 

Somebody reported this is fonts issue:

[http://appdb.winehq.org/commentview.php?iAppId=2249&iVersionId=6278&iThreadId=16500](http://appdb.winehq.org/commentview.php?iAppId=2249&iVersionId=6278&iThreadId=16500)

2. You have copied the wrong MSVCR80.dll
Search your windows box (where you already have Silo installed) for MSVCR80.dll. See if if it has other MSVCR80.dll in other folders (not system32). If you find it, try it one by one. Remember to kill all wine processes every time you want to start Silo again.

3. Try MSVCR80.dll from below file:

[http://www.christopherlewis.com/wget/ssllibs.098b.b.zip](http://www.christopherlewis.com/wget/ssllibs.098b.b.zip)

Unzip it and you could find MSVCR80.dll there, and try to run with it.

Hopefully the above solutions could solve your problem. You are very close to running your program in linux. By the way, you should keep the option one as I think it is good to have your wine complete with all kind of fonts, just in case some programs need it but it did not pack the fonts with it.

DK

---

### Post by yabbadabbadont on 2007-04-02
Is it possible that you need to run winecfg and specify that it should use the native dlls instead of the built-in versions?

---

### Post by mech7 on 2007-04-03
> **yabbadabbadont said:**
> Is it possible that you need to run winecfg and specify that it should use the native dlls instead of the built-in versions?

Where exaclty can i find this setting?

Moving the fonts did not work unfortunately :( also there are like 20 / 30 of the same dll files on my pc so i am not sure which one to choose 0_o

---

### Post by yabbadabbadont on 2007-04-03
> **mech7 said:**
> Where exaclty can i find this setting?

Moving the fonts did not work unfortunately :( also there are like 20 / 30 of the same dll files on my pc so i am not sure which one to choose 0_o

Here is the documentation from the WINE project on how to do it:

[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241)

---

### Post by mech7 on 2007-04-03
> **yabbadabbadont said:**
> Here is the documentation from the WINE project on how to do it:

[http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241](http://www.winehq.org/site/docs/wineusr-guide/config-wine-main#AEN241)

hmm i don't really understand that page but it says:

> DLLs usually get loaded in the following order:

   1.

      The directory the program was started from.
   2.

      The current directory.
   3.

      The Windows system directory.
   4.

      The Windows directory.
   5.

      The PATH variable directories. 

So shouldn't that dll be loaded from the dir then anyway ?

---

### Post by david_kt on 2007-04-03
Could you try the ones in you c:/windows/WinSxS folder? (inside the subfolders of this folder)

I found mine is inside these folders:

C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd
C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.163_x-ww_681e29fb

So, replace all 3 dll from system32 and copy it from here instead. 

DK

---

### Post by yabbadabbadont on 2007-04-04
> **mech7 said:**
> hmm i don't really understand that page

>  With that in mind, once you've copied the DLL you just need to tell Wine to try to use it. You can configure Wine to choose between native and builtin DLL's at two different levels. If you have Default Settings selected in the Applications tab, the changes you make will affect all applications. Or, you can override the global settings on a per-application level by adding and selecting an application in the Applications tab.

To add an override for FOO.DLL, enter "FOO" into the box labeled New override for library: and click on the Add button. To change how the DLL behaves, select it within the Existing overrides: box and choose Edit. By default the new load order will be native Windows libraries before Wine's own builtin ones (Native then Builtin). You can also choose native only, builtin only, or disable it altogether. 
Seems pretty clear to me.

---

### Post by mech7 on 2007-04-04
> **yabbadabbadont said:**
> Seems pretty clear to me.

Yes but on the bottom it says that it would load the dll's in the dir first so then it should not even matter right ?

---

### Post by david_kt on 2007-04-04
> **mech7 said:**
> Yes but on the bottom it says that it would load the dll's in the dir first so then it should not even matter right ?

Have you tried to use the dlls in the folder I mentioned before? I think you shouldn't play with wincfg first as there is native dll available. Now you just need to copy the correct dlls, and please try the ones I suggested.

I have tried to extract the dlls from the installation program, but I could not find it. So, looks like it just use the available dlls in the windows by pointing to the apporpriate ones. The earlier beta, it could not even get the correct dlls.

DK

---

### Post by mech7 on 2007-04-07
> **david_kt said:**
> Have you tried to use the dlls in the folder I mentioned before? I think you shouldn't play with wincfg first as there is native dll available. Now you just need to copy the correct dlls, and please try the ones I suggested.

I have tried to extract the dlls from the installation program, but I could not find it. So, looks like it just use the available dlls in the windows by pointing to the apporpriate ones. The earlier beta, it could not even get the correct dlls.

DK

Thanks for the help i tried the dll's from the link but it does not work.. I also don't get that dll in the program dir so i think it uses the default one. Am not sure why the error stays though :(

---

### Post by david_kt on 2007-04-09
> **mech7 said:**
> Thanks for the help i tried the dll's from the link but it does not work.. I also don't get that dll in the program dir so i think it uses the default one. Am not sure why the error stays though :(

I mean not from the link, but from your windows box:

C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.42_x-ww_0de06acd
C:\WINDOWS\WinSxS\x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.163_x-ww_681e29fb

Try to use all three dlls from that folders

DK

---

### Post by phunkycow on 2007-04-10
**[ From [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine) ]**

Hope it helps :)

[I]5.2 MSI

MSI is an installer by Microsoft that appears to replace Installshield. MSI's .msi files can be installed with a utility called "Windows Installer". You can download Windows Installer from this location: [Download]("http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe")

You can install Windows Installer by typing wine instmsia.exe

Now add the following lines to the DllOverrides of "Default Settings" using winecfg:

"msi" = "native, builtin" "msiexec.exe" = "native, builtin"

Now type wine msiexec /i msifile.msi and the application will be installed.[/I]

Edit: I did it and it worked for me.. Just have in mind that when you type "wine instmsia.exe" there will be no output, but it will install successfully. Good luck!

---

### Post by david_kt on 2007-04-10
> **phunkycow said:**
> 

Edit: I did it and it worked for me.. Just have in mind that when you type "wine instmsia.exe" there will be no output, but it will install successfully. Good luck!

Do you mean it work to install the said program or just any other msi file? I tried to manually extract the required dlls from the installation program but I could not find it, so, most likely, even if the installation is successful, the program will still not run because could not find required dll. But I can be wrong.

DK

---

### Post by mech7 on 2007-04-15
> **david_kt said:**
> Do you mean it work to install the said program or just any other msi file? I tried to manually extract the required dlls from the installation program but I could not find it, so, most likely, even if the installation is successful, the program will still not run because could not find required dll. But I can be wrong.

DK

Yes the dll's are also not in the program dir.. adobe seems to have allot of these dlls in their dirs as far as i can see on my windows 0_o
Don't really know what else i could do to get this working though :(

---

### Post by mech7 on 2007-04-21
Ok i found a solution.. it needs these files: [http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip](http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip)
posted in bug section: [http://bugs.winehq.org/show_bug.cgi?id=7409](http://bugs.winehq.org/show_bug.cgi?id=7409)

The menu's are still very buggy though sometiems they disseapear.. and it starts up with all preferences lost. If anybody knows how to fix the menu plz lemme know :)

[[IMG]http://img382.imageshack.us/img382/1997/screenshot2re0.th.png[/IMG]](http://img382.imageshack.us/my.php?image=screenshot2re0.png)

---

### Post by mech7 on 2007-04-30
The console is saying this:

> 
fixme:system:SystemParametersInfoW Unimplemented action: 8202 (SPI_GETFONTSMOOTHINGTYPE)
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented


Does anybody know what this mean or how to fix this ? :confused:

---

### Post by JeffreyRatcliffe on 2008-03-03
> **mech7 said:**
> The console is saying this:
Does anybody know what this mean or how to fix this ? :confused:

I fixed this by installing a new version of wine from winehq:

[http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/gutsy/wine_0.9.55~winehq0~ubuntu~7.10-1_i386.deb)

---

