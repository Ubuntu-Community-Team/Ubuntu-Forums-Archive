---
title: "A little confused with linux file system"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by arcooke on 2007-06-23
I'm trying to install a skin for XMMS, and I'm having a little trouble doing what it's asking me to.  It says:

> If you want your skins to be available to all users put them in <prefix>/share/xmms/Skins and for user specific skins use ~/.xmms/Skins
Skins can be installed without unzipping them. To be able to use zipped skins you need unzip installed.

I'm not sure what <prefix> or "~" are supposed to represent.

I'm still trying to figure out my way around, so any tips you can offer would be appreciated. 

Thanks :D


- EDIT
I did manage to find the user folder in /home/me/.xmms but had to show hidden files and folders.  I'm still unsure what the all-user <prefix> is supposed to represent.  It's going to take a while to get used to this.

---

### Post by DBStevens on 2007-06-23
~/.xmms/Skins

is shorthand for what is normally /home/user/.xmms/Skins

wher user is a username.

The first reference is to a normal shared resource folder for your system. 

The prefix is probably /usr but it doesn't have to be.

Don't you just love flexible systems ;-)

---

### Post by kerry_s on 2007-06-23
press alt+f2 type>

nautilus ~/.xmms/Skins

now just drag and drop your skin there.

---

### Post by arcooke on 2007-06-23
> **DBStevens said:**
> Don't you just love flexible systems ;-)

Not yet, lol.  But the more I play with it the more I get used to it.  So far, so good.  Thanks for your answer.

@kerry_s
Thanks, I never knew about the run command.  I also wasn't aware nautilus was the Linux equivalent of windows explorer. Learn something new every 5 minutes. ;)

---

### Post by BobCFC on 2007-06-23
I think prefix is just their get-out clause in the docs meaning insert your directory here because it might be in different places depending on your distribution.  It's not a common unix term.

You were on the right track with the hidden folder... ~ is just shorthand for home.  Any folder or file with a dot infront of it's name is hidden so it doesn't clutter you home directory.  Usually used for config files.

---

### Post by caro on 2007-06-23
> **kerry_s said:**
> press alt+f2 type>

nautilus ~/.xmms/Skins

now just drag and drop your skin there.

Didn't know you could do that.  :eek:

---

