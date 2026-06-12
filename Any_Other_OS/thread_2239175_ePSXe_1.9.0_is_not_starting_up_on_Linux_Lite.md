---
title: "ePSXe 1.9.0 is not starting up on Linux Lite"
date: 2014-08-12
forum: Any Other OS
---

### Post by cobradabest on 2014-08-12
I'm having a problem with running [ePSXe]("http://www.epsxe.com/download.php") on Linux Lite (which is a Xubuntu derivative/distro), and it isn't working at all, when I click on the executable, nothing happens. I've looked it up the problem online and this seems to be a common issue with Xubuntu. I haven't found a solution, however. I asked about this issue in a thread in the "Other OS/distros" forum, and they said to post a thread here.

So has anyone here got it working on Xubuntu? How can I get it working?

---

### Post by adec2 on 2014-08-12
try opening a terminal in the folder you have epsxe in and type ./epsxe (or whatever your epsxe is called) and post what the terminal produces in error messages.

As a hint for the future, its always good to try running problematic programs from the terminal as it will give you more specified errors that can be sorted to get your program running

---

### Post by cobradabest on 2014-08-13
I'm getting this error:

```
./epsxe: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
```

---

### Post by adec2 on 2014-08-13
If you are running 64bit OS try installing the 32bit lib

sudo apt-get install libgtk2.0-0:i386

if it doesnt run after installing the above package, you may also need :

sudo apt-get install libsdl-image1.2:i386

sudo apt-get install libsdl-ttf2.0-0:i386

---

### Post by cobradabest on 2014-08-14
Okay, it's starting up, though only through command line, and games are also starting up. However, When I attempt to edit the Video, Sound or Netplay options, I get the error: ```
plugins/libbz2.dll: invalid ELF header
``` on the command line and then it closes...

---

### Post by adec2 on 2014-08-14
Hmm, thats a new one. I would be tempted to install [COLOR=#545454][FONT=arial]**libbz2**[/FONT][/COLOR][COLOR=#545454][FONT=arial]-dev as i have just had a look around and i have it installed and epsxe runs fine. Clutching at straws here cobra :)
You could always edit the video config files manually in the cfg directory and epsxe itrself has a hidden cfg file (.epsxerc) in the same directory as the epsxe binary, you will have to press ctrl+h to unhide it[/FONT][/COLOR]

---

### Post by cobradabest on 2014-08-14
I've done that, but I'm afraid it didn't help...

---

### Post by adec2 on 2014-08-14
Then other than post your problem in the epsxe forums and if you get a fix write it here, then all i can say is edit your cfg files manually before running.

Edit I have found a possible solution from the epsxe website about dependencies

[http://ngemu.com/threads/epsxe-configuration-guide-ubuntu-linux.93374/](http://ngemu.com/threads/epsxe-configuration-guide-ubuntu-linux.93374/)

sudo su
apt-get install lib32ncurses5
apt-get install lib32z1
apt-get install libx11-6:i386
apt-get install ia32-libs-gtk

especially the lib32z1 library

---

### Post by coffeecat on 2014-08-14
*Thread moved to **Other Operating Systems and Projects**.*

And thread title amended. Linux Lite != Xubuntu. Linux Lite is a 3rd party unofficial derivative of Xubuntu.

---

### Post by cobradabest on 2014-08-14
> **adec2 said:**
> Then other than post your problem in the epsxe forums and if you get a fix write it here, then all i can say is edit your cfg files manually before running.

Edit I have found a possible solution from the epsxe website about dependencies

[http://ngemu.com/threads/epsxe-configuration-guide-ubuntu-linux.93374/](http://ngemu.com/threads/epsxe-configuration-guide-ubuntu-linux.93374/)

sudo su
apt-get install lib32ncurses5
apt-get install lib32z1
apt-get install libx11-6:i386
apt-get install ia32-libs-gtk

especially the lib32z1 library

That hasn't worked either. I'll ask around on the ePSXe forums, thanks for all of your help anyway.

By the way, when I said ePSXe only starts up on command line, will it turns out the launcher I made for the executable was what didn't work, none of the launchers I've made for programs I made work. Is there a way to get launchers working on an Xfce desktop? It's a lot harder than I first thought, it seems there's more to it then clicking "Create Launcher"...

EDIT: Oh wait! it turns out the problem with my ePSXe was that I was using windows plugins, I didn't think there was a difference! I downloaded and use Linux plugins, and it all works now, thanks so much for your help!

---

### Post by adec2 on 2014-08-14
You're very much welcome, dont forget to mark your thread as solved too

---

