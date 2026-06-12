---
title: "Why is it so HARD to play STEAM games on Ubuntu??"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by FreemanChief on 2006-12-07
I got into this hell hole because i hear it's really user friendly...oh look! i spent half a day simply trying to get Ubuntu to understand that i have 2 NIC's....so all my information is gone and i'm stuck with this.... so how do i get WINE and how do i install it?

---

### Post by Tomosaur on 2006-12-07
Basically, it's because Steam is written for Windows. 

```

sudo aptitude install wine

```

to install Wine. Good luck :)

---

### Post by FreemanChief on 2006-12-07
Yeah so how do i fix this? where should i d/l wine?

---

### Post by mcduck on 2006-12-07
Tomosaur just gave you command that will automatically download and install wine for you.

[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by FreemanChief on 2006-12-07
ftf2006@ftf2006-desktop:~$ sudo aptitude install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
ftf2006@ftf2006-desktop:~$ wine SteamInstaller.exe
wine: could not load L"c:\\windows\\system32\\SteamInstaller.exe": Module not found
ftf2006@ftf2006-desktop:~$

---

### Post by esaym on 2006-12-07
Welcome to the forum

You might be frustrated with ubuntu but alot of us users are frustrated with new members coming in here, blaming us or ubuntu for their problems, and demanding a simple fix.

Yes ubuntu is the most user friendly of all the linux distros imo.  You shouldn't have deleted your whole hard drive to install it though.  Linux takes awhile to learn and it takes lots of reading and patience.  

I do not game but there is alot of info about wine and other programs like wine in the gaming forum

---

### Post by meng on 2006-12-07
So SteamInstaller.exe is located in ~            ?

---

### Post by FreemanChief on 2006-12-07
i wasnt blaming you...but why dont you all just d/l windows? its free...just bittorrent it....and its very user friendly

any one have an answer to my problem ^

---

### Post by finferflu on 2006-12-07
I didn't know Windows was free... :P - and by the way, this looks like trolling to me, and I won't take this further...

---

### Post by FreemanChief on 2006-12-07
Oh, it is...just buy a two-thousand dollar box! (The computer)

---

### Post by fatneck on 2006-12-07
votekick freemanchief [4 more votes required]

---

### Post by FreemanChief on 2006-12-07
The SteamInstaller.exe is located right on my desktop. (one of them atleast)

---

### Post by MetalMusicAddict on 2006-12-07
> **FreemanChief said:**
> i wasnt blaming you...but why dont you all just d/l windows? its free...just bittorrent it....and its very user friendly

Are you serious?! Its not free at all. You MUST be a kid to openly have this level of ignorance.

Ubuntu, is free. You must have mistyped.

---

### Post by meng on 2006-12-07
> **FreemanChief said:**
> The SteamInstaller.exe is located right on my desktop. (one of them atleast)
Well if it's on your Desktop, then it isn't located in ~, it's located in ~/Desktop, and so of course your command won't work.

Try:
cd Desktop
wine SteamInstaller.exe

---

### Post by FreemanChief on 2006-12-07
I was making a joke, read my last post on first page :)

---

### Post by finferflu on 2006-12-07
> **fatneck said:**
> votekick freemanchief [4 more votes required]

How do you votekick?

---

### Post by FreemanChief on 2006-12-07
ftf2006@ftf2006-desktop:~$ cd Desktop
ftf2006@ftf2006-desktop:~/Desktop$ wine SteamInstaller.exe
wine: could not load L"c:\\windows\\system32\\SteamInstaller.exe": Module not found
ftf2006@ftf2006-desktop:~/Desktop$

---

### Post by FreemanChief on 2006-12-07
you have to type "rockthevote" then "votekick *playername*"
or just hit f10...
some servers give you shotguns with f10 :-D

---

### Post by meng on 2006-12-07
Just humor me a little further then. Could you list the contents of the directory:
ls

because Linux is case-sensitive, and I just want to check exactly how this SteamInstaller.exe program is listed.

---

### Post by finferflu on 2006-12-07
> **FreemanChief said:**
> ftf2006@ftf2006-desktop:~$ sudo aptitude install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
ftf2006@ftf2006-desktop:~$ wine SteamInstaller.exe
wine: could not load L"c:\\windows\\system32\\SteamInstaller.exe": Module not found
ftf2006@ftf2006-desktop:~$

Actually, how did you know how to use wine, when you didn't even know (or pretend not to know) how to use the command you were given earlier?

Troll.

---

### Post by FreemanChief on 2006-12-07
Yeah, about that... See in windows i just type "dir" and everything is listed! but noooo here in Ubuntu world...im sure theres a long ...NON user friendly command..let me hear it

---

### Post by meng on 2006-12-07
ls

---

### Post by FreemanChief on 2006-12-07
Im in Cisco Net Acadamy... I know a LITTLE about computers....you might say...
But this is rediculous... lol I have an easier time using Windows 3.1

---

### Post by FreemanChief on 2006-12-07
ftf2006@ftf2006-desktop:~$ cd Desktop
ftf2006@ftf2006-desktop:~/Desktop$ ls
hldsupdatetool.bin            new file   SteamInstall.exe
install_flash_player_7_linux  new file~
ftf2006@ftf2006-desktop:~/Desktop$

---

### Post by FreemanChief on 2006-12-07
odd....i listed the directory...then tried wine again..and it worked...does ls tell ubuntu  that the files are there? why doesnt ubuntu know already? isnt that what NTFS is for? does ubunut USE NTFS?

---

### Post by meng on 2006-12-07
Have you run:
winecfg

It's a good idea to do this before trying anything else with wine.

Also have you seen this help page?
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by FreemanChief on 2006-12-07
ftf2006@ftf2006-desktop:~$ cd Desktop
ftf2006@ftf2006-desktop:~/Desktop$ ls
hldsupdatetool.bin            new file   SteamInstall.exe
install_flash_player_7_linux  new file~
ftf2006@ftf2006-desktop:~/Desktop$ start SteamInstall.exe
bash: start: command not found
ftf2006@ftf2006-desktop:~/Desktop$ wine SteamInstall.exe
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF9c1.tmp") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:GetFileSecurityW (L"C:\\windows\\temp\\GLF9c9.tmp") : returns fake SECURITY_DESCRIPTOR
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc WM_SETFONT: stub
fixme:richedit:RichEditANSIWndProc EM_LIMITTEXT: stub
fixme:shell:IShellLinkA_fnGetPath (0x7fdb77e8): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\\"C:\\Steam\\steam.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x7fdb77e8): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\\"C:\\Steam\\unwise.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x7fdb77e8): WIN32_FIND_DATA is not yet filled.
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\\"C:\\Steam\\steam.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
ftf2006@ftf2006-desktop:~/Desktop$
ftf2006@ftf2006-desktop:~/Desktop$

---

### Post by meng on 2006-12-07
> **FreemanChief said:**
> odd....i listed the directory...then tried wine again..and it worked...does ls tell ubuntu  that the files are there? why doesnt ubuntu know already? isnt that what NTFS is for? does ubunut USE NTFS?
Actually, it's not that much of a mystery. There's a big difference between
wine SteamInstaller.exe

and

wine SteamInstall.exe

Now, I know you know more than a little about computers, so it probably won't take you too long to see what the difference is.

---

### Post by FreemanChief on 2006-12-07
what about *this* error?

---

### Post by SunnyRabbiera on 2006-12-07
Ubuntu is not NTFS based, it is ext3 based.... and that is sort of like fat32 on windows.
Dont expect ubuntu to do everything windows does, it is not a replacement it is an alternative to windows.
Many make that mistake, ubuntu and other linux variations are not windows replacements but they will do a good job if you know what to do.
I personally suggest a dual boot for games, most games will not work under wine and might be XP only.
Like I said use a dual boot, its easy to do.

---

### Post by Chinkostu on 2006-12-07
> **FreemanChief said:**
> odd....i listed the directory...then tried wine again..and it worked...does ls tell ubuntu  that the files are there? why doesnt ubuntu know already? isnt that what NTFS is for? does ubunut USE NTFS?

no. EXT.

NTFS does not magically make every program know where a file is. you seem to have a fairly basic grasp of what file systems are.

---

### Post by finferflu on 2006-12-07
Come on people! this is obvious trolling! He's got already 15 posts with this stupid thread, let's not keep it up in the list!

I already know that game is not gonna work, because he already knows!

---

### Post by xpod on 2006-12-07
I still cant get my head round why sooo many folks go jumping in feet first and even wiping Windows just to get ubuntu with wine etc:confused: 

But then what do i know:-k 

Good luck either way FC

---

### Post by Henry Rayker on 2006-12-07
> **FreemanChief said:**
> odd....i listed the directory...then tried wine again..and it worked...does ls tell ubuntu  that the files are there? why doesnt ubuntu know already? isnt that what NTFS is for? does ubunut USE NTFS?

No, Ubuntu and Linux in general doesn't use NTFS because it is a proprietary file system.

I just think maybe you should re-wipe your drive and reinstall Windows XP. Not only do you have an incredibly condescending attitude about the way things are done here
> Yeah, about that... See in windows i just type "dir" and everything is listed! but noooo here in Ubuntu world...im sure theres a long ...NON user friendly command..let me hear it
Reply With Quote

but I don't know that Ubuntu will meet your needs.

---

### Post by TheRingmaster on 2006-12-07
[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by FreemanChief on 2006-12-07
ok....i got it to work...but now the steam update stops at 26%....\

---

### Post by elizleisndahizle on 2006-12-12
Just follow this and you should be good.
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games")

---

### Post by mightyzug on 2007-09-25
> **FreemanChief said:**
> Yeah, about that... See in windows i just type "dir" and everything is listed! but noooo here in Ubuntu world...im sure theres a long ...NON user friendly command..let me hear it

i know this is an old thread but i dug it up while gettin ready to set up my cs:s, and i couldnt resist

whoever said it up there was right, this douche is an obvious troll, and not even a good one, cisco academy rofl yea right!! 

what a pathetic piece of loser.

---

