---
title: "damaged gutsy? sloooow boot, screen problems"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by maya9 on 2008-01-14
I attempted to install KDE 4.0 a couple of days ago and it went very badly.  I finally got it off my system (not showing up in the session options, aps not showing up in the menus).  I did some removing with Synaptic as part of that. (could I have mistakenly taken something off I shouldn't have?)

For a while, I couldn't get Ubuntu to boot at all--it would go to a black screen--except in recovery mode.  Now it is booting in (whoo hoo!), BUT the boot is incredibly slow, 3-4 minutes (it used to be about 30 sec before all this), including a full minute and a half of black screen, flashes of snow, zig-zag lines, red dots, and other screen madness.  And once up, though everything is working, it is still very slow, for example, a lag time when hitting a letter and it showing up on the screen, aps loading really really slowly, etc.

Help!  I want my old gutsy back!  I have no idea what to do next.  Do I need to reinstall? If so, how do I do that without a CD?  And will I have to reinstall all my stuff (docs, music, photos, etc).

Thank you!

---

### Post by bumanie on 2008-01-14
I don't know of a fix for what you describe, but as it does boot (although slowly) you should be able to save all your documents, photos or whatever to some external media (dvd, external hard drive etc). You seem to have internet access, so if worse come to the worse, you can download and burn a cd.
But wait for a while. Thnere are many knowledgeable people on this forum, if there is an answer someone will come up with it. I have some ideas that may help, but will have to do some more research first. If I come up with anything I will get back to you. Hopefully in the mean time someone else can help.
Could you please post your system specs.

---

### Post by maya9 on 2008-01-14
My stuff is backed up, it's just a drag to reinstall it all--it would be excellent to avoid that if possible.
I have internet on the ubuntu laptop, and on the windows desktop.
The problem laptop's specs:
Sony Vaio pcg-r505gl
258 mb ram
25 GB harddrive, 10 available
no partitions or other os
I ran dapper for a while and recently updated to gutsy using system update.
Then I got lured by the sexy kde screenshots--should have left well enough alone! Everything was working great!
Sigh.
Is there any other info that would be useful?

---

### Post by philinux on 2008-01-14
For the boot, install 

startupmanager from synaptic. Then run it.

Click the psychocats link and the scroll down for kde, gnome, getting pure gnome etc. All the info you need is there.

---

### Post by LukeCarrier on 2008-01-14
Hi,
 
I can't really help you other than to recommend you do a re-install. If you really don't want to do that, you could always try removing KDE and re-installing Gnome.
 
Personally, I'd opt for the re-install.
 
--Luke

---

### Post by sailor2001 on 2008-01-14
> **maya9 said:**
> My stuff is backed up, it's just a drag to reinstall it all--it would be excellent to avoid that if possible.
I have internet on the ubuntu laptop, and on the windows desktop.
The problem laptop's specs:
Sony Vaio pcg-r505gl
258 mb ram
25 GB harddrive, 10 available
no partitions or other os
I ran dapper for a while and recently updated to gutsy using system update.
Then I got lured by the sexy kde screenshots--should have left well enough alone! Everything was working great!
Sigh.
Is there any other info that would be useful?

did you update from dapper to gutsy?  Jumping a distro is just begging for trouble....My personal suggestion would be to back-up to an external and completely re-install

---

### Post by maya9 on 2008-01-14
Hello, thanks all.  No, I didn't jump a distro, but went through the whole process through Edgy and Fiesty.  Gutsy was working properly before I tried KDE.  I have removed KDE.  I had already found the 'getting pure gnome' page at psychocats and had already done what they suggest when I posted.  

If a reinstall is what I need to do, how do I do that without a disk?

I will try startupmanager and report back.

---

### Post by maya9 on 2008-01-14
still having a three minute boot (hubby just pointed out that I used to have a 6 or 7 minute boot with windows on the machine!) with weird screen effects, and sluggish ap load time.  I put startup manager on there.  It's livable right now, but it sure ain't what it was a couple of days ago.

---

### Post by maya9 on 2008-01-14
I also just noticed that in the terminal, it says maya9@ubuntulaptop:~$  Isn't it supposed to end with a # ?  And a few times when I have tried various things I have gotten a message saying it couldn't do whatever it was and asked "Are you in root?"  
Does this make sense to anyone?  Could it be related?

---

### Post by philinux on 2008-01-14
Run startupmanager and tick the option for text information on boot up. Reboot and look whats being loaded. You may spot the culprit. Mine takes 53 seconds to boot and 14 to shutdown everytime.

Also click link below for known bugs.

---

### Post by maya9 on 2008-01-14
Okay, I checked the text box but it goes by really really fast, impossible to read, for about 15 seconds, then it all goes black for a minute and a half, then the crazy screen effect (stripes, snow, black and grey zigzags) then the login screen, I log in, then a white screen for another minute, then we're in.
Shut down takes a full minute with most of that being black screen (it used to be fast, too).
Is there a way to go back and see what it said, a log of what it's doing in bootup somewhere?

---

### Post by philinux on 2008-01-14
Sounds like a graphics driver issue maybe.

The log you want is 

/var/log/messages/messages.log

It's quite long but you can scroll through quite quickly and see whats going on. 

There is a utility called bootchart in synaptic it creates a graphical process boot chart with timings etc. It creates a png file each time you boot. Might be useful for you.

[http://www.bootchart.org/](http://www.bootchart.org/)  (for info)

Did the link below for known bugs help at all.

---

### Post by maya9 on 2008-01-14
Okay, this is weird.  Suddenly it wasn't booting at all again, just black screen and stuck.  So I (swore a bunch of times and then) booted into recovery mode and it did that check thing (what is that anyway?) that it does every 30 times.  I couldn't go online in recovery mode to get the bootchart thing, so I shut down.  On a lark I started it up again and Lo! it went right through, no black screen, full boot (including me entering my login and password) in less than 2 minutes.  Still did a flash of crazy screen garbage after all the words and right before the login screen.  But it did words all the way through, no black screen for a minute and a half.
I installed bootchart, but it isn't showing up on any of the menus.  I'd like to use it--it sounds like just what I need, but I can't find it to run it.
Things are looking up!

---

### Post by philinux on 2008-01-14
You run bootchart from the terminal I'm guessing. I last ran it two months ago and since uninstalled it as my boot problems were solved by startupmanager.

Glad its cut the boot time down to something reasonable. But I bet there's more to squeeze yet.

---

### Post by philinux on 2008-01-14
With boot chart installed it just does its thing, you have to find where it's put the png file. I last ran it two months ago and since uninstalled it as my boot problems were solved by startupmanager.

Glad its cut the boot time down to something reasonable. But I bet there's more to squeeze yet.

---

### Post by philinux on 2008-01-14
Found it.

Have a look in directory

/var/log/bootchart 

It creates a new chart every boot so once you got it sorted you can uninstall it.

---

### Post by maya9 on 2008-01-14
Is there a way for me to show the results of the bootchart image?  Can I paste an image here or something?

---

### Post by maya9 on 2008-01-14
The things that start up the latests (towards the bottom right of the tbootchart image) and thus, perhaps, have to do with the wacky screen snow, are 
mdadm
atd
cron
s90binfr
update-l

Then, at the very bottom of the list are a series of things that appear to be doing stuff the whole time (their bars go from the far left to the far right)
kthreadd
migration/0
ksoftirqd/0
watchdog/0
khelper

The very last few things on the bottom of the list ( and are running all the way to the end/right)
kjounald
scsi_eh_3
kpmoused
pccardd
kondemand/0

All this 'k' stuff makes me wonder if they are related to KDE, even though I have supposedly removed all fo that.  Is that true?  If so, perhaps getting them off of there would help?

---

### Post by EnergySamus on 2008-01-14
Wow.
I am no Ubuntu master, but I have had issues like this before with Windows. It was on my reeeeaaallly old Windows 95 PC. I tried to install Windows 98 SE, but my computer rejected it (really slow bootup and shutdown, lots of error messages). So I had to reinstall my entire OS!!! I know that Ubuntu isn't Windows, but it might be the same sort of issue. I'd recommend reinstalling the OS. Get all of your Memories and documents of of the PC first. 
Also, I would recommend installing more RAM. 256MB is a little bit too cramped... 512 is better!:lolflag:

Good Luck!
EnergySamus

---

