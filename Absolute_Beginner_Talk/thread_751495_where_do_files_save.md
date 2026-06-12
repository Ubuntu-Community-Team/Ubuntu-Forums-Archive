---
title: "where do files save?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by mstrchfmjolnirty on 2008-04-10
Alright so Im really new to linux and I'm really used to XP where all you do is go to my compute>C:/ and there's everything, but in Linux I just installed Utorrent with Wine and when I go to dl a torrent it tells me that the default program is bittorrent so I try to browse to find utorrent, soon after I began the browsing I discovered that I have no idea where to look...so basically what is the Linux equivalent of program files?

---

### Post by smartboyathome on 2008-04-10
Go to /usr/bin and look for utorrent. Also, right click applications and select edit menus, click wine on the left side, and then click programs from the dropdown on that same side. Double click the utorrent launcher to get the command used, which is what file you are looking for. It could also be located in /usr/sbin.

---

### Post by stchman on 2008-04-10
> **mstrchfmjolnirty said:**
> Alright so Im really new to linux and I'm really used to XP where all you do is go to my compute>C:/ and there's everything, but in Linux I just installed Utorrent with Wine and when I go to dl a torrent it tells me that the default program is bittorrent so I try to browse to find utorrent, soon after I began the browsing I discovered that I have no idea where to look...so basically what is the Linux equivalent of program files?

WINE will put the program in your /home folder in the .wine folder.

The uTorrent will not save files in a folder in which you do not have write permission.  Most likely in your home folder.

---

### Post by Steveway on 2008-04-10
You should NOT use uTorrent on Ubuntu.
Will it may work with almost no problems, it is not advisable to use if there are better native applications.
If you like uTorrent then you should use Deluge or Ktorrent if you use KDE.
That'll give you less problems.

---

### Post by Saint Angeles on 2008-04-10
i use gnome and i still like ktorrent the best for some reason.

i might not have given deluge a fair shot.

what i do is i save all my downloaded files onto my desktop. when they are done i can rename them and put them in the correct spot (pictures, videos, music, etc...)

i think of my desktop as a temporary place for files that havent been sorted yet.

---

### Post by bodhi.zazen on 2008-04-10
Open a terminal and enter :

```
echo $PATH
```

That will list the common locations of user executables.

sbin = system executables and are on root's path :

```
sudo -i

echo $PATH
```

For an overview of the Linux file system :

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

To find a program you can use which or locate (and other commands)

```
which bittorrent

locate bittorrent
```

utorrent is different, it is in ~/.wine/c_drive/Progam\ Files[/code]

Or wherever you saved it (utorent is distributed as an exe, so if it is on the desktop :

```
wine ~/Desktop/utorrent.exe
```

---

### Post by krinderlin on 2008-04-10
In a more generic sense that may help you in the future, here's some tips to finding programs:

[LIST]
[*]There are several "bin" (short for binary, which generally means executable in a Linux environment, though not always) directories floating about on your file system.  Most programs you run will be located in /usr/bin because these are user programs.
[*]Several of the commands you use from the terminal prompt are in fact programs themselves.  These programs are generally located in /bin or /usr/bin.
[*]Any sort of program that asks for your password when you launch it or you use sudo for when you type it into a terminal will usually be located in /sbin, /usr/sbin/ If you know the command you use to open a program, but need to find the full path for say making a launcher or the like, you can open a terminal and type:
```
which *command_name*
```
[/LIST]

Also, if you pull up Synaptic, and pull up the properties for a particular package, you can get a listing of all the files it installs.  Look for files installed in /usr/bin or /bin for the appropriate file.

---

### Post by mstrchfmjolnirty on 2008-04-10
Alright, I think I might try out ktorrent but what is KDE? or how do i know if i have it or not?

---

### Post by tango_ninja on 2008-04-10
I would recommend **deluge** over all other linux torrent apps. It's great....

PS if you're new to linux, check out this article on KDE vs Gnome. ([http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)). You're using Gnome by default if you installed Ubuntu. They're basically different ways to view your desktop environment.

---

### Post by mstrchfmjolnirty on 2008-04-10
Alright nvm i got it and i like it so far lol, but now how do i fully get rid of utorrent i open applications>wine>uninstall wine software...and theres no software in the list it says to choose from...utorrent is also listed directly under the wine subfolder and not under the wine programs subfolder....what should i do here?

---

### Post by mstrchfmjolnirty on 2008-04-10
alright ive now installed both and will use until i decide which i like best lol, but how to uninstall utorrent?

---

### Post by The Cog on 2008-04-10
Wine maintains a dummy drive C where it installs all its stuff. This dummy drive C is in your home folder, in a directory called **.wine**. This directory has a name that starts with a dot, so it is normally hidden. You can see the hidden files and folders by pressing Ctrl-H while in nautilus (the file explorer). 

If you don't have anything else installed in wine, you might as well just delete teh .wine directory. It will get recreated next time you run wine.

---

### Post by mstrchfmjolnirty on 2008-04-10
alright so I found the .wine directory and wanted to check it out before just deleting it....the only thing in the emulated C drive was internte explorer and a folder named common which had nothing in it.....im not sure but i saw nothing about utorrent in there, if i just delete the entire dirctory will that get rid of it still?

---

### Post by mstrchfmjolnirty on 2008-04-10
haha nvm im retarded...but a new problem arose as i was typing this....im currently installing limewire and its frozen installing on sunjava 6...does this normally take a while or should i restart the installation?

---

