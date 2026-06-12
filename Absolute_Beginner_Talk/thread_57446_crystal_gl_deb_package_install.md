---
title: "crystal gl deb package install ??"
date: 2005-08-16
forum: Absolute Beginner Talk
---

### Post by Corona on 2005-08-16
I am trying to install crystal gl for kde from this page:

[http://kdelook.org/content/show.php?content=18983](http://kdelook.org/content/show.php?content=18983)

I downloaded the .deb file and then I opened a terminal, became root and entered the following command:

dpkg -i crystalgl_0.8.1-1_i386.deb

I think that worked as there were no errors.

Now I am lost, what do I do now to get this to work?

Thanks for any help.

---

### Post by TristanMike on 2005-08-16
I don't mean to sound like a tool, but did you follow the other instructions??
> 
-- INSTALL -------------------------
Basic Installation (from the console):
- Step 1
$ ./configure
OR: $ ./configure --prefix=`kde-config --prefix`
- Step 2
$ make
- Step 3 (as root)
# make install

If configure fails, check that you have both the Qt and KDE development headers installed. If you used a previous version before, you need to restart kde to use the upgraded version. 

---

### Post by Corona on 2005-08-16
Thanks for your reply,

As you can see I am an absolute beginner and I have no idea what I am doing here.

Could you please give me a step-by-step procedure starting with which files do I need to download and then the commands that I need to use to install them.

---

### Post by TristanMike on 2005-08-16
Sorry, I just thought you might have passed over them, I do it *all* the time and I am an absolute beginner to Linux too, but enjoying the ride. I'm not too sure as I'm trying Gnome first untill I get the hang of things. But, if you can't find it already in your themes menu all ready, I'd try running those commands from a terminal but change to the place you put the files are in.

Can someone else help?

---

