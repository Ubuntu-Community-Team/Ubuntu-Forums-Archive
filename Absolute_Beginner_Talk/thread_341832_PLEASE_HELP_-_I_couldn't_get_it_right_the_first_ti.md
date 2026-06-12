---
title: "PLEASE HELP - I couldn't get it right the first time so I'm starting over."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by tibrslackey on 2007-01-19
I like the feel of the Ubuntu Community. I like how the more experienced users don't belittle the newbies and are willing to help someone as clueless as I am. I've read through the forums but when it comes to writing code I just can't get it.  I want to get out of Windows but I can't get Ubuntu to do what I want. I'm going to give it my best effort one more time but I need help.

I have started over with a fresh install of Edgy.

Here is what I want to do:

Install the driver for my Belkin F5D7230-4 Router.
Install World of Warcraft for my son. (I know I have to install WINE and I believe I can get it from the Add/Remove Program, right?)
Get Ubuntu to recognize my iPod or better yet install iTunes if possible.
Install the driver for my wireless keyboard and mouse.

I have two other computers that have Belkin F5D7000 wireless card that need the driver installed also.

Please help! Like I said, I started over with a fresh installed of Edgy. I have done nothing else to it. It is a blank canvas. Instead of saying /<pathtodirectory>/whatever.exe, please spell out the path, most of the time I can't even find the path. I know its a lot to ask for but if I can get those things taken care of I can learn at my own pace. Any help is greatly appreciated!

---

### Post by deadgobby on 2007-01-19
Here is a Howto for the Belkin. 
[http://ubuntuforums.org/showthread.php?t=262465&highlight=Belkin+howto](http://ubuntuforums.org/showthread.php?t=262465&highlight=Belkin+howto)

---

### Post by Jussi Kukkonen on 2007-01-19
Hi, tibrslackey

I suggest you post one post for each problem (preferably of course after you've searched the forums and wiki.ubuntu.com for solutions), that usually works better.

Some advice:
* You don't need a driver for your router -- you may need one for your wireless card though.
* WOW issues will be handled best in the gaming sub-forum
* Most mp3 players work out-of-the-box when you connect them (they'll appear on the desktop). If ipods do not, someone will no doubt let you know what to do...
* again, many wireless keayboards just work (maybe not with all of the extra buttons though) just try it.
* Any time you have a problem with a usb device (like ipod or wireless keyboard), you should paste the output from this command:
 [INDENT] 1. run  ***tail -f -n0 /var/log/messages*** in a terminal
  2. connect the device
  3. copy-paste whatever was printed on the screen to your post.[/INDENT]

Hope this helps.

---

### Post by tibrslackey on 2007-01-19
Thanks for the quick responses. I get frustrated very quickly. I searched the forums and wiki be still did something wrong. This is my very first experience with Linux in any form. I've been a Windows user since the 3.1 days so if I can't click on it or it doesn't autorun I'm lost. My navigation skills consists of clicking through folders in the windows explorer so I'm way out of my comfort zone. I'm at work now and can't try any of these suggestions until later. I just wanted to say thanks for the replies.

---

### Post by BarfBag on 2007-01-19
A good place to start would be [Automatix]("http://www.getautomatix.com/").  It's an install script that takes care of things like MP3 and DVD support, browser plug-ins, and other things that can be difficult to install.

Most music players in Ubuntu support your iPod.  I don't own one myself, so I can't tell you the best from personal experience.  For starters, you could try Rhythmbox (comes with Ubuntu).  You can find the link in Applications -> Sound & Video -> Rhythmbox Music Player.  If that doesn't work out, there's also AmaroK and GTKPod.  You have to install those yourself, so if Rhythmbox doesn't work out, either post a reply here or contact me.

As others have said, your router doesn't need a driver.  As long as it has DHCP enabled, you're good to go.  However, if you have a wireless network - you do need drivers.  I've never set this up myself, so I can't help you here.

[Here's instructions on how to install World of Warcraft.]("https://help.ubuntu.com/community/WorldofWarcraft")

One last thing.  You'll probably want to mount your Windows partition so you can access your files from Ubuntu.  [Here's instructions.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

I wish you luck!  Keep at it.  We all did, and look at us now.  :)

---

