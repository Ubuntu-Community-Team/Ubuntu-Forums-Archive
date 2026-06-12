---
title: "how to get rid of wine files"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ndrew2505 on 2007-07-07
how can i delete the wine files in the filesystem? when i try it tells me it cant be done. do i have to log in as root and if so how do i log in to delete files?

---

### Post by Anonii on 2007-07-07
You want to **uninstall** wine, or just delete your configurations, Program Files, etc.?

---

### Post by ndrew2505 on 2007-07-07
i had tried to install wine with the commands from the wine site but didnt get it right appearantly...anyway i used automatix to try to install it but still cant get it to work and i think it has something to do with the botched install..

---

### Post by Anonii on 2007-07-07
> **ndrew2505 said:**
> i had tried to install wine with the commands from the wine site but didnt get it right appearantly...anyway i used automatix to try to install it but still cant get it to work and i think it has something to do with the botched install..
Open a terminal, and execute this:
**wine --version**

Then paste the output here.

I suspect that Wine is alright but you don't know how to use it.

---

### Post by ndrew2505 on 2007-07-07
it said it wasnt installed and i did what it said and i still cant find wine..?i had it installed before and i found it in the system tools i think but i had to reinstall feisty and havent been able to get it right since...



drew@drew-laptop:~$ wine --version
The program 'wine' is currently not installed.  You can install it by typing:
sudo apt-get install wine
Make sure you have the 'universe' component enabled
bash: wine: command not found
drew@drew-laptop:~$ sudo apt-get install wine
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.3MB of archives.
After unpacking 46.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Selecting previously deselected package wine.
(Reading database ... 128311 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.40~winehq0~ubuntu~7.04-1_i386.deb) ...
Setting up wine (0.9.40~winehq0~ubuntu~7.04-1) ...

---

### Post by Anonii on 2007-07-07
Well you most probably just installed wine. Try this:
**wine --version** and you should get related output. If the output is correct (it gives you the version number, which is 0.9.40 for me) then you have a working Wine setup. 
You can **uninstall** it with this command: *sudo apt-get remove wine*

---

### Post by ndrew2505 on 2007-07-07
yeah i got the 9.4 but what happened to the "wine files" link in system tools? how do i run the app with wine or where do i save the file to

---

### Post by Anonii on 2007-07-07
> **ndrew2505 said:**
> yeah i got the 9.4 but what happened to the "wine files" link in system tools? how do i run the app with wine or where do i save the file to
I don't know what that Wine Files is, because I'm running Kubuntu and not Ubuntu. 

Also, Wine is a command-line application so you don't expect flashy interfaces, menus etc. (It's use is really easy, tho.).
Read this, it will help you: 
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by ndrew2505 on 2007-07-07
awesome help! thanks alot.

---

### Post by ndrew2505 on 2007-07-07
could you also help clear up step 3 of this...

To install Windows applications using Wine, follow these instructions:
1.Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
2.Place it in a convenient directory (e.g. the desktop, or home folder).
3.Open the terminal, and cd into the directory where the .EXE is located.
4.Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).

i keep getting no such file or directory.

---

### Post by forrestcupp on 2007-07-07
> **ndrew2505 said:**
> could you also help clear up step 3 of this...

To install Windows applications using Wine, follow these instructions:
1.Download the Windows application from any source (e.g. download.com). Download the .EXE (executable).
2.Place it in a convenient directory (e.g. the desktop, or home folder).
3.Open the terminal, and cd into the directory where the .EXE is located.
4.Type wine the-name-of-the-application.extension (e.g. wine realplayer.exe).

i keep getting no such file or directory.

The e.g. is wrong.  If you cd into the directory that has the installation file, for instance realplayer.exe, you should type:
```
wine ./realplayer.exe
```
If you type the "./" that tells it to look for realplayer.exe in the current directory.  Or instead of cd'ing into the correct directory you could type:
```
wine /home/username/realplayer.exe
```
or whatever directory the file is in.

edit:
If you want to configure wine, type:
```
wineconfig
```
and it will bring up a GUI to configure wine

---

### Post by ndrew2505 on 2007-07-07
could you help clear up what im doing wrong? the exe is on the desktop.

drew@drew-laptop:~$ wine ./desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$ wine ./iview.exe
wine: cannot find './iview.exe'
drew@drew-laptop:~$ wine /home/drew/iview.exe
wine: cannot find '/home/drew/iview.exe'
drew@drew-laptop:~$ wine /home/drew/desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$

---

### Post by Anonii on 2007-07-07
> **ndrew2505 said:**
> could you help clear up what im doing wrong? the exe is on the desktop.

drew@drew-laptop:~$ wine ./desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$ wine ./iview.exe
wine: cannot find './iview.exe'
drew@drew-laptop:~$ wine /home/drew/iview.exe
wine: cannot find '/home/drew/iview.exe'
drew@drew-laptop:~$ wine /home/drew/desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$
First of all, almost everything in Linux is case sensitive, which means that 'beacon' and 'BeAcOn' are completely **different** things. Also, the desktop directory is not 'desktop' but 'Desktop'.
Also, your home directory is not a dot (.) like in your examples, but this symbol: ~.
So the correct command would be:
**wine ~/Desktop/iview.exe**

---

### Post by ndrew2505 on 2007-07-07
sorry im still new to linux. thanks for your help but it gave me this message...

drew@drew-laptop:~$ wine ~/Desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\Desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\Desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$

---

### Post by Anonii on 2007-07-08
> **ndrew2505 said:**
> sorry im still new to linux. thanks for your help but it gave me this message...

drew@drew-laptop:~$ wine ~/Desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\Desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\Desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$
Is there a file named iview.exe in your desktop?
Try this in the terminal:
**ls ~/Desktop**

Sorry, for the slow responce, I was sleeping.

---

### Post by chuckyp on 2007-07-08
To answer one of your other questions....

To get wine back on your Aplications menu try pressing Alt+F2 to bring up a run dialog.  Then type in wineboot as the command.  Wine should then add itself back to your gnome menu.  It will also run any applications that are supposed to startup automatically with windows.

---

### Post by forrestcupp on 2007-07-08
> **ndrew2505 said:**
> sorry im still new to linux. thanks for your help but it gave me this message...

drew@drew-laptop:~$ wine ~/Desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\Desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\Desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$

Well, it could possibly be that it won't work.  Wine is great, but it won't run *every* Windows application.  And sometimes it will run an app, but it's a pain to get it to work (like downloading extra dll's and setting up the configuration specifically for a certain app to work).  

It looks like this needs a dll installed and configured for iview to work properly.  I don't know about iview, but maybe you could check [Frank's Corner](http://frankscorner.org/).  It's a website that takes you step by step through getting some tough-to-configure Windows apps to work.  It may not have what you're looking for, but maybe you can find some clues.

---

### Post by Anonii on 2007-07-08
> **ndrew2505 said:**
> sorry im still new to linux. thanks for your help but it gave me this message...

drew@drew-laptop:~$ wine ~/Desktop/iview.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\drew\\Desktop\\iview.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\drew\\Desktop\\iview.exe" failed, status c0000135
drew@drew-laptop:~$
Aw yeah, disregard my previous post. I misunderstood the output. From what I saw here: [http://appdb.winehq.org/appview.php?iVersionId=7834](http://appdb.winehq.org/appview.php?iVersionId=7834) your error is normal, and you will have to get that .dll by yourself (Try this site: [http://www.dll-files.com/](http://www.dll-files.com/) , just found it off google).
After that it should have no problems installing.

---

