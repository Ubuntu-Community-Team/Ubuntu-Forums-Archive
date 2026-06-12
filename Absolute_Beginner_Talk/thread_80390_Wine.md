---
title: "Wine"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2005-10-22
After installing Wine using Automatix, tried starting by typing wine in terminal, got this,

ching@ubuntu:~$ wineserver: could not save registry branch to /home/ching/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/ching/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/ching/.wine/user.reg : Permission denied

Wat's wrong?  How to overcome?

---

### Post by Jenda on 2005-10-22
You do not have the root permissions. To solve temporarily, add "sudo " before the command you issued. To solve permanently, open your filebrowser, if it is Nautilus in Gnome, press Ctrl+H to reveal hidden files and check to see if ./.wine o any subfolders and files have a lock emblem on them. If any do, do ```
sudo nautilus
``` and go to your home folder (yours, not root's) and after pressing Ctrl+H, right click any folder or file in and including ./.wine and in the permissions tab, select yourself as the owner. Note: Except for the ./drive_c/windows subdirectory. That should be root.)

---

### Post by Svictor on 2005-10-22
I'm not an expert, but I just installed wine from the ubuntu repos (not from winehq) and everything went fine so I wonder why your install should cause you troubles ? Have you ran winecfg right after installing wine ? If you haven't try it, because it configures automatically your ~/.wine folder (or allows you to change the existing config). Note that there are some files in this foler (specially in the /drive_c/windows subfolder) that are supposed to belong to root. Your user should only have read access to them.

---

### Post by Jenda on 2005-10-22
[QUOTE=Svictor]I'm not an expert, but I just installed wine from the ubuntu repos (not from winehq) and everything went fine so I wonder why your install should cause you troubles ? Have you ran winecfg right after installing wine ? If you haven't try it, because it configures automatically your ~/.wine folder (or allows you to change the existing config). Note that there are some files in this foler (specially in the /drive_c/windows subfolder) that are supposed to belong to root. Your user should only have read access to them.[/QUOTE]
I see. Sorry for my desinformation.(Edited)

---

### Post by webbie180 on 2005-10-23
Er, I've unlock everything and change owner to user, so how do I reverse it?  Don't know which one belongs to root or user.

---

### Post by Svictor on 2005-10-23
If you haven't installed any windows software yet (or if they are not too difficult to reinstall), the easiest way would be to simply erase the ~/.wine folder (move it to trash for safety) and run winecfg. It should recreate a fresh ~/.wine folder with the appropriate settings.

---

### Post by Master Shake on 2005-10-23
As long as we're talking WINE, how the heck do I get it to run a program?  Is there a good tutorial somewhere?

---

### Post by Jenda on 2005-10-23
Just type: ```
wine nameofprogram
```
But before you do that, you will have to cd to the location of the prog, I think.

Another way is to install xwine - a graphical frontend.
```
sudo apt-get install xwine
```

---

### Post by Svictor on 2005-10-23
Another thing to know is that you have much greater chances of succesfully running the program if you install it through wine, than if it is already installed on some windows partition. This is because wine uses its own registry. Sorry if it seems obvious to you, but it was not to me, until recently ;) ...

---

### Post by Jenda on 2005-10-23
Not obvious at all: thanks. Good to know, except I don't see myself installing windows any time soon. Why expose myself to the pain?

---

### Post by Svictor on 2005-10-24
Sorry, I didn't mean you had to install windows itself. Anyway, you probably couldn't do it through wine (if you ever want to go through that pain, try qemu). What I meant was that the software you wanted to run through wine had to be installed through wine.
For example, I need wine to run Macromedia's Flash MX. I still have my old windows partition and I first tried to run the "flash.exe" that was on it. This wouldn't work. But by reinstalling the software through wine (running its "setup.exe" through wine and leaving every setting to its defaults) I got it to work with no trouble at all. Hope this makes it clearer.
You don't need MSwindows at all to run programs through wine.

---

### Post by chrisblack on 2005-10-24
As I've no internet conection for ubuntu (yet)... I was wondering which file/files to download and install for xwine from [http://mirrors.xmission.com/ubuntu/pool/universe/x/xwine/](http://mirrors.xmission.com/ubuntu/pool/universe/x/xwine/)

Thanks

Chris

---

### Post by Svictor on 2005-10-24
It depends on the architecture you are running. You definetly want a *.deb file. Choose *i386.deb for a "standard" PC. The *amd64.deb is for the amd64 architecture (weird isn't it ?), and the *powerpc.deb is for the powerPC one ... The *tar.gz file is the source code, but you don't want to compile that yourself, do you ?

In case you don't know what to do next with the *.deb file, in a shell :
```
cd *the-directory-of-your-deb-file*
sudo dpkg -i *name-of-your-deb-file*
```

This will install the package. Then, you run it with
```
xwine
```

---

### Post by Stormspace on 2005-11-09
How do I get wine to launch an app when I double click the exe file? Currently when I do this it loads the winecfg window.

---

### Post by Svictor on 2005-11-09
Right-click an exe file, choose "properties".
Go to tab "open with". There, if wine is listed, just choose it.
If not, click on "add". This will open a window listing several applications. If wine is listed there, choose it. If not, choose (at the bottom of this window) "use custom command" and simply type "wine" (no quotes).

---

### Post by Stormspace on 2005-11-09
[QUOTE=Svictor]Right-click an exe file, choose "properties".
Go to tab "open with". There, if wine is listed, just choose it.
If not, click on "add". This will open a window listing several applications. If wine is listed there, choose it. If not, choose (at the bottom of this window) "use custom command" and simply type "wine" (no quotes).[/QUOTE]

THX!

---

