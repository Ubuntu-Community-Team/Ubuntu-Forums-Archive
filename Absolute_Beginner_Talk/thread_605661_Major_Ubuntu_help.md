---
title: "Major Ubuntu help"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-07
Hello, I recently have installed Ubuntu 7.10(Gutsy Gibbon) on my laptop. To get internet on my laptop I have been using a 
Sierra Wireless AirCard 875, I also have learned that I need to install the drivers to get the card to work, the problem is I'm a little new with Ubuntu and I'm not sure how to do that, could someone please help me with this problem? Also is it guarrenteed this certain card is compatible with Ubuntu 7.10? 

A little off-topic, but how do I install Ubuntu Beryl on my 7.10?

Thanks for any help offered

---

### Post by RobotoWorks on 2007-11-07
Has anyone else encountered this problem?

---

### Post by Harpoon on 2007-11-07
Well, I don't have this card and I have not installed Gutsy.  For fun I did a quick Google on the name of your card + ubuntu and found a bunch.

You may find this useful:  [http://learnaboutlinux.net/sierra_wireless.htm](http://learnaboutlinux.net/sierra_wireless.htm) 
and here [www.engadget.com/2006/11/20/cingular-debuts-seirra-wireless-aircard-875/comments/2702582/](www.engadget.com/2006/11/20/cingular-debuts-seirra-wireless-aircard-875/comments/2702582/)

Hope one of those works for you

---

### Post by RobotoWorks on 2007-11-07
Thank you, but does anyone know how to install Unbuntu Beryl?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Has anyone else encountered this problem?

First, you need to got to the manufacturer's website and see if a linux driver is available.  If not, you will more than likely have to use ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

2nd. Beryl is no more. It has been replaced by Compiz-Fusion which is in Gutsy by default.  You will have to install the Compiz-Manager to configure all the plugins.

Compiz-Manager: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion).

Get your wifi card working 1st before you work on the pretty eye-candy.

---

### Post by RobotoWorks on 2007-11-07
Again Thanks, is Compliz Fusion another distro of Linux, or just an add on?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Again Thanks, is Compliz Fusion another distro of Linux, or just an add on?

Just and add-on.

Compiz-Fusion: [http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)

---

### Post by RobotoWorks on 2007-11-07
I got this from one of the websites you guys gave me, regarding my card:

Once you have that file, un-gzip/tar it and you will get some files.

    $ tar zxvf sierra.v.1.0.6.tar.gz
    sierra.v.1.0.6/Makefile
    sierra.v.1.0.6/sierra.c
    sierra.v.1.0.6/Module.symvers 

To install the driver, perform the following commands:

    $ cd sierra.v.1.0.6/
    $ make
    make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/joelinux/Do
    wnload/sierra.v.1.0.6 modules
    make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
       CC [M] /home/joelinux/Download/sierra.v.1.0.6/sierra.o
       Building modules, stage 2.
       MODPOST 1 modules
       CC /home/joelinux/Download/sierra.v.1.0.6/sierra.mod.o
       LD [M] /home/joelinux/Download/sierra.v.1.0.6/sierra.ko
    make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'

The make command will use the files in the sierra.v.1.0.6 directory to build 4 additional files, and place them into the directory for you. If you list the directory's contents, you will see the 4 extra files. Once make is finished doing what it's doing, now you can install the driver:

How exactly to I install the driver, Im a total noob and this doesnt make sence to me.

---

### Post by RobotoWorks on 2007-11-07
Does anyone know what that means?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> Does anyone know what that means?

Don't bump your posts after just a few minutes.  Just some friendly FYI.

You are tyring to compile the driver from source.  Read the following link to get you started:

Installing from Source: [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

Once you get going, just follow the direction that were provided for you on the card's site.  There may be additional info in a README/INSTALL document in the extracted folder as well.

---

### Post by P4man on 2007-11-07
Please don't bump your posts unnecessarily. if you want a good response, it may take longer than 10 minutes :???:. 

Anyway, yes it makes sense to me. You have to open a terminal. Go to applications, accessories, terminal. Don't be afraid, it won't bite, and you'll need it rather often ;)

I am assuming you downloaded that file to your home folder (/home/yourname). If you open a console, by default you will be in that directory. You can check by typing

> ls

to get all files there. "sierra.v.1.0.6.tar.gz" should be among them.

If so, you need to unpack that file. A tarball is a bit like a zipfile. To unpack it, follow the command you just quoted. type in the terminal:

> tar zxvf sierra.v.1.0.6.tar.gz

(hint: to copy/paste commands, copy them in your browser, then paste them using** shift**+control+V, or of course edit/paste)

Now a directory will be made named "sierra.v.1.0.6/". cd to it by typing:

> cd sierra.v.1.0.6

(another hint, you can use tab key to autocomplete file or folder names in the terminal. So you could type "cd sier", then press tab, then enter. Try it).

anyway, etc, etc. Just follow the commands you quoted. When you see something preceeded by a $ or # sign, then that means those are commands you should enter in the console. The rest is the output you should get.

Does that help?

---

### Post by RobotoWorks on 2007-11-07
What exactly do you mean by "home" folder?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> What exactly do you mean by "home" folder?

The home folder of the user (you).

> cd /home/username

That is the home folder for the user you created when you installed Ubuntu.  OR Did you download it to your Desktop?

> cd ~/Desktop

*Linux is **C**ase **S**ensitive.

---

### Post by RobotoWorks on 2007-11-07
I downloaded it to my desktop, is that okay?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> I downloaded it to my desktop, is that okay?

That's fine.  You need to navigate to that directory(commands I posted above), then run your tar command, etc...

---

### Post by P4man on 2007-11-07
Your homefolder is a bit like "my documents" in windows. It is located in 

```
/home/robotoworks/
``` (if that where your login name).

Your desktop folder is a subfolder of that home folder. in your case it would be:

```
/home/robotoworks/Desktop/
```

Note that the homefolder name is Dependant on your login name, a generic way to describe it it the tilde sign. So your desktop would also be located at:

```
~/Desktop 
```

Two more notes:
1) file and folder names in Linux are case sensitive. /home/Bob is NOT the same as /home/bob.
2) "cd" command is "change directory". Use it to change the active directory (/folder) in the terminal. Eg:

```
cd /home/yourname/Desktop
```

---

### Post by Maestro23 on 2007-11-07
> **P4man said:**
> Your homefolder is a bit like "my documents" in windows. It is located in 

```
/home/robotoworks/
``` (if that where your login name).

Your desktop folder is a subfolder of that home folder. in your case it would be:

```
/home/robotoworks/Desktop/
```

Note that the homefolder name is Dependant on your login name, a generic way to describe it it the tilde sign. So your desktop would also be located at:

```
~/Desktop 
```

Two more notes:
1) file and folder names in Linux are case sensitive. /home/Bob is NOT the same as /home/bob.
2) "cd" command is "change directory". Use it to change the active directory (/folder) in the terminal. Eg:

```
cd /home/yourname/Desktop
```

Excellent post my P4, just want to add a link that will help the OP in the long when getting help on the forums:

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

---

### Post by RobotoWorks on 2007-11-07
When I type cd ~/Desktop, it gives me ~/Desktop$ ~/Desktop
What would I type after ~/Desktop$ ~/Desktop?

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> When I type cd ~/Desktop, it gives me ~/Desktop$ ~/Desktop
What would I type after **~/Desktop$ **~/Desktop?

You are already in the Desktop directory then.  

Type **ls **(list contents of current directory, like P4 posted above.)

Should see your driver file.

---

### Post by P4man on 2007-11-07
Thanks for that link, I just learned something extremely useful from it. Call me a noob if you want (cause I am :) but I never knew this: you can select some piece of code in your  browser, dont even copy it, then in the terminal press middle mouse button and its copy/pasted. 

**Awesome!**

:guitar:

:popcorn:

:)

---

### Post by RobotoWorks on 2007-11-07
What do I do after that? Could someone gives me a detailed HOWTO? Thanks for all the help, much appreciated!

---

### Post by Maestro23 on 2007-11-07
> **RobotoWorks said:**
> What do I do after that? Could someone gives me a detailed HOWTO? Thanks for all the help, much appreciated!

I know you are new to Linux and the terminal, but P4's post could not have been more by the numbers. He broke everything down for you. Go back and look at his post.

*Installing from source is never easy for a person new to linux.  Just do happens that your driver was a tar file.

---

