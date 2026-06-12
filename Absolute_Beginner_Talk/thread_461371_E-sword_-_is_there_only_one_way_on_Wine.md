---
title: "E-sword - is there only one way on Wine?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ken_38 on 2007-06-01
Re yesterday's thread on GnomeSword2 and its dependencies.
Following the advice given I've decided to go with e-sword through Wine. Because of this, can I please have help with one more thing.
Do I have to install the e-sword package into /.wine?
OR
Can I use my e-sword installation on WindowsXP and make a link to it? I imagine it's the first option, but I thought that the second might be handier and space-saving as I could just copy over material I've put on it in XP.
Do I use only the Wine package listed in Synaptic? I see the Ubuntu doc. says the WineHQ newer Edgy version is "not recommended". Does this mean that it will cause problems, or that it hasn't yet been taken into Ubuntu itself?

---

### Post by david_kt on 2007-06-01
> **ken_38 said:**
> Re yesterday's thread on GnomeSword2 and its dependencies.
Following the advice given I've decided to go with e-sword through Wine. Because of this, can I please have help with one more thing.
Do I have to install the e-sword package into /.wine?
OR
Can I use my e-sword installation on WindowsXP and make a link to it? I imagine it's the first option, but I thought that the second might be handier and space-saving as I could just copy over material I've put on it in XP.
Do I use only the Wine package listed in Synaptic? I see the Ubuntu doc. says the WineHQ newer Edgy version is "not recommended". Does this mean that it will cause problems, or that it hasn't yet been taken into Ubuntu itself?

I think you could do it both ways. But the how to I send you before is using separate folder (/.wine_Esword) not ./wine as somebody complain the dll downloaded affect other program running in ./wine.

To run your Esword on WindowsXP partition, you could try the steps, except just skip the installation of esword and its modules. After that, make sure you navigate to folder containing esword.exe in terminal and execute below command:

```
env WINEPREFIX=~/.wine_Esword wine e-sword.exe
```

I have not tried it before, so, please post here in case there is error (copy and paste the error appear in terminal).

If it run, you could make a launcher using below command:

```
env WINEPREFIX=~/.wine_Esword wine /path/to/folder/folder/e-sword.exe
```

It is good to try the above command in terminal first to see whether or not it is working before you make a launcher.

DK

---

### Post by ken_38 on 2007-06-01
Thanks for responding david_kt.
1] My e-Sword is in Program Files on my WinXP partition. I can navigate to /media/windows as per wine drives, but terminal doesn't recognise extending this to /program files - No such directory  OR to e-Sword - No such directory
2] Terminal says I need to use **wineprefixcreate** before I can enter a command using WINEPREFIX. I'm still very new to this. I didn't spot a line to do this. Have I mistaken your instructions, or is it just something I should do normally?
Sorry to be so slow in understanding.

---

### Post by david_kt on 2007-06-01
yes, you should follow the instruction I told you before:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

but just skip the installation of esword of you want to run from windows partition.

And whenever you want to navigate to a folder with space in the name (Program Files for example), put \ before the space:

cd Program\ Files

instead of cd Program Files

DK

---

### Post by ken_38 on 2007-06-02
Help! - I think I followed everything correctly up to the command to run e-Sword. Here's the relevant part from the terminal:

kennedy@kennedy-desktop:~$ cd /media/windows/Program\ Files/e-Sword
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ env WINEPREFIX=~/.wine_Esword wine e-Sword.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\media\\windows\\Program Files\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\windows\\Program Files\\e-Sword\\e-Sword.exe" failed, status c0000135
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ 

New to this, it seems I should have a dll installed which isn't there. Do I download it through Synaptic and how do I get it to where it is needed - or is it automatically picked up? The err:module line I don't even pretend to understand, except that things have failed. Your advice, please?:confused:

---

### Post by david_kt on 2007-06-02
> **ken_38 said:**
> 
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\media\\windows\\Program Files\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\windows\\Program Files\\e-Sword\\e-Sword.exe" failed, status c0000135
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ 

Yes, you are doing right. Now copy MSVBVM60.DLL from /media/windows/system32 (or /media/windows/system) to ~/.wine_Esword /drive_c/windows/system32. If you could not find it, you could download it from [http://www.dll-files.com](http://www.dll-files.com) or direct link [here]("http://www.dll-files.com/dllindex/download.php?msvbvm60download0UKmVDZMeO")

After that try to run it again. If it still complaint could not import MSVBVM60.DLL, go to ~/.wine_Esword /drive_c/windows/system32 and rename MSVBVM60.DLL to msvbvm60.dll (change from uppercase to lowercase), and try to run again.

DK

---

### Post by ken_38 on 2007-06-03
Thanks again for the help david_kt. I managed to do everything you suggested and reached the point of entering the run command which clearly tried to execute. This is the result pasted from terminal.

kennedy@kennedy-desktop:~$ cd /media/windows/Program\ Files/e-Sword
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ env WINEPREFIX=~/.wine_Esword e-sword.exe
env: e-sword.exe: No such file or directory
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ env WINEPREFIX=~/.wine_Esword wine e-Sword.exe
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:ole:OleLoadPictureEx (0xe07a24,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f9e0), partially implemented.
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ 

Is there a way forward ? I expect there is [I'm learning that in Ubuntu]  but at the moment I'm treading water and the shore seems some way off. Thanks again in anticipation.
EDIT - if you have a number of smileys on paste I think they are a colon followed by letter o.

---

### Post by david_kt on 2007-06-04
> **ken_38 said:**
> 
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:ole:OleLoadPictureEx (0xe07a24,18910,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f9e0), partially implemented.
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3


Have you put oleaut32.dll to your ~/.wine_Esword /drive_c/windows/system32 ? Have you set oleaut32.dll to native for e-sword.exe in winecfg (env WINEPREFIX=~/.wine_Esword winecfg) ? Looks like it complaint about oleaut32.dll

Another way is to try to install it using wine first before trying the windows partition.

DK

---

### Post by ken_38 on 2007-06-04
Another day - and here I am again [oh no! I hear you cry]
The story so far. Got oleaut32 into drive_c and into winecfg as native only - I assume other native options were wrong. Ran the command as last time and got:

kennedy@kennedy-desktop:~$ cp /media/windows/WINDOWS/system32/oleaut32.dll -t ~/.wine_Esword/drive_c/windows/system32
kennedy@kennedy-desktop:~$ env WINEPREFIX=~/.wine_Esword winecfg
kennedy@kennedy-desktop:~$ cd /media/windows/Program\ Files/e-Sword
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ env WINEPREFIX=~/.wine_Esword wine e-Sword.exe
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject class {66833fe6-8583-11d1-b16a-00c0f0283628} not registered
err:ole:CoGetClassObject no class object {66833fe6-8583-11d1-b16a-00c0f0283628} could be created for context 0x3
kennedy@kennedy-desktop:/media/windows/Program Files/e-Sword$ 

Looks like the second line Load Picture has disappeared - otherwise the same. Any ideas? If it's going to get more involved, perhaps I should just cut losses and download e-Sword to wine - or perhaps we can fight through to the end.

---

### Post by david_kt on 2007-06-04
> **ken_38 said:**
> Another day - and here I am again [oh no! I hear you cry]
The story so far. Got oleaut32 into drive_c and into winecfg as native only - I assume other native options were wrong. Ran the command as last time and got:

Looks like the second line Load Picture has disappeared - otherwise the same. Any ideas? If it's going to get more involved, perhaps I should just cut losses and download e-Sword to wine - or perhaps we can fight through to the end.

As I do not have ubuntu with me now as I am on business trip (I am still using windows xp for work), it is difficult for me to figure it out. I suggest you just use the how to exactly how I have written it. Only after successful implementation, you could try to run it from your windows partition (as I never done it before). 

But I thought you already have E-sword installer so that you do not need to download again? In that case you just need to run the installer in wine, from whatever place it is. And it will install in .wine_Esword folder.

After you could run it, copy your entire folder (/media/windows/Program Files/e-Sword) to ~/.wine_Esword/drive_c/Program Files/e-Sword, and run it from ~/.wine_Esword/drive_c/Program Files/e-Sword so as not to repeat the whole module installation that you have in your windows partition.

DK

---

### Post by ken_38 on 2007-06-15
DAVID_KT --- I haven't got back to you sooner as I didn't want to hassle you on your business trip. I decided to scrap my idea of accessing e-Sword directly from my XP partition. The result of my last effort in trying to apply your suggestions was a whole list of error messages etc. which spilled down the terminal page and down a fresh part of the screen. I don't make it easy!

I removed Wine completely and did a re-install, downloading e-Sword from the website --- it settled itself on my Desktop. I then followed your guide on the relevant thread. e-Sword appeared to install successfully. I then had a "new user" problem. Where was the installation directory you mention from which I was supposed to run e-Sword? I couldn't find it listed in Search for Files. So I tried running it from Desktop and then from my home directory with this result:

kennedy@kennedy-desktop:~$ cd ~/Desktop
kennedy@kennedy-desktop:~/Desktop$ ls
setup785.exe
kennedy@kennedy-desktop:~/Desktop$ env WINEPREFIX=~/.wine_Esword wine e-sword.exe
wine: could not load L"c:\\windows\\system32\\e-sword.exe": Module not found
kennedy@kennedy-desktop:~/Desktop$ env WINEPREFIX=~/.wine_Esword/drive_c/windows/system32 wine e-sword.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/kennedy/Desktop', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\e-sword.exe": Module not found
kennedy@kennedy-desktop:~/Desktop$ cd ~/
kennedy@kennedy-desktop:~$ env WINEPREFIX=~/.wine_Esword wine e.sword.exe
wine: could not load L"c:\\windows\\system32\\e.sword.exe": Module not found
kennedy@kennedy-desktop:~$ 

I imagine I've done something basically silly, but can't work out what it is. Or is it possible that e-Sword didn't really install? I'm hoping that I'm close enough to a solution for you to provide me with the answer which will  resolve the problem. I expect you'll be glad to see this come to a successful conclusion too.:eek:

---

### Post by ken_38 on 2007-06-19
Is there any guidance to get me past the latest problem in my message of three days ago?
:confused::confused::confused:

---

### Post by david_kt on 2007-06-21
> **ken_38 said:**
> DAVID_KT --- I haven't got back to you sooner as I didn't want to hassle you on your business trip. I decided to scrap my idea of accessing e-Sword directly from my XP partition. The result of my last effort in trying to apply your suggestions was a whole list of error messages etc. which spilled down the terminal page and down a fresh part of the screen. I don't make it easy!

I removed Wine completely and did a re-install, downloading e-Sword from the website --- it settled itself on my Desktop. I then followed your guide on the relevant thread. e-Sword appeared to install successfully. I then had a "new user" problem. Where was the installation directory you mention from which I was supposed to run e-Sword?

I imagine I've done something basically silly, but can't work out what it is. Or is it possible that e-Sword didn't really install? I'm hoping that I'm close enough to a solution for you to provide me with the answer which will  resolve the problem. I expect you'll be glad to see this come to a successful conclusion too.:eek:

Sorry I am not able to respond to you sooner. It is quite easy actually. What you need to do is:
```
cd .wine_Esword/drive_c/Program\ Files/e_Sword
```

Please note that the dot (.) in front of the folder name means the folder is hidden, so that you do not see .wine_Esword folder if you open nautilus.

After you are in that folder, run

```
env WINEPREFIX=~/.wine_Esword wine e-sword.exe
```

Try to make launcher with command like this:

```
env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe'
```

You could also try to run that command in terminal to see if that is correct command (do not require to go to installation folder).

If that fail, try below command:

```
sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
```

Never mind about my business trip as I always in business trip nowadays. The only problem is I have to help you bases on my memory only as I am using windows xp on my laptop.

DK

---

### Post by ken_38 on 2007-07-09
Greetings david_kt!
Used the first line of code to get into the folder, then ran second line and YES!!! e-Sword launched. Trouble was at the same time a whole list of stuff appeared on the terminal [see below]. In spite of this I tried to make a launcher in the terminal [was that right?] and I got the > line which I didn't know what to do with. I found I couldn't change directory, so I tried typing e.sword.exe and nothing happened  [shows I'm still breaking out of my Windows shell].

[email]kennedy@kennedy-desktop:~/.wine[/email]_Esword/drive_c/Program Files/e-Sword$ env WINEPREFIX=~/.wine_Esword wine e-sword.exe
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:AnimateWindow partial stub
fixme:win:AnimateWindow partial stub
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:AnimateWindow partial stub
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:AnimateWindow partial stub
fixme:win:LockWindowUpdate (0x1002c), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
[email]kennedy@kennedy-desktop:~/.wine[/email]_Esword/drive_c/Program Files/e-Sword$ [COD]env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-sword.exe'[/code]
> cd
> e-sword.exe
> 

1]Trouble is, I don't know whether the > means it has worked or not, or what to do next, and I don't want to mess things up now we've got so far.
2] If I can't set up a launcher, do I have to go to the folder and type the second line of code every time I want to use the program?

Thanks again.

---

### Post by david_kt on 2007-07-10
> **ken_38 said:**
> 
1]Trouble is, I don't know whether the > means it has worked or not, or what to do next, and I don't want to mess things up now we've got so far.
2] If I can't set up a launcher, do I have to go to the folder and type the second line of code every time I want to use the program?

Thanks again.

If you could run E-sword, then yes you have installed it successfully. Don't worry about all the error code on terminal, it does not have any effect so far. But you should make launcher to make it easier to run, and also not to see any error message.

Well, to make launcher is not in the terminal, but on your desktop. Right click on blank space on your desktop, and then choose "create launcher". And you need to make name for your launcher, you could add icon as well, I have provided an icon on that how to to use. You could save it anywhere, and navigate from your launcher to that icon.

But the most important is the command line. Please put below command:

```
env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe'
```

Please see below video showing how to create launcher:

[http://youtube.com/watch?v=nda5q4qGv8g](http://youtube.com/watch?v=nda5q4qGv8g)

That is the easy one. But there is another way to create launcher, and this is to integrate the launcher with ubuntu menu.

Open terminal and run below command:

```
gksudo gedit /usr/share/applications/Esword.desktop 
```

It will request your password, so key in your password.
After that it will open a blank sheet, copy and paste below command:

```
[Desktop Entry]
Name=E-Sword
Comment=E-sword running under wine
Categories=Application;office

Exec= sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
Type=Application
Icon=yourfile.png

```

And then save that file, then you will have E-sword launcher on your menu, under office submenu.

For the icon, you have to change yourfile.png to real file (for example esword.png), and this file/icon has to be placed on /usr/share/pixmaps folder. Otherwise, you could just ignore this icon it will still work, but there would be no icon in your launcher.


Please let me know if you still unable to create launcher.

After you are able to make, it is time to install modules, quite easy.

DK

---

### Post by ken_38 on 2007-07-10
Thanks for your last post.

I did the create launcher bit, entering the command line as given. The launcher appeared on the desktop OK but  when I tried running the program I received the following launch error message:

**Text ended before matching quote was found for '. (The text was 'env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe'')**

I tried removing the ' at the end of the line in case it was an error, and launching. Nothing happened. I tried inserting one at the beginning and launching. An error message came up:

**Failed to execute child process* "command line as copied from post"* (No such file or directory**).

I also tried the section for integrating with the ubuntu menu. I entered the terminal command and password and got the gedit screen, but also the following terminal message:

[B]kennedy@kennedy-desktop:~$ gksudo gedit /usr/share/applications/Esword.desktop
(gedit:13870): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

I went ahead with the gedit code anyway and saved it, changing the Icon entry to Esword.ping [still working on icon but noted that it should run anyway without it]. Clicked on save and closed gedit and terminal. Went to Applications/Office on the menu. Nothing.

I'm quite happy if we can get the desktop launcher to respond, but am puzzled about the menu option.

Thanks again.

---

### Post by david_kt on 2007-07-10
I think there was a typing error, there should not be any ' or " in the command line:

```
env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe
```

Please remove the ' or " in the beginning and the end of command line.

But for the menu integration, it is correct you must have ' (just copy and paste the code I give).Please remove the icon line, it might cause the menu could not appear. So I think for the icon either you should put it correct, or remove it. It would work without icon.

Please let me know if you still have issue.

DK

---

### Post by ken_38 on 2007-07-10
To let you know.

I removed the ' as you said and checked the command line. Tried to launch from desktop. Nothing happened.

As for the menu launcher, I re-pasted the code and saved [by the way that strange message on the terminal came up again]. Went to applications/office - nothing there. Tried removing the icon line. Same result. Had to close down computer for an hour.

On restart checked under Applications. New entry Other - and there was eSword [how did it get there?]. Yes! BUT - on trying to launch from there - nothing. So two starting points, but going nowhere.

Can't think what I might have done wrongly or even failed to do. Aaargh.

---

### Post by david_kt on 2007-07-10
Could you open terminal and run this command to see if e-sword could launch:

```
env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe
```

If it could not launch, post the error here.

And also run below command in terminal to see if e-sword could launch:

```
sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
```

If it could not launch, post the error here.

DK

---

### Post by ken_38 on 2007-07-10
First command line works fine in terminal, as it did yesterday - just doesn't work on launcher.

Second command line produced error message:

kennedy@kennedy-desktop:~$ sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
wine: invalid directory ~/.wine_Esword in WINEPREFIX: not an absolute path
kennedy@kennedy-desktop:~$ 

I'm not sure what this is saying, but I'm confident you will be.

---

### Post by david_kt on 2007-07-10
That is good. We will concentrate on the command that is working. So, could you replace the command in the menu integration from:

```
Exec= sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
```

To

```
Exec=env WINEPREFIX=~/.wine_Esword wine ~/.wine_Esword/drive_c/Program\ Files/e-Sword/e-sword.exe
```

And after you save that file try to launch using the menu launcher.

As for the desktop launcher, it should work actually, just make sure the command is exactly the same as the one you run in terminal (without navigating to the E-sword folder).

As for the second command, it require to give absolute path. So, instead of:

```
sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=~/.wine_Esword wine e-sword.exe'
```

the command shoud change to


```
sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=/home/kennedy/.wine_Esword wine e-sword.exe'
```

I am guessing your abolute path here. But let's forget about the second command as we just need one working-command to move on. The second command is for certain program that require us to be in the program folder in order to run properly. But for esword, I think we do not need to be in the program folder, i.e. we could call the program from any location because you said that the first command is working.
DK

---

### Post by ken_38 on 2007-07-11
Guess what? I entered the command
***sh -c 'cd ~/.wine_Esword/drive_c/Program\ Files/e-Sword && env WINEPREFIX=/home/kennedy/.wine_Esword wine e-sword.exe'***
in the Exec= line in gedit, saved, exited and tried launching from the menu - IT WORKED!! Thank you.:D

As to the desktop launcher - I checked that I had entered the same command in the icon's Properties/Launcher /Command line as I originally did in Terminal. BUT when I click on the icon it simply highlights, but nothing happens at all. *Yet the same command works from the Terminal.*

Perhaps I should just get rid of the desktop launcher, work from the menu and start adding the modules - which you have said is straightforward. What do you think? It just leaves a puzzling loose end.

By the way - I suppose I can now get rid of the **setup785.exe** icon on my desktop?

Thank you for your long and patient journey with me. I hope I've learned a few things on the way.

---

### Post by david_kt on 2007-07-11
Congratulation, you are almost done with your e-sword. And this would be very good experience for you in case you want to install other software in the future.

For the desktop launcher, you could delete it, and create a new one with just a few clicks. First navigate to your Esword menu you have created, but instead of run it, try right click, and then select add launcher to desktop (or something like that). And you will have new-working-desktop-launcher now. But may be you want to add this launcher to the desktop after you completed the menu with icon.

Now I will guide you to add icon:

```
sudo cp ~/Desktop/esword.png /usr/share/pixmaps/esword.png
```

Alternatively, you could do:

```
gksudo nautilus
```

It will open nautilus, and you should navigate to your esword.png, copy it, and navigate to /usr/share/pixmaps folder, and paste it there. After that close nautilus as it is not a good idea to run nautilus using gksudo.

After that go back to  
```
gksudo gedit /usr/share/applications/Esword.desktop
```

add back 
```
Icon=esword.png
```

It is also very nice to add below line:

```
StartupNotify=true
```

It would notify you that it is starting Esword when you launch it.

Please let me know if you have issue with this. And how about installing modules? Do you have any issue?

DK

---

### Post by ken_38 on 2007-07-11
Suddenly it all went smoothly!:):)

I deleted the desktop launcher, then went to the terminal and into gedit. I entered the commands you listed, putting my icon name in that line and adding the startup line. The program launched without a hitch.

Back to the menu and had it place the launcher on the desktop. Again, started up e-Sword with no problem.
Success at last. Many thanks for guiding me through. You're right - this has been a helpful learning curve. - though I feel I've been a slow learner.

If you can bear it, I would like to be clear about adding modules. Do I download and then open them in the way I would in XP, or is there a special way of doing it?

---

### Post by david_kt on 2007-07-11
It is not the same as in windows, but it is very straight forward.

[LIST=1]
[*]Download/copy the module you want to install to your linux box (for example you put it in Desktop)
[*]Open terminal
[*]CD Desktop
[*]run below command:

```
env WINEPREFIX=~/.wine_Esword WINEDLLOVERRIDES="riched20=n" WINEDLLOVERRIDES="riched32=n" wine yourmodule.exe
```
[/LIST]

You should change yourmodule.exe to whatever module you have on your desktop.

Please let me know if you have trouble with it although I have tried to make it as clear as possible.

Just for experiment, as I also never done it before, you could try to run your esword at your windows partition now:[LIST=1]
[*]Open terminal
[*]Navigate to program folder in your windows partition containing e-sword.exe
[*]Run below command:
```
env WINEPREFIX=~/.wine_Esword wine e-sword.exe
```
[/LIST]

Theoritically, you should be able to run your esword in your windows partition, complete with all the modules you have installed.

Another method is to copy your windows program to linux partition, but as of now do not do it first as I worry you make a mistake that ruin all your effort so far.

DK

---

### Post by ken_38 on 2007-07-12
We're there!

The modules downloaded and installed without any problem.

I tried the experiment twice. First before I downloaded anything and, sure enough there was e-Sword called from the windows partition. Then I ran the command again from windows after loading the modules, and there was e-Sword again, this time with all the modules I had added. It seems that the experiment is no longer theoretical.

I don't think there is much left to do on this e-Sword thread - unless you want me to try copying the windows program to the linux partition. On the other hand it may be that I'm not ready for that yet.

In any case - well done and thank you. This helping and being helped from miles away is a great thing.

---

### Post by david_kt on 2007-07-12
There is no need to copy anything from windows now as you have installed your modules. But if your modules are many, it takes time to installed them again. As such, copying all the files in the C:\Program Files\e-Sword to your linux partition (but not overriding existing files) will do the trick. But I have never tried it before, so, please do not try it, just install your modules.

By the way, I have found E-sword portable, I have tried it in windows. No installation needed, just copy and paste. I will try it in wine once I arrived home, and if it is successfull I will post it here.

The beauty of E-sword portable is you could bring your E-sword on usb disk, and run it from any computer without installation. If it could run in wine, this portable E-sword would be fantastic.

DK

---

### Post by ken_38 on 2007-07-12
E-sword portable? Great idea. Didn't know that. Good that it works for windows
BUT
Post your results here for wine whatever happens, please.

---

### Post by ken_38 on 2007-07-13
I have used -e-Sword today and it seems to be working fine, except for one thing.

I wanted to print out some text, clicked on the print icon and selected the text then the print button. The print screen came up listing the settings as dummy and with no printer selected. I tried the dropdown printer list and there was my HP8200 Photosmart listed. I clicked on it. The print screen disappeared. e-Sword closed down. Nothing printed. I tried again and on the print screen tried the options button, but nothing there was relevant.

I then went into terminal and cd to my windows partition, calling up e-sword from there. I tried the process again, with exactly the same result.

I went to the Wine document on ubuntu website. Nothing there about printer settings. Not sure where to go from here. The printer works correctly in Open Office and other programs. I assume there must be a setup procedure as either Wine or e-Sword is not automatically recognizing my printer - but where can I locate it?:confused:

---

### Post by david_kt on 2007-07-13
I have not tried any printing with wine yet so far. May be in near future I will give it a shoot and see what I can do to make it work. In the mean time, you could post another request to the forums titled "Printing with wine" for example. I think there are other people have already done it.

For the start, you could try below instruction:

[http://www.codeweavers.com/support/docs/wine-user/config-printing](http://www.codeweavers.com/support/docs/wine-user/config-printing)

DK

---

