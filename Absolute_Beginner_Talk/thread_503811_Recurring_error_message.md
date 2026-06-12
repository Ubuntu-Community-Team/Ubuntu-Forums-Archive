---
title: "Recurring error message"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jdb1981 on 2007-07-18
Hello, and thanks for these helpful forums, this is the first time in 8 months I've actually had a question that was not answered elsewhere...

I keep getting this, about every 20 minutes or so- it only came up after I installed PHPadmin, and a few days I uninstalled it, and it stopped, but I need it to run a webserver, so I had to re-install. I've searched everywhere, and the only similar occurrence I've read about online had to do with a camera, or something... And was not quite the same. Does anyone know how I can make this stop? 

[CENTER][IMG]http://i19.tinypic.com/66128tl.jpg[/IMG][/CENTER]

On a related note, does anyone know of a good guide to add content to your LAMP-served site? I found dozens to help you set it up, and it's up and running fine, but I have no idea how to make it actually, you know, serve HTML pages from a directory on the server... If anyone knows of a good "after-set-up" guide, preferably written for people who are relatively tech-stupid, that would be awesome. Thank you!

By the way, I'm running Ubuntu Server Feisty 7.04, Xubuntu Desktop, fully updated, and standard LAMP server installation, and not much else, this system was just set up a few days ago, and the only other thing I've installed is Azureus, which is working fine. All standard settings should be default, for the most part... It's on an old Athlon 850 w/512 ram. Any other info anyone needs I can post... Thank you!

---

### Post by DBStevens on 2007-07-18
Your system seems to be complaining about media in a CD drive.    I don't know what the connection would be to PHPmyadmin, unless you installed it off of the distribution CD.

I don't have that message and I have it installed.

As for site content, first you need a topic to write about, then you write about that topic, after that you wrap what you have written with a markup language, put the file into the correct directory on your web server and rake in the big $$$ (if only).

---

### Post by jdb1981 on 2007-07-18
OK, well, here's another question; How do you get Ubuntu to stop asking for the installation disc most times you make changes with either Synaptic or apt-get? I read days ago somewhere a command that was supposed to fix this, and ran it, but it didn't work, and maybe this error has something to do with the CD being in the drive all the time. I can't really take it in and out constantly, because this server runs headless, and I'm not in the same room (or city) as it much of the time, so I just left it in, which sucks, because I can't restart remotely, since it tries to install... If someone can tell me the command I need to issue, I'll try and see if that fixes it. Thanks!

As far as the second part...

Thanks, someone sent me a nice PM about content, too, perhaps I should have rephrased my question; I was having a hard time figuring out how to get the contents of a specific HTML document to serve as my "home page" rather than the default index.html, which is just a list of directories within the webroot directory. (I think I said that right) I figured it out, though, in case it might help anyone else, you just have to place whatever HTML page you want to display when you enter your external ip (or domain name) in that folder and rename it "index.html." This assuming you've already set up Apache. By default, that directory is "/var/www". So, more of a nuts-n-bolts question than a design one, but thank you all the same!

---

### Post by spur on 2007-07-18
I would try first by going to  System -> administration->Software sources  and remove the entry for your cd. This worked for me.

---

### Post by jdb1981 on 2007-07-18
*Addendum: *

The command to stop it from asking you for the CD is actually an edit in a config file- *Edit-* Or do it the above way!

sudo nano  /etc/apt/sources.list

You can use gedit, or whatever text editor.

then  place a # in front of the lines at the beginning of the file that start with "deb cdrom:" and save your changes.

This solved the problem, however, I had to go to the disc on the desktop, and tell it to eject. pressing the button just brought the error back up... For reference, I'll include the text of the error here, in case someone else has to google it..

Failed to eject "/org/freedesktop/Hal/devices/storage_model_CR_4804TE"
Given device "/org/freedesktop/Hal/devices/storage_model_CR_4804TE" is not a volume or drive 

Thanks!

---

### Post by DBStevens on 2007-07-18
First you will need to modify the default Ubuntu site setup in /etc/apache2/sites-enabled/default-000 so that a non root protected directory structure can be used (or you'll have to live with entering sudo and your password every time you turn around.  You can actually assign directory structures to multiple users and lock them to each user. 

Now about server security and other operational aspects.

You should visit the server documentation and understand how the configuration containers and options interact.

Then some time spent looking at robots.txt and the robot exclusion protocol. 

Spend a bit of time reading the nuts and bolts forums on WebMasterWorld they have forums on just about every aspect of web sites. 

Read as much as you can about Linux security while you are at it.  You will be operating at the intersection of many systems and a breach can come form more places than you might think.

About the only aspect that you won't have to deal with is intentional employee mischief, and you'll probably be surprised at how much trouble you can unintentionally cause yourself.

Some keywords to search on are:

query string attacks
proxies
absolute hrefs
relative hrefs
base hrefs
htaccess
apache rewrite engine / mod rewrite
302s 301s
scrappers
frames
proper custom error page setup
http headers
rex swain  (he has an online http header checker)
xenu link sleuth
spider traps

---

### Post by XeroZohar on 2007-07-27
I hope it's ok to bring this thread back up, but anyway:

I've been getting the same error message about my CD/DVD drive whenever I try to eject it via the eject button.  This only started happening when I upgraded to feisty (from edgy) a while ago.  I have to either unmount the disc then press the eject button, or just eject it from the desktop.  The discs are mounted but not in actual use, so theoretically shouldn't the automounter detect that and just unmount them and let it eject?  Any ideas why this happened only after the upgrade?  Or rather, the message given almost seems like it tries to unmount it but can't due to an incorrect name or something.

Here's the exact sequence of events, for reference.
1.  I insert a DVD (a video DVD usually, but it could be data or a CD-ROM), and it mounts itself as usual.
2.  I press the eject button on the drive.  (originally, it would unmount, eject, and all was well)
3.  The error shown above in the first post pops up, with the name of my drive as the only difference.

I'm so confused and not really sure where to start looking for solutions.  :confused:  Well, not that it's the biggest hassle in the world, but it's -really- counterintuitive for the eject button not to work when it should.

---

### Post by DBStevens on 2007-07-27
That message is misleading, no doubt about it.

But what it is attempting to do is say:

Hey,  look here you.   You  have mounted media in a device perhaps you really should unmount it before sending it into space.  

Maybe the last user of the device should unmount it but I doubt if that always happens.

---

