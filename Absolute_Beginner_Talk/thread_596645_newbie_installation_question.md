---
title: "newbie installation question"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-10-29
I just recently downloaded the adobe flast player ( .tar.gz file) from the website.  The instructions from it say to navigate to the folder ¨ install_flash_player_9_linux ¨ withing terminal and to enter ¨ ./flashplayer-installer ¨ to install.  My question is how do I change directories within terminal ( i.e. ´cd´ for windows, ? for ubuntu).


P.S.  - I also downloaded the realplayer10gold.bin to desktop but have no idea how to install it as well.

---

### Post by Inxsible on 2007-10-29
Directories can be changed in Linux using cd too


The steps to installing bin files are

```
sudo chmod +x *<file-name>*
sudo ./*<file-name>*
```So for your real player it will be
```
sudo chmod +x RealPlayer10Gold.bin
sudo ./RealPlayer10Gold.bin
```Make sure you use proper case in the file name

---

### Post by fiskking on 2007-10-29
thanks Inxsible.  I enter the first line and received this in the terminal:

 ¨chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory¨

The file for the Realplayer10GOLD.bin is on my desktop if that helps any.

---

### Post by stroyan on 2007-10-29
Learning shell commands can certainly pay off in the long run.  But, you can install adobe flash
with an ubuntu helper package.  The flashplugin-nonfree package puts adobe flash player on your system.
[https://help.ubuntu.com/community/MultimediaApplications#head-8da6bb74fc999112e0c2ec15e70c1cb4a1187107](https://help.ubuntu.com/community/MultimediaApplications#head-8da6bb74fc999112e0c2ec15e70c1cb4a1187107)

---

### Post by fiskking on 2007-10-29
yes ,you are definitely right.  thanks for the link.  I need to search the forums for using commands.  Thanks for everything guys.  :popcorn:

---

### Post by Inxsible on 2007-10-29
> **fiskking said:**
> thanks Inxsible.  I enter the first line and received this in the terminal:

 ¨chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory¨

The file for the Realplayer10GOLD.bin is on my desktop if that helps any.
Like i said in my earlier post. Make sure the case is appropriate. Linux is case sensitive. RealPlayer is very different from Realplayer as far as Linux is concerned.

---

### Post by fiskking on 2007-10-31
your right which is the problem that I am having.  The file name is entered correctly ,with the correct case, but still recieve this message within terminal:

 chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

:confused:

---

### Post by Maestro23 on 2007-10-31
> **fiskking said:**
> your right which is the problem that I am having.  The file name is entered correctly ,with the correct case, but still recieve this message within terminal:

 chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

:confused:

Are you in your Desktop directory when trying th chmod command?

> cd ~/Desktop

then 

ls (lists contents of directory, should see the .bin file)

then try your commands.

---

