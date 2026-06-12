---
title: "64 bit or 32 bit?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by neal.s on 2008-02-13
Which should I install? What are the benefits?

---

### Post by oldb0y on 2008-02-13
Do you have a 64-bit cpu?
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by jan quark on 2008-02-13
I ask  precautiously : your system supports 64 bit?

the benefits are improved speed when doing complicated and complex operations, like 3d editing or rendering stuff

see also

[http://www.pcworld.com/article/id,111508-page,1/article.html](http://www.pcworld.com/article/id,111508-page,1/article.html) 

note that not every driver is supported now in 64 bit

---

### Post by chewit on 2008-02-13
First of all you NEED a 64bit cpu. Usually, 64bit its meant to be faster and be better for new faster hardware. Because 64bit can handle more than 2GB RAM, 32bit can't.

However, not all applications and utilties work with 64bit, or it can be hard to get working.

---

### Post by earobinson on 2008-02-13
If you do have a 64 bit cpu I recomend the 64bit version

---

### Post by neal.s on 2008-02-13
I do have a 64 bit processor. I just wasn't sure about compatibility. It's an AMD Turion dual core.

I'll be going with 64 bit then.

---

### Post by frankos44 on 2008-02-13
Be careful, Not all the app's are available for 64bit

The difference in speed is not huge for most people with normal use.

Processing is quicker but the bottle neck is always loading files from your hard-disk.

Sitting in front of a word processor, checking emails and browsing the web and you wont find much difference in speed.

Boot speed isnt much different either.

---

### Post by Sinkingships7 on 2008-02-13
keep in mind that if you're going to be performing trivial every-day tasks such as listening to music, text editing, managing pictures, and surfing the web, the a 64 bit system is more than you need. i.e. it won't speed up those processes.

if you're planning on doing some hardcore photo editing or modeling, or using other intensive applications that take up tons of system resources, then 64 bit is the way to go. 

i'm basically saying that unless you have the need for it, you'll get more problems than it's worth, because the trivial things aren't always as easy. i have a 64 bit cpu and i'm still using a 32 bit os.

just my two cents. :)


EDIT: i posted this before i saw the post above me, sorry! but our points remain valid.

---

### Post by neal.s on 2008-02-13
Any apps specifically that don't work in 64 bit?

---

### Post by mahuyar on 2008-02-13
This excellent [thread]("http://ubuntuforums.org/showthread.php?t=368607") on 64-bit should get you started.  It talks about disadvantages and advantages of using the 64-bit version and also mentions about programs that wouldn't work under 64-bit, at least without a bit of tweaking.

---

### Post by igknighted on 2008-02-13
> **neal.s said:**
> Any apps specifically that don't work in 64 bit?

Flash and Java don't have browser plugins that are 64bit, but there are ways to make it work anyways, and they are fairly easy.  There are also programs/drivers that don't have 32 bit versions either (creative x-fi sound cards, for example), so don't assume that 32bit=easy and 64bit=hard, there is give and take.

---

### Post by Trebaruna on 2008-02-13
64 bit is too much? Like the infamous --and bogus-- quotation about 640K?
The fact of the matter is that slowly the computing world will shift to 64 bit, like it has to 32 bits, when also nobody thought we'd need to.

Saying it's too much implies it's like buying a top of the range computer to read emails, when in fact it's just a different CPU architecture. I've been running 64bit Gutsy since its release and only had a problem with Skype (my fiancee uses it, I don't), but I must add that I do not need DVD playback or media things on this machine other than flac, ogg and mp3. I have yet to come across a real problem with the distro, and it doesn't feel at all like I'm using immature technology or anything.

If you have the time and inclination check out 64 bit and you'll most likely be fine. If you really need to play it safe (you've some ancient version of Foo sitting around that you desperately need) stick with 32 bit. Ubuntu's repositories are well stocked with 64 bit versions of their packages, you won't be starved for functionality.

---

### Post by frankos44 on 2008-02-15
> **neal.s said:**
> Any apps specifically that don't work in 64 bit?

In my case, after installing LAMP on my desktop:

1. PHP5 generates blank pages but the php cli works OK. If anybody has an answer to this on I would be grateful.

2. Navicat wont run (probable a wine problem) yet I purchased a Linux version when in actual fact it has been tweaked to work with wine.. I think that is a con myself as there was no mention of wine on the website when making the decision to purchase it.  However, it is an excellent product all the same.

---

### Post by frankos44 on 2008-02-16
> **frankos44 said:**
> In my case, after installing LAMP on my desktop:

1. PHP5 generates blank pages but the php cli works OK. If anybody has an answer to this on I would be grateful.

2. Navicat wont run (probable a wine problem) yet I purchased a Linux version when in actual fact it has been tweaked to work with wine.. I think that is a con myself as there was no mention of wine on the website when making the decision to purchase it.  However, it is an excellent product all the same.

Here is how I got Ubuntu 64bit DESKTOP to run with LAMP

$ sudo apt-get install apache2
$ sudo apt-get install php5 libapache2-mod-php5
$ sudo /etc/init.d/apache2 restart
$ sudo apt-get install mysql-server
$ gksudo gedit /etc/mysql/my.cnf
	Comment out bind-address = 127.0.0.1
$ sudo /etc/init.d/mysql restart
$ sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin
$ gksudo gedit /etc/php5/apache2/php.ini
	Uncomment the extension=mysql.so
$ sudo /etc/init.d/apache2 restart

---

