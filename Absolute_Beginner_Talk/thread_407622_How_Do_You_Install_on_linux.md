---
title: "How Do You Install on linux?"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-12
h've been wanting to get stuff installed on my machine, but when i download programs, the do go into a install when. What do i do?

---

### Post by KitChy on 2007-04-12
If you download .deb files then it's just a case of open it with package manager but most things can easily be installed using the "apt-get" function.

---

### Post by Nythain on 2007-04-12
if you download a source tar extract it, and look for an install or readme... they usually have instructions, most commonly consisting of ./configure, make, make install though im running across more and more that have install scripts you just run and whatnot

---

### Post by aysiu on 2007-04-12
You don't download stuff manually. The package manager takes care of it for you.

**Brief conceptual overview for understanding**
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step-by-step tutorial with screenshots**
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by JayDeePlus on 2007-04-12
So, Can I download something and jump start into install?

---

### Post by zvacet on 2007-04-12
If you download deb package from some site just right click on it and you will see Gdebi.Click on it.

---

### Post by aysiu on 2007-04-12
> **JayDeePlus said:**
> So, Can I download something and jump start into install? Well, as I said before, you shouldn't have to manually download anything. Use the package manager for installing things. If you don't know what a package manager is, read the links I posted earlier.

> **zvacet said:**
> If you download deb package from some site just right click on it and you will see Gdebi.Click on it. Actually, you should be able to just double-click the .deb file. I believe GDebi is the default program for .deb files.

---

### Post by jfinkels on 2007-04-12
> **JayDeePlus said:**
> So, Can I download something and jump start into install?

Depends what you download! Tell us what you have and we can help you if you need it. First, though, read aysiu's links (he knows good stuff :D).

---

### Post by JayDeePlus on 2007-04-12
> **jfinkels said:**
> Depends what you download! Tell us what you have and we can help you if you need it. First, though, read aysiu's links (he knows good stuff :D).

right.......what if i wanted to download a program from Bittorent. like it don't show up in  package manager

---

### Post by aysiu on 2007-04-12
> **JayDeePlus said:**
> right.......what if i wanted to download a program from Bittorent. like it don't show up in  package manager
Can you give us the name of one program as an example? If we know the name of the program, we could probably tell you the best method to install it.

---

### Post by JayDeePlus on 2007-04-12
well i downloaded this programmed call DJ Traktor, it's a MP3 mixer, and i don't understand how to install it.

---

### Post by aysiu on 2007-04-12
> **JayDeePlus said:**
> well i downloaded this programmed call DJ Traktor, it's a MP3 mixer, and i don't understand how to install it.
[Isn't that a Mac OS X program?](http://www.apple.com/downloads/macosx/audio/traktordjstudio.html)

I think you should try finding a native Linux MP3 mixing program. Try searching Synaptic or Adept. If you have no idea what that last sentence means, read the links I posted earlier.

---

### Post by JayDeePlus on 2007-04-12
naw thats not a mac app, it's a DJ studio product, they also make fruity loops and some other stuff. so i mean i had it on Windows, how do i install it on this?

---

### Post by igknighted on 2007-04-12
Most windows apps don't run on Linux at all.  You can try setting up and using a compatability layer like Wine, but no promises.  Your best bet is to look for a linux native alternative program.

---

### Post by aysiu on 2007-04-12
[This thread](http://ubuntuforums.org/showthread.php?t=182848) might help you out.

---

### Post by Denis on 2007-04-12
If you want to know more about how to install software in Ubuntu Linux, you may want to read this: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

The first place to look for software should be Synaptic or the Add/remove program in the Applications menu. With these tools you can download and install software very easily. 

If you want to install software you find on a **website**: 
[LIST]
[*]Check if the software has a Linux version
[*]Look for a package for Ubuntu (preferably your version)
[*]If there is no Ubuntu package, look for a package for debian (.deb)
[/LIST]

(If you find no .deb install file, you'll have to do more research as to how to get the program)

In your case: try some DJ programs for Linux. Terminatorx and Mixxx are such programs. You can download and install these with the Add/remove tool in the menu or with Synaptic.

---

### Post by CJay554 on 2007-04-12
i think he's talking about .exe files... if thats the case you cant install them, unless you get a windows emulator like wine then it could work, otherwise you would use the package manager,
i would bet he moved from windows :P

---

### Post by aysiu on 2007-04-12
Read these threads. They tell you A) that DJ Traktor isn't going to happen, even in Wine and B) some good *native* Linux alternatives:
[http://ubuntuforums.org/showthread.php?t=402051&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=402051&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=367454&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=367454&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=311507&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=311507&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=307792&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=307792&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=295613&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=295613&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=249607&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=249607&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=214092&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=214092&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=185100&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=185100&highlight=dj+traktor)
[http://ubuntuforums.org/showthread.php?t=107331&highlight=dj+traktor](http://ubuntuforums.org/showthread.php?t=107331&highlight=dj+traktor)

---

### Post by CJay554 on 2007-04-12
ooooh its a CERTAIN program, thats my bad, i didnt see that part
yeah that wont work,
wine only supports so many things, mostly game interfaces, many programs have different programmings and kernel settings that wine would not support, at least not yet, people tend to keep making their own "brand" of programming that its hard to keep track of processes to run them :/

---

