---
title: "root?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2006-12-28
how do i login as root??? i was told to install flash player i just have to cut and paste the files into the plugin folder and im good but i need to login as root

---

### Post by 23meg on 2006-12-28
You don't. Use sudo.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

To start the Nautilus file manager as root, do this:```
gksudo nautilus
```

---

### Post by antgul3382 on 2006-12-28
ok i tried to install it with the terminal and it said my architechture (x86_64) is not supported

---

### Post by antgul3382 on 2006-12-28
Quote:
Installation Instructions

1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


and this is what came up

slave@slave3:/tmp/flash7$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
Macromedia Flash Player installer.

does this mean there is no flash player for 64 bit???? im a myspace user and without flash its useless.....

can anyone help????

---

### Post by Verlaine on 2006-12-28
Using ```
sudo -s 
```will let you "login" as root, you don't have to type sudo before every root command.

---

### Post by antgul3382 on 2006-12-28
got that i did everything it dont work to cut and paste em   and the terminal install says it dont work with my arcitechure (64 bit) this is ridiculous

---

### Post by Sef on 2006-12-28
> got that i did everything it dont work to cut and paste em and the terminal install says it dont work with my arcitechure (64 bit) this is ridiculous

It doesn't yet.   There are some work arounds for it though.  If I find a link to one will post it.

---

### Post by Verlaine on 2006-12-28
Did a quick google and found this. [http://blogs.adobe.com/penguin.swf/]("http://blogs.adobe.com/penguin.swf/")
The post about 64bit support is the last on the page apparently they haven't rolled out FP9 for Mac or WIndows 64bit yet never mind Linux!

---

