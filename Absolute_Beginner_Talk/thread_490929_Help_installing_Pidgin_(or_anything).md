---
title: "Help installing Pidgin (or anything)"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Yonderknight on 2007-07-03
Hi everyone!

I'm getting started with ubuntu, and to tell you the truth I'm not liking gaim very much =(. I'm trying to install pidgin in hopes of getting a better IM client and for the sake of learning how to compile/install software from source (yes I know I can use the package manager).

Following some guide, I downloaded the pidgin source files, and extracted them into a folder in my home folder. I then ran some configure command, then make, then make install.

When I tried running pidgin, it worked, but none of the pictures or icons are displayed (they all show up as a page with a red x on it)!

I'm pretty sure it's because I was supposed to copy the files after (or before?) the install to some other directory other than my home directory, because I don't see any other program folders in there...

So, where do you put programs after you compile them? Is there a "program files" equivalent in linux? Also, what exactly does "make" and "make install" do? Does it just compile the binaries and put them in the same folder the source files were in, or does it also copy some files into some system directories (I'm guessing that's what an "install" is supposed to do?). Say I wanted to now remove pidgin, could I just delete the directory I unzipped everything to, or would I also have to remove some system files?

Thanks!

---

### Post by smo0th on 2007-07-03
don't trouble yourself too much..

for messenger i'm using amsn, whatever software you need to install, first go easy, click Applications>Add/Remove... or System>Administration>Synaptic Package Manager and search there for the software you want to install, just click it and apply to install it. No need to download sources and install them manually, (unless the software you are looking for is not in the list) ubuntu does al the magic for you.

programs normally install on your user root folder, for example /home/Yonderknight and they could be hidden, if you are browsing your home directory type ctrl+h to see hidden files and dirs.

---

### Post by dpar on 2007-07-03
Ummm, Pidgin really is Gaim. Just a new name.:biggrin:

---

### Post by meborc on 2007-07-03
new pidgin 2.0.2 version debian file (click-install) is available at [www.getdeb.net](www.getdeb.net) 

you should also read this - [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by sailor2001 on 2007-07-03
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

a short tutorial where you can put your files

---

### Post by MarilenCorciovei on 2007-07-03
I wrote a small tutorial with all the steps involved for feisty, you can find it here  [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/install-pidgin")

---

### Post by Yonderknight on 2007-07-04
Thanks everyone =).

> **smo0th said:**
> don't trouble yourself too much..

for messenger i'm using amsn, whatever software you need to install, first go easy, click Applications>Add/Remove... or System>Administration>Synaptic Package Manager and search there for the software you want to install, just click it and apply to install it. No need to download sources and install them manually, (unless the software you are looking for is not in the list) ubuntu does al the magic for you.

programs normally install on your user root folder, for example /home/Yonderknight and they could be hidden, if you are browsing your home directory type ctrl+h to see hidden files and dirs.

I mostly need an AIM client. Besides pidgin/gaim, I think the only one is the one released on the AIM website, but that seems a little "lite" for me, it doesn't even support some important features.

I couldn't find "pidgin" in the package manager, and I didn't know there was a debian package for it, so I tried installing it myself (which failed).

So I'd like to know how installing works so I can figure out how to remove it. Let's say I extracted the source files to the directory /home/Yonderknight/pidgin and ran the configure,make,make install stuff over there. Can I just delete this directory to remove it, then install the debian package? Or does running "make install" put files in other places, like the /etc/ folder or whatever.

BTW, the tutorial was very helpful, sailor!

Thanks everyone!

---

### Post by Axed on 2007-07-04
To uninstall an application that you installed from source, simply change to the directory that you installed it from and run: ```
sudo make uninstall
```

---

### Post by chele on 2007-07-04
> **Yonderknight said:**
> Hi everyone!

I'm getting started with ubuntu, and to tell you the truth I'm not liking gaim very much =(. I'm trying to install pidgin in hopes of getting a better IM client and for the sake of learning how to compile/install software from source (yes I know I can use the package manager).

Following some guide, I downloaded the pidgin source files, and extracted them into a folder in my home folder. I then ran some configure command, then make, then make install. Ubuntu is a Debian based system, as such you are better off compiling packages the debian way, rather then the generic linux way. Even further along that path, is using [prevu]("https://wiki.ubuntu.com/Prevu") to build and install application versions that are newer then the version of Ubuntu you are using.

What is you do not like about gaim? They have now changed the name to pidgin, but it functions mostly the same.

---

### Post by alienexplorers on 2007-07-04
I did not see a big difference between Pidgin and Gaim so I switched back to Gaim.

---

### Post by Yonderknight on 2007-07-04
Well, they are mostly a lot of little things that annoy me.

For one, I can't see my offline contacts. I'm kind of a control freak, so when I want to check if someone is online, sometimes I like to see them actually in the "offline" list to make sure that I'm not just skipping over their name in my buddy list or they have been accidentally deleted off my list somehow.

Also, I can't login to multiple screennames without having multiple buddies show up multiple times. In Trillian, it shows each buddy just once and lets you choose which SN you want to IM them with.

Also, there are no popup notifications (I don't know if this is available in pidgin though). And the amount of time the "sign on" or "sign off" icons are showing is really short, so by the time i have a time to switch over to my buddy list to see who has signed on/off, it's already too late.

---

### Post by kc5hwb on 2007-07-06
I've yet to find a Linux IM program that is as good as Trillian.  Most of them will connect and chat fine, but it is the littel features that Trillian has that I like.  Like notifications and what-not.  I wish that Trillian would run in WINE, but it won't.

---

### Post by absolutnoob on 2007-07-08
Does those DEB packages work for dapper?

---

