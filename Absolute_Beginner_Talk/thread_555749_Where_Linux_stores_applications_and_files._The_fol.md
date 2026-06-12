---
title: "Where Linux stores applications and files. The folder structure?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Proximo1 on 2007-09-20
I am new to Linux and I love it.  I went through some tutorials for new users on a sticky here and learned allot.  

Repositories
Terminal
CLI
Aptitude
sudo
gedit
sources.list

and some other things on how the system is different than Windows XP.

What I would like to know is where does Linux install it's applications vs. Windows.  I see the /etc/apt/ path allot, but is this the default installation location for applications?

What are all the other folders for?  I don't need to know them all, but maybe just some background on the system folders and what may be of interest to a new user that came from Windows XP.

I consider myself a very advanced Windows XP user and love what I see with Linux, but I am a novice and would like to dig a little deeper into the system folder structure.

Any feedback would be appreciated.

---

### Post by az on 2007-09-20
Linux is a Unix-type OS.  That means that if something was written for a Unix-type OS, it can be ported to linux.  That being said, linux uses the same kind of filesystem structure as Unix.

Executable programs go in /bin.  System executables go in /sbin.  Less important (or user-only) executables go in /usr/bin and /usr/sbin.

Shared libraries go in /lib

Non-user data does in /var (like logs or system program data.  Apt's cache in in /var/cache/apt)

/boot is where your files needed to boot go.  The linux kernel is able to use disk space beyond what your motherboard may be able to read - this means that you need to make sure that liux can load into memory (boot) before you need to use anything from a part of the disk that requires more that the bios.  For example, an old motherboard that can't recognize more that the first gig of hard disk space or a modern software raid array.

/home is your (and all the other users' on your computer) home

/root is the root user's home.

/etc is where all your system configurations go

... anyway, Ubuntu being a binary distro, you don't need to worry about any other part of the filesystem than home.  If anything requires that you need to play around there, it's a bug (or it's your choice.)

If you do want to muck around with the rest of the filesystem, you need to make sure you are not interfering with the package manager or any other system utility.

---

### Post by Maestro23 on 2007-09-20
[http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)

---

### Post by mikewhatever on 2007-09-20
More links on linux directory structure [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by Proximo1 on 2007-09-21
This is what I love about the Linux Community.  You guys are GREAT.

Thank you so much for the feedback.  It's EXACTLY what I was looking for.  I just like to understand the foundation my house sits on.  It makes me feel better.  I don't plan on touching anything in these folders, but just the fact that they are there and I did not know why, bothered me.

In Windows XP,  I am very advanced and can even hack into the Registry to tweak some things.  What I love about Ubuntu so far is the open architecture, the open source community and the awesome help you get from people like you.

Why I like Linux?  Because it's not Windows.  I have grown tired of Windows.  it's great and easy to use, but I want some excitement in my life.  I want an OS that is built and structured to work well and stable and not deal with as many crashes.  

Thanks again

---

