---
title: "Can't get Wine to work!!!!"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by adamd on 2007-08-09
I have searched and searched and tried every single tutorial on how to install Wine on Ubuntu and not one of them has worked like the tut-writer has said and now I am getting very frustrated. If anyone can point me in the direction of the most thorough guide on how to get Wine working I would love you. Remember though that I know absolutely nothing about Ubuntu and just started using it. Thanks a lot.

---

### Post by Billy_McBong on 2007-08-09
```
sudo apt-get install wine
```
[COLOR="Blue"]that should install wine[/COLOR]

---

### Post by JParkus on 2007-08-09
Have you already tried installing it with synaptic?

Thats the way I did it and it worked fine for me

---

### Post by GameManK on 2007-08-09
The usual method is to install the 'wine' package in synaptic, then run "winecfg".  After that you should be able to install and run windows applications by running "wine /path/to/the/exe".  What goes wrong?

---

### Post by adamd on 2007-08-09
1) I already tried the sudo apt thing and that didn't work.

2) How do you install the wine package in Synaptic?

3) What is Synaptic?

4) After you have installed it how do you run "winecfg?"

5) How do you run wine/path/to/the/exe?

6) Mostly what went wrong is that I don't know much at all about Ubuntu so I can't figure it out.

Thanks again for all the quick replies.

---

### Post by toidi on 2007-08-09
> **adamd said:**
> 1) I already tried the sudo apt thing and that didn't work.

2) How do you install the wine package in Synaptic?

3) What is Synaptic?

4) After you have installed it how do you run "winecfg?"

5) How do you run wine/path/to/the/exe?

6) Mostly what went wrong is that I don't know much at all about Ubuntu so I can't figure it out.

Thanks again for all the quick replies.

2/3. Click 'System' Then 'Administration' then 'Synaptic package manager'

do a search for 'wine' (it should come up with lots of answers.   Tick the 'wine' box and then apply.  This should install wine for you.

4. Click 'Applications' 'Accessories' and then 'Terminal'

It should bring up a cmd like box like windows cmd box.

Just type winecfg into it and it should load up a windows style configuration system.

All that I am proficient enough in at this time to answer.  Try [www.winehq.com](www.winehq.com) as they have lots and lots of tutorials on how to use wine with windows apps and games.

Hope this helps..

---

### Post by EXCiD3 on 2007-08-09
You can also install Automatix ([http://www.getautomatix.com]("http://www.getautomatix.com")) and choose to install Wine in it. Many people don't like Automatix as it has broken systems, however i have never had that problem. Just download the .deb and double click on it to install it. Then go run it from the menu and check the Wine box under the Virutalization section and click apply. It will download and install it for you. It will also run Winecfg for you too.

---

### Post by GameManK on 2007-08-09
First of all, I recommend you familiarize yourself with Ubuntu, the included software, and how to install programs on Ubuntu before trying to use wine.

> **toidi said:**
> 4. Click 'Applications' 'Accessories' and then 'Terminal'

It should bring up a cmd like box like windows cmd box.

Just type winecfg into it and it should load up a windows style configuration system.

This can also usually be done from the Run dialog (Alt + F2)

> **adamd said:**
> 
5) How do you run wine/path/to/the/exe?
When I said /path/to/the/exe I meant you would type in the location of the application you are trying to run.  You would do this in a run dialog or in a terminal window.  You should also be able to just double click the file in nautilus (the file manager) but I'm not sure if .exe's are run with wine by default.

Notepad is included with wine, so for example to run it you would run:
```
wine /home/yourusername/.wine/drive_c/windows/notepad.exe
```
Replace "yourusername" with your user name.
For notepad this would also work, but may not work for all applictions:
```
wine notepad.exe
```

Some applications installed in wine actually show up in your applications menu, but I wouldn't rely on it.

---

### Post by adamd on 2007-08-09
Thank you very much toidi. That worked perfectly but now I don't know how to run wine and download things for it such as Steam. Can anyone tell me how to do that now?

Thanks very much.

edit: GameManK, I tried both of your codes to run notepad and neither of them worked. I don't even know if I installed Wine correctly but I am pretty sure I did because I got a setup dialog type thing. And how do you suggest I familiarize myself with Ubuntu if I don't know anything about it or any of the commands. Is there some website that teaches you how to use it? Thanks.

---

### Post by GameManK on 2007-08-10
> **adamd said:**
> edit: GameManK, I tried both of your codes to run notepad and neither of them worked. I don't even know if I installed Wine correctly but I am pretty sure I did because I got a setup dialog type thing. And how do you suggest I familiarize myself with Ubuntu if I don't know anything about it or any of the commands. Is there some website that teaches you how to use it? Thanks.
I meant not so much commands, but even all the graphical stuff.  Try out the programs.  If you want to do something that's not already in the menu, search for it in Synaptic or in Add/Remove Applications and install some programs and give them a try.  Basically, use your computer for a while before trying to do advanced things like running beta software to emulate windows.

---

### Post by toidi on 2007-08-10
I posted a link in [http://ubuntuforums.org/showthread.php?t=521860&page=2](http://ubuntuforums.org/showthread.php?t=521860&page=2) with regards to getting steam working in wine.

Hope this helps..

Toi

---

### Post by adamd on 2007-08-10
GameManK, I have tried out a lot of the programs in the applications menu and looked around places but I don't understand all the seemingly random letters in my computer. I have also tweaked my preferences a little bit under system but that is about all I can figure out how to do. 

I just looked around the Synaptic Packet Manager a little bit and that is really cool. Now when I want something I don't have to search the internet. Thanks a lot. But how can I find fonts to use. Do I still have to search the internet? And when I do find them how do I download them and use them?

Also, how do you open Nautilus? When you do does it just show all the programs you have and you can remove them or run them?

Sorry about all the questions but thank you very much.

edit: I was wondering what the multiverse and universe things mean in the Synaptic Manager?

---

### Post by mlsquad on 2007-08-10
> **adamd said:**
> Thank you very much toidi. That worked perfectly but now I don't know how to run wine and download things for it such as Steam. Can anyone tell me how to do that now?From a command line type in *winecfg*.  From here you can configure various settings for wine.
Next download the Windows program you wish to run and run the installer.  It will install the program.  Then you just simply run the program.  Different programs work better than others in Wine so it will be a matter of trail-and-error to find what programs do and don't work.

---

### Post by adamd on 2007-08-10
Alright, when I tried following this link:

[http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037](http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037)

All I got when I typed "wine iexplore http://winehq.org" and "wine start SteamInstall.msi
" was:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/adam', starting in the Windows directory.
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Bad device type

I don't know what is wrong and I opened winecfg and made sure there was a drive C so I am kind of lost. Any help is appreciated.

edit: Also, whenever I search for wine or .wine in my hard drive no results come up which confuses me so I don't really know what is going on because I can open winecfg...

---

### Post by Vague on 2007-08-10
> **adamd said:**
> edit: I was wondering what the multiverse and universe things mean in the Synaptic Manager?

Multiverse and Universe are repositories that include things that aren't in the main, Canonical-supported Ubuntu repository.

---

### Post by GameManK on 2007-08-10
> **adamd said:**
> But how can I find fonts to use. Do I still have to search the internet? And when I do find them how do I download them and use them?

Also, how do you open Nautilus? When you do does it just show all the programs you have and you can remove them or run them?
There are some font packages in the repositories in synaptic.  There is more information on installing fonts here: [https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

I'm sure you've opened nautilus by now.  It's the program that shows you all your files.  I'm sure someone else can tell you more about it (I use Kubuntu, an ubuntu derivative with a different desktop interface, so the program I use for file browsing is Konqueror).  A file browser doesn't show you your applications.  You run applications through the applications menu.  You install and remove them through Synaptic.

---

### Post by splintercellguy on 2007-08-10
> **adamd said:**
> Alright, when I tried following this link:

[http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037](http://appdb.winehq.org/appview.php?iVersionId=1554&iTestingId=14037)

All I got when I typed "wine iexplore http://winehq.org" and "wine start SteamInstall.msi
" was:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/adam', starting in the Windows directory.
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Bad device type

I don't know what is wrong and I opened winecfg and made sure there was a drive C so I am kind of lost. Any help is appreciated.

edit: Also, whenever I search for wine or .wine in my hard drive no results come up which confuses me so I don't really know what is going on because I can open winecfg...

Do sudo rm -rf ~/.wine and run winecfg (make sure not to run as root).

---

### Post by superstylin on 2007-08-10
I am also a Linux newbie, and I could never figure out how to install steam.msi via some wine command, I would suggest the following:

1 - Open a terminal

2 - type "winefile"

3 - look for the steam file, should be on your desktop, double click and presto!

:)



Edit: ps, it seems you may be having some permission issues... >.<

Edit2: .wine is hidden by default, it wont show up on your searches if you havent enabled it... (not sure if you have :P)

---

