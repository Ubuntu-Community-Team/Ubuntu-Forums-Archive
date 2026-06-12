---
title: "Installing Applets"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by CorryJm on 2008-02-05
I just downloaded this [http://joh.deworks.net/blog/?page_id=58](http://joh.deworks.net/blog/?page_id=58) applet.

but now I can't seem to figure out for the life of me how to install it.

there is no automatic installation file included and I can't seem to quite understand the instructions on the site!

help please =)

thanks.

---

### Post by jordanmthomas on 2008-02-05
Ok, I will assume you have saved the tarball on your desktop.
1.  Open up a terminal (applications -- accessories -- terminal)
2.  Type
```
cd ~/Desktop
```
3.  Now install the stuff you'll need to compile the applet:
```
sudo apt-get install libglib2.0-dev libgtk2.0-dev libgnomevfs2-dev libgconf2-dev libglade2-dev libgstreamer0.10-dev libgnome2-dev libgnomeui-dev libpanel-applet2-dev libnotify-dev
```
4.  Now, we'll extract the tarball.
```
tar zxvf alarm-applet-0.1.tar.gz
```
5.  Now, we go into the directory we just extracted to:
```
cd alarm-applet-0.1
```
6.  Next up, we run the included configure script that more or less gets the program ready to be compiled.
```
./configure --prefix=/usr
```
7.  Now, time to compile and install:
```
make && sudo make install
```

You should be able to add it to your panel now by right-clicking your panel and going to add applet.  If you can't, log out and back in and try again.

I realize I just copied the instructions from the site, but hopefully you can understand what is going on now.  This is the basic process you go through any time you download the source code for a program, with the exception that generally you'll need to download different dependencies and the filenames will be different (of course).

---

### Post by erginemr on 2008-02-05
At the "make install" stage, you may alternatively use "sudo checkinstall" instead of "sudo make install". This will inject your installation into your package management system so that you can later uninstall it easily with "sudo aptitude remove <package_name>"

It will also create a Debian package in the same source directory, which you can back up and use later on for an easier installation of the same program.

Although installing from the source code will help you learn how Linux works better and so is recommended, it involves the installation of numerous development packages to your system. Since I already have those dev packages in mine, although I still recommend you to do it yourself for the sake of learning, I have created and attached a Debian package for you to install to your system with a single click. The package works for me well, so I hope, should work on your system too.

---

### Post by CorryJm on 2008-02-05
hey guys

first, thanks for the quick replies

jordanmthomas: I tried your method, but the terminal somewhat boldly tells me that my desktop does not exist.

corryjm@corryjm-desktop:~$ cd ~/desktop
bash: cd: /home/corryjm/desktop: No such file or directory


I find that hard to believe.

I think it may be due to another problem I have wherein my home folder is being shown as my desktop.

i've tried changing this in gconf-editor but can't seem to make anything work.

any ideas?

---

### Post by jordanmthomas on 2008-02-05
Desktop has a capital D.
If the file is in your home directory, don't cd to your desktop.  Only go in there if that's where your tarball resides.

---

### Post by CorryJm on 2008-02-06
> **jordanmthomas said:**
> Desktop has a capital D.
If the file is in your home directory, don't cd to your desktop.  Only go in there if that's where your tarball resides.

Desktop with a capital D procured the same results.

to cd to my home folder would I type 

cd ~/home/corryjm

in the terminal?

also: I'm a newb to Linux, could you define Tarball for me?

also also: what does cd stand for here?

---

### Post by jordanmthomas on 2008-02-06
OK, let's try to get this all straight here:
cd stands for "change directory"
~ <-- that symbol stands for "my home directory"
So, ~/home/corryjm would most likely be /home/corryjm/home/corryjm

So, if you were to type 
```
cd ~/home/corryjm
```
chances are you'd get an error


However, typing 
```
cd ~
```
would take you to your home directory and is the same as typing
```
cd /home/corryjm
```

Also, the quickest way to get to your home directory is to just type:
```
cd
``` and you'll go back to your home directory.


A tarball is a way of grouping many files together into one file.  While it's technically not an accurate comparison, it's akin to a zip file.  You can extract them (which is what the tar command in the instructions is doing) to get all the files out.

---

### Post by jordanmthomas on 2008-02-06
So, is your file you've downloaded from the website on your desktop (which you say is actually your home directory)?

Type this in a terminal:
```
cd
ls | grep alarm

```

So we can see if the file is indeed in your home directory.

---

### Post by erginemr on 2008-02-06
> **CorryJm said:**
> Desktop with a capital D procured the same results.

to cd to my home folder would I type 

cd ~/home/corryjm

in the terminal?

also: I'm a newb to Linux, could you define Tarball for me?

also also: what does cd stand for here?

I appreciate **jordanmthomas**' efforts to help you, but following the latest posts, and given the fact that you are not experienced at all at the CLI (terminal), I believe it will be very difficult to hold your hand through the entire source installation this way. I believe the best way for you is to install via the Debian package I have provided before, and attempt a source installation later on when you get more familiar with your shiny new Linux system.

If you would like, you can also read the following tutorial pages to learn more on installing both from source and from binary packages:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by CorryJm on 2008-02-06
thanks to both of you again!

I'm on my way to maybe moving out of these beginner forums.

I'll try to get this going when I get home again later :)

---

### Post by CorryJm on 2008-02-06
Ok, i'm pretty sure installation went smoothly.

but uh... where did it go?

there is no start up icon in the applications menu or otherwise.

uh, eh?

---

### Post by jordanmthomas on 2008-02-06
It's an applet for your panel, right?
If so, right click on a panel and go to Add Applet (or something similarly labeled, I don't use Gnome)
It should be in there.

---

### Post by CorryJm on 2008-02-06
> **jordanmthomas said:**
> It's an applet for your panel, right?
If so, right click on a panel and go to Add Applet (or something similarly labeled, I don't use Gnome)
It should be in there.

oh wow!

look at that, a whole menu I had no idea existed.

thanks a bunch Jordan and erginemr

people like you make these forums great.

---

### Post by nikoPSK on 2008-02-06
I just did a sudo apt-get for the timer-applet...

---

### Post by jordanmthomas on 2008-02-06
> **nikoPSK said:**
> I just did a sudo apt-get for the timer-applet...
:)
Who knew it'd be in there?

---

### Post by nikoPSK on 2008-02-06
> **jordanmthomas said:**
> :)
Who knew it'd be in there?

lol, I read about it in a guide, so easy route for me. :p

---

