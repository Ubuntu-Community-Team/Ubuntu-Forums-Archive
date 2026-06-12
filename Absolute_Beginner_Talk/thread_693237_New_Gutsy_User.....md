---
title: "New Gutsy User...."
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by CynicX on 2008-02-10
Hey guys....New Ubunto Gutsy user here.  I'm trying to make the switch to Linux starting on my laptop as it has nothing special on it.  Last time I switched to Linux during the install the boot sector of a very expensive hard drive was corrupted and it cost me 200+ dollars to fix.  So years pass and I decide to try Ubunto....

ANYWAY I have two really quick questions...

First off I it wont remember my WiFi information.  I've entered my wireless router connection information into Manual Network Config and it works fine.  Turn the computer off and back on and I have to redo it.  It will REMEMBER everything but it just wont work until I re-enter my password for the router....its a real hassle as its very long and random...

Secondly and not so easy of a question is where can I find information about converting my extensive Windows knowledge to Linux?  I dont understand how the file system works at all...its quite frustrating as I know how to get anything done in Windows in SECONDS and it takes hours in Ubuntu before I give up....Maybe just like a general knowledge or how to webpage...

My buddy recommended my BUY a book from Barnes and Noble.  I laughed because I can Pirate Windows in 15 minutes...why would I BUY a book for FREE software...you know?

I guess I'm a dork in essence just wanting to learn the ways of Linux!!

Thanks guys for any help!!

---

### Post by dstew on 2008-02-10
> Maybe just like a general knowledge or how to webpage[This site]("http://www.linux.org/") has good lessons in Basic Linux, that are arranged with a table of contents so you can skip what you know. Look for the Courses button.

---

### Post by jonkulp on 2008-02-10
When I first started using Ubuntu about two months ago I had troubles with the wireless, too.  I couldn't even make it work if the network required a password.  The solution for me was to configure my router only to admit my MAC address and no one else's.  That way I didn't need a password anymore.  Now my laptop hooks right up to the network as soon as it's done booting up.  I've checked the security by trying to get on the network using other laptops and they can't get on, so I'm assuming it's secure enough in this configuration.

I'm not sure what to say about the file system question.  Are you trying to figure out where your apps are stored and that kind of thing?  There are lots of hidden files and that's where you'll find apps and configurations and stuff.  One piece of advice I'd give is to backup your xorg.conf file before you mess around with any display settings.  I learned the hard way that if this file gets jacked up there are serious problems.  It's in /etc/x11.  Back that file up and keep it on a flash drive or another computer in case your x11 configuration ever gets out-of-whack.  I haven't had to poke around in application folders much except to transfer email into Thunderbird.  Other users are probably much better prepared to answer file system questions.  Good luck!  JK

---

### Post by amingv on 2008-02-10
I'll go with your buddy here. Knowing how to "pirate" windows won't help you a single bit in linux. Don't underestimate free software as not being book-worthy...

The ubuntu wiki is a good place to get basic info: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

BTW, Kazaa is not a hacker tool...

---

### Post by steveneddy on 2008-02-10
> **chirulais said:**
> cheeeeeeeeeeeeetos.... mmmm

I love cheetos. The puffy ones or crunchy?

Try[ ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy")

---

### Post by CynicX on 2008-02-16
Thanks for the help guys....I'm still having a hell of a time to getting this thing to log on without having to re-enter my WPA password.  I've actually memorized my random number and letter password now hahah....

Anyway I cant mess with the router as its setup to work with 1 PS3's, 1 xbox 360, 2 desktop computers, 1 nintendo wii, 2 laptops, and a mac.  The PS3 is in the DMZ and everything has static IP besies this laptop I'm trying to learn Linux on....Its just too much work to reconfigure everything...

This could just be something very stupid.

But when I start Ubuntu everything goes well and I start firefox (been using it for years in XP) and it will saying Loading....or Waiting for....com but nothing.  I click the little Manual Network Config in the upper right then click Manual Config.  Then on the screen I goto properties of Wireless and re-enter my password....it does it thing and then the web works fine....

But I have to redo this every time I turn on the laptop.  Is this common?  Maybe a simple fix?  I've googled around but I'm so new to Ubuntu and Linux that I cant really source much out yet....thanks guys...

---

### Post by badmedic on 2008-02-16
By default Network Manager will not automatically log into WPA secured Wifi networks. There is a way to make it connect when you log onto Ubuntu though, using libpam-keyring... Take a look at this Feisty how-to:

[http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html](http://blog.yumdap.net/archives/56-The-ease-of-WPA-in-Ubuntu-Feisty-Fawn.html)

I have seen other people recommend switching from Network Manager to Wifi-Radar, but I have never tried it.

---

### Post by CynicX on 2008-02-17
Thanks guys.....It seems the more I just mess around the more accustom I get with Ubuntu Gutsy..  I'll probably end up investing into a book...Although I think it would be too difficult to use Linux on my other computers (i use them for tuning cars), I think its pretty neat to use on my computer I use for web browsing....

I think my issues are more of bugs.  Sometimes gutsy will hang when I shut it down.  It also uses more resources vs XP that I had previously on here...I have constant 4-7% CPU usage and about 50% memory usage.  Thus the battery life suffers....

Probably has a lot to do with this computer being kind of old Toshiba Sat. Celeron.  Even when I set the CPU usage to 50% I could get an extra hour out of XP running at 100% on the same system...

Maybe once I got more used to I can figure out why/whats sucking up all the resources.....

---

### Post by jerrynewt on 2008-02-17
I went from using Network Manager to Wi-fi Radar and finally to wicd (it's in the repos). I use it for my laptop when on the road and it works like a charm. Automatically locates available wireless and wired networks and after initial configuration, just a click and you are connected everytime !!

---

### Post by CynicX on 2008-02-19
> **jerrynewt said:**
> I went from using Network Manager to Wi-fi Radar and finally to wicd (it's in the repos). I use it for my laptop when on the road and it works like a charm. Automatically locates available wireless and wired networks and after initial configuration, just a click and you are connected everytime !!


Well I tried Wifi-Radar and it was OK but I like the normal thing more.  So then I tried the other one but it doesnt seem to work...It downloaded and all but I get the message "Unknown Encoding etc etc....a bunch of wingding looking symbols pop up with it/usr/etc/etc"  You get the idea.

I'm gong to run to Barnes and Nobles tonight when my girlfriend goes to work and maybe once I learn how the file system works I'll be able to get around better.  Anyone know of a quality Linux book for beginners that will get you to a level of self learning?  I found a lot of stuff online but I can learn better from a book I can read while I'm not around my computer

---

### Post by CynicX on 2008-02-22
I got a book for those who care.  But its more of a Ubuntu book rather then Linux.  So basically I need a new book...lol...

I'm actually going to have to put Ubuntu off for the time being though.  Its needs to much/many resources.  Basically my computer is too slow.  Windows XP works great on this machine...

I cant even really play the game Gnometris because it will get a little laggy and I'll end up spinning a piece way too many times.

I thought Linux was supposed to be faster or at least not use as much memory.  I tried re downloading , re burning a fresh copy of Gutsy to a flreshly formated harddrive (1 drive laptop)  but its about as slow as Windows Vista is on this machine.  So Windows XP is probably my best bet.  XP flys on this machine (its what came on it when I bought it)....

Maybe once I get a faster computer I'll be back to try Ubuntu again.  Thanks for the help guys!  I might try a different Distro for the timing being.

---

### Post by mrsudo on 2008-02-22
all my network info is in my /etc/network/interfaces file.  im not sure if that will help at all.

I learn linux from poking around on my machine, reading websites and browsing the forums.  there are also many tutorials on the net which will help.

---

