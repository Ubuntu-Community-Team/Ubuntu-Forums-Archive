---
title: "Linux Nuts and Bolts"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by SonWon on 2006-11-16
I am looking for a document that would give me the step by step process of what happens when Linux boots, all the way to the desktop.  I have some ideas but I am interested in learning about the nuts and bolts of Linux.  I am looking for a detailed process flow.  Like this,

1. grub loads.
2. grub loads Linux kernel.
3. etc..

I know my example is short.

Can some point me to a link?

Thank you,
SonWon

---

### Post by fritz_monroe on 2006-11-16
Have you looked at [rute]("http://rute.2038bug.com/index.html.gz")?  Covers just about everything, I would think it will have what you are looking for.

---

### Post by SonWon on 2006-11-16
Thank you for the reply.  I just read the first few pages and it appears to be what I am looking for.

Now if I could only remember it all in a week.  :-? 

SonWon

---

### Post by SonWon on 2006-11-16
I notice that the text says, "...never use the space or tab character in a file name..."  I have all sorts of files with spaces in the names that I carried over from Windows.  They work okay, why?  Or is this covered later in the text?

SonWon

---

### Post by whatintheworldisthat on 2006-11-16
Becuase when using filenames in the command line you have to insert and escape character before every space. The escape character is the backwards slash "\".

---

### Post by Shuja on 2006-11-16
If you want to get a great understanding of linux look at [linux from scratch]("http://www.linuxfromscratch.org/") you can use ubuntu to build it but by doing so you'll gain a lot of understanding how the system works at it's base levels

---

### Post by bodhi.zazen on 2006-11-16
Start here: [Speed Ubuntu boot](http://ubuntuforums.org/showthread.php?t=89491)

And then: [How Linux Boots](http://www.linux.com/article.pl?sid=04/06/23/1734235)

---

### Post by SonWon on 2006-11-17
Thank you for the replies.

I probably have enough to keep me busy through the winter months but how about gnome and KDE?

Thanks,
SonWon

---

### Post by bodhi.zazen on 2006-11-17
[KDE](http://docs.kde.org/userguide/kde-startup-sequence.html)
start kde is in /usr/bin/startkde and is a plain text file.

[Gnome](http://library.n0i.net/linux-unix/applications/x/gnome/faq/x503.html)

/usr/bin/gnome-session

[X](http://www.die.net/doc/linux/man/man1/startx.1.html)

See also usr/bin/startx

From there follow your google....

---

### Post by SonWon on 2006-11-17
Thank you for the reply.

Now I have my winter reading planned.

SonWon

---

### Post by SonWon on 2006-11-23
I just finished reading [How Linux boots]("http://www.linux.com/article.pl?sid=04/06/23/1734235") and found it very interesting and informative.  One question I have that was not covered is where should I place commands that are hardware specific?  Like,

> # set Left-scroll to act like Left-arrow

setkeycodes 5a 105

# set Right-scroll to act like Right-arrow

setkeycodes 59 106

# set Up-scroll to act like Up-arrow

setkeycodes 69 103

# set Down-scroll to act like Down-arrow

setkeycodes 68 108



These commands will enable the 4-way scroller on my laptop.  I would like these commands to be non-user specific but I am also interested in knowing where to place user specific commands?

Thank you for the help.
SonWon

---

