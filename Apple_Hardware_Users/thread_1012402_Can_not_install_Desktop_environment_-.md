---
title: "Can not install Desktop environment -"
date: 2008-12-15
forum: Apple Hardware Users
---

### Post by Thandien on 2008-12-15
I have downloaded Ubuntu 8.10 alternative for PPC (at [http://cdimage.ubuntu.com/ports/releases/intrepid/release/](http://cdimage.ubuntu.com/ports/releases/intrepid/release/) ), and I've run into some troubles during the installation process. Let me first state that I am a complete newcomer to the Linux world, but I am eager to learn.

I'm trying to install onto a G3 iMac, with 300MHz and 256 MB RAM. I loaded up the installation disk with no troubles, and got around a problem detecting my CD-ROM drive with a command found using Google (modprobe ide-scsi). No troubles until it attempts to install software, then it hangs at 6% and ultimately fails. 
From googling (and googling, and googling, and googling---), I found that I should be able to run Linux anyway, just without the additional software, such as the Desktop environment. Through that, I was supposed to be able to install the additional stuff using "apt-get install ubuntu-desktop". So, I did this, and was prompted for my CD. Inserting it and pressing enter, however, has no effect, and it will not continue. Is there any solution? Any command I can use in another shell (is that proper terminology?) to make my CD-ROM detect my CD? I tried "modprobe ide-scsi" from before (with sudo before it and everything, I think I'm learning a little), but it had no effect that I could see.
I feel that I'm so close to making this work! I'm sorry if the answer is out there somewhere &#8212; if it is, then I missed it.

Oh, and I did verify the disk image I used to burn the disk using md5sum, and it checked out perfect there. I tried burning it twice, both times at lowest speed to be sure, and always got the same error. I'm sure it isn't that (and I hope to, too, because I'm running out of burnable CDs!).

Thank you in advance, I hope I didn't make any mistakes such as posting in the wrong forum or forgetting to specify any details.

-

Edit: I forgot to mention that the computer is not connected to the internet. I could hook it up to the router like I used to, but I have no idea how to configure the system to connect. If I could do this, it would probable be a good solution to my problem, so help in this regard would be appreciated too.

---

### Post by eraker on 2008-12-15
I'm not sure about it hanging at 6%. It would be nice to have at least a base with a moderately complete shell before we start trying to patch everything together. We can troubleshoot things like networking with what you have, but with so few tools, we may have difficulty testing and figuring out everything that needs to be fixed.

I had enough problems with Ubuntu discs for ppc recently (also for a G3, but an iBook) that I decided to install debian instead (which is the distro that Ubuntu is based off of). I don't know if this is a kosher suggestion here, but for a new user at this point, it might be an easier way to go.

You can get the debian netinst (net-install) cd for ppc here: 
[http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/debian-40r5-powerpc-netinst.iso)

You'll burn it as an iso, like you did with the Ubuntu iso, and it should load and install without any problem. Plug the computer into the router before you turn it on, load the cd, and go for it. It will give you a less graphically-pretty installer to work with, but you as long as you have a working network connection, it should be able to install a full desktop system without much command-line fussing. Note: be sure to select "Desktop system" or something like that when prompted and it will give you a graphical front-end and a browser, as well as a few other common applications.

Ubuntu (and debian) for that matter, puts only the bare essentials on a cd. The idea is that once your system is up and running, you can download whatever software you'll want from *software repositories*, which are storehouses of everything you could want and more. To get to that point, any installer should build a kernel to interact with your hardware, should set up your network connection, and should even build a basic set of repositories from which it will be able to download and install all the software you want.

In other words, the command "sudo apt-get install *package*" won't do much until all of those other things have been done.

Hope that helps.

---

### Post by stream303 on 2008-12-16
> **Thandien said:**
> Let me first state that I am a complete newcomer to the Linux world, but I am eager to learn.

I hope you are eager, because with all that you've provided, you are in for a mountain of fun, depending on how you look at it. :)

As a newcomer to Linux, nothing could be more discouraging than to have to deal with ppc in the first place, let alone deal with possible desktop-environment issues as seen with recent releases of Xubuntu - which given your ram, is what I'd normally recommend until lately.  And, G3 iMacs have their own special problems that one has to be aware of like having a non-original hard disks larger than 8gb.  Is your disk larger than 8gb?

Keep this faq handy:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

Honestly, I think you'd have a much better time starting off with Ubuntu's parent, Debian Etch 4.0r5.  Until you get your networking figured out, you just want to put Linux on your G3 without a lot of hassle.  No problem.  It is much easier to configure, and you can rely on Ubuntu-provided solutions to help with any weird Debian quirks.

During installation, you can just say NO to using mirrors.  Then once your networking issues are worked out, you can put repositories back in place and you'll be good to go.  But be patient too while it is installing - it can take a good long while, but at least it shouldn't fail.

If you can, use bittorrent or jigdo to get the powerpc port.  Of course you can use http or ftp if needed:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

A quick link to the Etch "stable" http download of the XFCE version:  (you just need CD-1 - scroll to see it if necessary)

[http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r5/powerpc/iso-cd/)

Again, use bittorent or jigdo if you possibly can from the first link provided, otherwise the direct link can be used if you KNOW you have a good connection so as not to waste bandwidth on failed downloads.

I guess you can tackle networking later.  Questions that will probably be asked are:

1) Are you really behind a router, or just a cable or dsl modem, where your other computer is running the necessary ppp software?

2) If you are behind a router, are you in control of it?  In other words, can you change it to dhcp without disturbing others on the network?

More general questions like this will probably be easier to get answered in the networking forum, although I certainly won't mind a quick tip now and then.

But first, get Linux installed - my money for all that you have provided is to go with Debian Etch XFCE4 as a first time installer with no Linux experience but willing to learn and no connection to the internet.

Obviously you'll have to download Debian with the other machine, and be sure to burn it as an iso at a very low speed if you can.

Since you have already tried installing, I'm assuming you blew away everything by telling the partitioner to "use the whole disk".  When installing Debian, just do the same again to make partitioning easy - but first let us know if you have replaced the hard drive with something bigger in the past just in case.

Or, if you were planning on dual-booting, things get slightly trickier for a newcomer, but it can be done.  At any rate, you'll have to have your original installation disks for OS9 or OSX if you want them back, because for the most part - it's bye-bye when you use the whole disk....

---

### Post by Thandien on 2008-12-16
First of all; I would like to state my deep gratitude for the quick, helpful and long replies.

At this moment, I'm burning the Debian installation disk at the slowest speed disk utility lets me.
> Is your disk larger than 8gb?
Slightly. It's about 12GB in size.

Perhaps it would be better to stick with Debian on my iMac, I intend to install Ubuntu on my laptop for general use, which would probably be easier. My plan is to let my iMac sit downstairs and out of sight (where the router is located) and act as a web-server, using my laptop to control it. Debian should do, right?
Thanks again for the assistance, I'll report back once I've tried installing Debian.

---

### Post by cyberdork33 on 2008-12-16
> **Thandien said:**
> Perhaps it would be better to stick with Debian on my iMac, I intend to install Ubuntu on my laptop for general use, which would probably be easier. My plan is to let my iMac sit downstairs and out of sight (where the router is located) and act as a web-server, using my laptop to control it. Debian should do, right?
Thanks again for the assistance, I'll report back once I've tried installing Debian.

Just a suggestion here, but if you want to make a fileserver, installing a desktop environment will only eat up ram, power, and disk space. Learn to use the commandline and ssh/sftp. Installing the Server Edition of Ubuntu will install and setup most everything you would want. If you really want a graphical utility to control the server, look into something like webmin and access a "webpage" on your LAN.

---

### Post by Thandien on 2008-12-16
Hm, that's true. I have only the slightest of experience with the command-line, though, so I'm a bit nervous. Are there any nice, easy to understand guides on how to set a computer up as a web-server through the command line?

Anyway, Ubuntu doesn't seem to want to install, for now. 

I'm going through the Debian install process right now, I'll post again if/when I run into some new problems. *grins*

---

### Post by Thandien on 2008-12-16
Debian is now up and running!
I was going to install the web-server version, but I forgot to select it (as opposed to highlighting it) before I pressed enter. 

Now I may be going a bit too far off the topic of Ubuntu, but this thread is the best place I know to ask: Is there any way to "downgrade" to the web-server version, or should I just reinstall?

---

### Post by tiresia on 2008-12-16
I installed Debian, Ubuntu and other distros maybe 100 times, before understanding and feeling to completely control the system. And you have seen that it lasts not more than 30-40 minutes, according to your machine and the internet connection.

Therefore, just as exeercise and of course if you have time, first learn to use 'apt-get' and 'aptitude'. The best place to learn such tools is of course the Web site of Debian, just look for documentation, and the man pages, just run in a terminal 'man apt-get' or 'man aptitude'. With these two tools you can 'remove' or 'purge' everything you want. 
After that you can install again Debian - as I said just as exercise.  

Another place to learn more about Linux in general is the Linux Documentation Project [http://www.tldp.org/](http://www.tldp.org/) and a forum [http://www.linuxquestions.org/](http://www.linuxquestions.org/) and of course the documentation of the wiki community.
Sometimes the documentations is a bit out of date - but it is still interesting to see how the system developed.
We are trying to build a wiki concerning linux and the powerpc architecture [http://www.ppclinux.info](http://www.ppclinux.info) - you can have also a look there if you are interested.

---

### Post by stream303 on 2008-12-16
> **Thandien said:**
> Now I may be going a bit too far off the topic of Ubuntu, but this thread is the best place I know to ask: Is there any way to "downgrade" to the web-server version, or should I just reinstall?

You don't want to know how many times I have reinstalled and letting the partitioner start all over again by "using the whole disk" - with either Ubuntu or Debian.  You have nothing to lose at this point, and the repetition will boost your confidence.

Cyberdork33 is right about not installing a graphical environment for servers.  However, in the case of certain Mac models, the native commandline fonts without the gui can be a real pain to use, or just downright unreadable for us gray-beards, so one sometimes resorts to installing a very minimal X server and light window manager just to run Xterm terminals.  Nothing fancy, we use *startx* to bring up the gui when needed, do our business in xterm, and then drop out of the X environment.  With your crt-based Mac, this might not be a problem and the commandline should be very readable - I assume.

In any case, be it Debian or Ubuntu, installing the server merely installs the LAMP stack in mosts cases, which by themselves are daemons and services and not graphical programs.  I think this might be what you were expecting.

With Debian up and running now, perhaps just use it for awhile to get a bit more familiar with Linux in general before tackling server administration - and most importantly the commandline.

Without basic familiarity and comfort in the commandline environment, at the first sign of trouble, you'll be sunk.  I'd hate to see you spend weeks or months on it, just to be tripped up by a gui that won't start. :)

---

### Post by Thandien on 2008-12-16
> Therefore, just as exeercise and of course if you have time, first learn to use 'apt-get' and 'aptitude'. The best place to learn such tools is of course the Web site of Debian, just look for documentation, and the man pages, just run in a terminal 'man apt-get' or 'man aptitude'. With these two tools you can 'remove' or 'purge' everything you want. 
After that you can install again Debian - as I said just as exercise. 
Thanks for the advice! I'll do as you suggest.
> Cyberdork33 is right about not installing a graphical environment for servers. However, in the case of certain Mac models, the native commandline fonts without the gui can be a real pain to use, or just downright unreadable for us gray-beards, so one sometimes resorts to installing a very minimal X server and light window manager just to run Xterm terminals. Nothing fancy, we use startx to bring up the gui when needed, do our business in xterm, and then drop out of the X environment. With your crt-based Mac, this might not be a problem and the commandline should be very readable - I assume.
From what I've seen, readability shouldn't be a problem. Thanks for the tip though; if it comes to that, I'll definitely remember this.
> In any case, be it Debian or Ubuntu, installing the server merely installs the LAMP stack in mosts cases, which by themselves are daemons and services and not graphical programs. I think this might be what you were expecting.
Hm.. Are these difficult to set up? What I'd really like to do is the equivalent of "Web Sharing" on the Mac. I'm sure I'll be able to change the httpd and other files through my laptop. I just need to get the web-server running, is what I'm saying. It was running on my laptop, but I heard bad things about running web-servers off such machines, and being able to move my main computer around without my website going down is a big plus anyway. 

So, the stuff I need to learn to begin with: Accessing my server with my laptop, and publishing my website with my server. At least.

---

### Post by cyberdork33 on 2008-12-16
> **stream303 said:**
> Cyberdork33 is right about not installing a graphical environment for servers.  However, in the case of certain Mac models, the native commandline fonts without the gui can be a real pain to use, or just downright unreadable for us gray-beards, so one sometimes resorts to installing a very minimal X server and light window manager just to run Xterm terminals.  Nothing fancy, we use *startx* to bring up the gui when needed, do our business in xterm, and then drop out of the X environment.  With your crt-based Mac, this might not be a problem and the commandline should be very readable - I assume.
ssh is your friend. You can use whatever terminal emulator you want in the other end.

> **Thandien said:**
> Hm.. Are these difficult to set up? What I'd really like to do is the equivalent of "Web Sharing" on the Mac. I'm sure I'll be able to change the httpd and other files through my laptop. I just need to get the web-server running, is what I'm saying. It was running on my laptop, but I heard bad things about running web-servers off such machines, and being able to move my main computer around without my website going down is a big plus anyway.

So, the stuff I need to learn to begin with: Accessing my server with my laptop, and publishing my website with my server. At least.
Depending on what you actually want to put on your website, only having the actual http server installed maybe all you need (apache). If you plan to do anything more than static html pages, look into installing the full LAMP stack

For remote access, on the server machine, install openssh-server. That will cover pretty much anything you will need. It will allow you to transfer files with an SFTP client (most FTP clients support SFTP). You can access the server's commandline by opening a terminal on your laptop and typing [noparse]"ssh username@server.ip.address"[/noparse] (where server.ip.address is your server's local IP address). Once logged-in, you are vitually sitting at the server's commandline.

That combined with a little [screen]("http://www.gnu.org/software/screen/") magic ought to be more than enough.

---

### Post by Thandien on 2008-12-16
Since I already use both PHP and MySQL on my small weblog, LAMP seems to be exactly what I need.

> Depending on what you actually want to put on your website, only having the actual http server installed maybe all you need (apache). If you plan to do anything more than static html pages, look into installing the full LAMP stack

For remote access, on the server machine, install openssh-server. That will cover pretty much anything you will need. It will allow you to transfer files with an SFTP client (most FTP clients support SFTP). You can access the server's commandline by opening a terminal on your laptop and typing "ssh [email]username@server.ip.addr[/email]ess" (where server.ip.address is your server's local IP address). Once logged-in, you are vitually sitting at the server's commandline.

Excellent! Just one more thing - is it possible to use the Finder to access the server remotely, instead of using an FTP client? Being on the same network, my guess is that it is possible, but needs to be enabled somehow.

---

### Post by cyberdork33 on 2008-12-17
> **Thandien said:**
> is it possible to use the Finder to access the server remotely, instead of using an FTP client? Being on the same network, my guess is that it is possible, but needs to be enabled somehow.

Doesn't appear so. I tried to use Go > Connect To Server and put in an sftp address, and this is what I got:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96698&stc=1&d=1229523158[/IMG]
I would recommend Fugu or Cyberduck as the client you use though. Fugu is specifically for sftp and cyberduck is a full ftp client. Both are Free Open Source Software.

[http://rsug.itd.umich.edu/software/fugu/](http://rsug.itd.umich.edu/software/fugu/)
[http://cyberduck.ch/](http://cyberduck.ch/)

If you really HAVE to, you can setup an ftp server to transfer files and use the Finder with that.

---

