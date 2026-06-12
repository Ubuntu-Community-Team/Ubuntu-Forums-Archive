---
title: "Where's Wine?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by seannosaurusrex on 2007-03-26
I've been searching the forums for a while now, trying to figure out how to make Wine work. I believe I've succesfully installed Wine. I followed the instructions on the Wine HQ website for Dapper x86 6.06 LTS. Where can I find instructions on how to use wine? More importantly, where can I find Wine? I don't have a clue where it insatlled to. There also doesn't seem to be any links for downloading a manual. Wine-wiki dead ends at several links that sound promising. [This]("http://www.psychocats.net/ubuntu/wine") website implies that I should be able to simply double click on a .exe file and Wine will automatically open it.
This isn't working for me at all. As a test, I'm trying to install winamp (not that I need it, it's just a small/simple program). When I click on the .exe all I get is:

Couldn't display "/home/sean/Desktop/winamp533_lite.exe".

It's hard not to get frustrated coming over from Windows. I'm really trying, though. I loathe Microsoft's monopolistic empire. My desire to "stick it to the man" is all that's keeping me going. :P

---

### Post by Patrick K on 2007-03-26
You don't directly access wine like other programs. It's more like a shell for running win apps. In a terminal type "winefile" to open wine's file browser. You can navigate to the app you want to install's setup file. Double clicking setup.exe will start the install process. Let it install in the default "c:\program files" directory. 

To run the program type "wine programname" in a terminal window.

---

### Post by codesplice on 2007-03-26
You should be able to just type "wine" in the command line and get the abbreviated help prompt.... is this not happening?

For instructions on its use, check out "man wine", again at the command line.  

By default, wine should be installed in /usr/bin/

Hope this helps a little.

---

### Post by seannosaurusrex on 2007-03-26
Thank you very much! Man Wine should be helpful. The winefile command also works perfectly.

---

### Post by labinnsw on 2007-03-28
I am having the same problem on Edgy

Below is the result of what I have tried.

_[SIZE="6"]Step 1[/SIZE]_

user@user-desktop:~$ winefile
wine: creating configuration directory '/home/user/.wine'...
wine: Unhandled page fault on read access to 0x00000002 at address 0x7de6c63b (thread 0009), starting debugger...
err:syslevel:_EnterSysLevel (0x7ee51b80, level 2): Holding 0x7ed41600, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee51b80, level 2): Holding 0x7ed41600, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed41600 level 3
err:seh:raise_exception Unhandled exception code 80000003 flags 0 addr 0x7b8876b0
wine: wineprefixcreate failed while creating '/home/user/.wine'.
user@user-desktop:~$ wineserver: could not save registry branch to /home/user/.wine-uYPuYF/system.reg : No such file or directory
wineserver: could not save registry branch to /home/user/.wine-uYPuYF/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/user/.wine-uYPuYF/user.reg : No such file or directory
user@user-desktop:~$ 

_[SIZE="6"]Step 2[/SIZE]_

user@user-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
user@user-desktop:~$ 

_[SIZE="6"]Step 3[/SIZE]_

user@user-desktop:~$ wine programname
wine: creating configuration directory '/home/user/.wine'...
wine: Unhandled page fault on read access to 0x00000002 at address 0x7de6663b (thread 0009), starting debugger...
err:syslevel:_EnterSysLevel (0x7ee48b80, level 2): Holding 0x7ed38600, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee48b80, level 2): Holding 0x7ed38600, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed38600 level 3
err:seh:raise_exception Unhandled exception code 80000003 flags 0 addr 0x7b8876b0
wine: wineprefixcreate failed while creating '/home/user/.wine'.
user@user-desktop:~$ wineserver: could not save registry branch to /home/user/.wine-B5mxwr/system.reg : No such file or directory
wineserver: could not save registry branch to /home/user/.wine-B5mxwr/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/user/.wine-B5mxwr/user.reg : No such file or directory

[SIZE="6"]_Step 4_[/SIZE]

When I go to /usr/bin/wine (graphic mode) nothing happens.

---

### Post by david_kt on 2007-03-28
Labinnsw, how did you install wine? Looks like there was a problem with wine installation.

DK

---

### Post by WaeV on 2007-03-28
Hi I'm a new user and managed to get wine installed, but I could only get a certain program (Steam) working after I uninstalled it and reinstalled using the following method outlined on winehq.org.  Since you haven't done anything with wine yet, I would definetly look to installation for the cause of the problem.
[URL="http://www.winehq.org/site/download-deb"]
http://www.winehq.org/site/download-deb[/URL]

> Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Edgy (6.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'.

I don't know how to use synaptic well at this point.  I recommend just using the apt-get method.

---

### Post by labinnsw on 2007-03-29
On my first attempt I installed it from Synaptic. When that did not work, I uninstalled it and reinstalled it using instructions from Wine HQ

---

### Post by labinnsw on 2007-03-29
Thanks for the help Guys. I will uninstall Wine over the weekend  and when I reinstall it, I will make a log of the process incase anything goes wrong again.

---

### Post by david_kt on 2007-03-29
> **labinnsw said:**
> On my first attempt I installed it from Synaptic. When that did not work, I uninstalled it and reinstalled it using instructions from Wine HQ

OK, try to use synaptic again, and inform us exactly what happen when you said "it did not work". We will help you from there.

DK

---

### Post by labinnsw on 2007-03-30
I uninstalled wine by deselecting it in Synaptic. I checked /usr/bin to make sure there were no wine files there after the uninstall.

Then I reinstalled and checked the installation as outlined below.
1.In Synaptic, Select Wine, Mark for installation, Apply [wine Microsoft Windows Compatibility Layer (Binary Emulator and Library)]
Response Changes applied
Successfully applied all changes. 
Details: Selecting previously deselected package wine.
		(Reading database ... 127756 files and directories currently installed.)
		Unpacking wine (from .../win_0.9.33~winehq0~ubuntu~6.10-2_i386.deb) ...
		Setting up wine (0.9.33~winehq~ubuntu~6.10-2) ...
2.Search Applications Menu for wine, it is not there.
3.Search System Menu for wine, it is not there.
4.Restart the computer.
5.Repeat 2 and 3
6.go to /usr/bin and click on wine – Nothing happens.
7.Click on winebrowser , select display – Got package installer error: Could not open “winebrowser” The package might be corrupted or your are not allowed to open the file. Check the permissions of the file.
8.Click on winebrowser , select open in terminal – Got the following: Wine: creating configurationdirectory '/home/username/.wine'...
err: advpack:creat_tmp_ini_file Unable to create temp ini file
err: advpack:creat_tmp_ini_file Unable to create temp ini file
Then the terminal closes.
9.Repeat 7 and 8 this time with wineconsole – Got the same result
10.Repeat 7 with winelauncher – Got the same result
11.Repeat 8 with winelauncher – Got in Terminal: Wine called with no arguments.
Invoking /usr/bin/wine  ...
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Got in Welcome to Wine Window: You have started Wine without specifying any arguments.

Wine requires at least one argument – the name of the Windows application you would like to run.

If you have launched this through the KDE menu system and your KDE installation is specially donfigured for Wine, then you can use the KDE file browser to select a Windows executable and then click on it to launch Wine with that application.

You can similarly use the GNOME file manager to select a Windows executable and double click on it.

If you would like to see the command line arguments for Wine, select the second option, below.

The options are “Okay,” “See the Wine Usage Statement” and “Configure Wine.”

Something tells me that it is Okay to attempt the installation of my first windows program, but I still have a needling doubt as to whether all is Okay. Plus I expected to see a Wine icon in the Applications or System Menu. Am I on the right track? If not, where am I going wrong?

---

### Post by david_kt on 2007-03-30
Step 1 is ok. The rest of the step is unnecessary (I could not figure out what you are doing though there though, but I am sure it is not neccesary).

After step 1, what you need to do is just using wine. To use wine, try to right click on your exe file, and choose run with wine.

If you want gui, you could try this one:

[INDENT][http://tsx.nl/index.php?p=winexs](http://tsx.nl/index.php?p=winexs)

Download
You can download WineXS 1.1 here:
[http://tsx.nl/files/winexs-1.1.tgz](http://tsx.nl/files/winexs-1.1.tgz)


Installation
Installation is easy:
extract the file (tar xvf wine-1.1.tgz) and run it from the directory where you extracted it and type ./winexs to run WineXS. [/INDENT]

DK

---

### Post by zvacet on 2007-03-31
```
winecfg
```

This command will configure wine and after that you can use it.If you don´t want do it that way in attachment are winetools and you can configure wine with them if you want.To work with wine 
```
winefile
```

---

### Post by labinnsw on 2007-03-31
Thanks again Guys

I thought that if Wine is properly installed, I should have an Icon in either the applications or the System menu. That is what the other steps were about. I was looking for the wine Icon. But I now realize that the way to tell if Wine is properly installed is to try using a windows application. 

Not sure if you are familiar with Mailbox Dispatcher (This was already installed in a Windows partition). I tested it and it works. It took some time to open, so if anyone uses this post to solve the same problem just remember, a touch of patience will help.

---

