---
title: "Package Module Assistant"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by shurguywutt on 2006-05-12
I am trying to install some drivers for my soundblaster card, and I use the following code 

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

then i get...

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant

It says this on the drivers webpage "note that you need to have enabled the Universe repository, because module-assistant is in Universe"

How do I enable the Universe repository?

Thanks

---

### Post by tonyr on 2006-05-12
Edit **/etc/apt/sources.list** (you need to be root to do this). 
 In there somewhere there should be lines that look
more or less like this:
```

deb http://archive.ubuntu.com/ubuntu/ breezy  universe
deb-src http://archive.ubuntu.com/ubuntu/ breezy universe

```

They may say **dapper** if you are using a Dapper release, and the archive
URL may be slightly different, might have **us** or **ca** or **eu** or something in it.

If they are there but commented ('#' as first character in the line),
uncomment them.  If they are not there, add them.  Then
in a terminal do
```

sudo apt-get update

```

or in Synaptic, select the **Reload** button.

---

### Post by shurguywutt on 2006-05-13
thanks a lot, with ubuntu users like you out there, we can surely take a bite out of microsoft, worked perfectly

---

