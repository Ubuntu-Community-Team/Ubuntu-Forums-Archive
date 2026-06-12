---
title: "Installing Flash player [Resolved]"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-05
As a Linux learner, I am trying to install Flash player, after download:  'install_flash_player_9_linux.tar.gz ' is  shown on my desk top.  I do have the install instructions which tell me to unpack the file ( no idea how to do this !) then a directory (with exactly the same name as shown above) will be created.  Has this directory been automatically created by Ubutu ?  And how do I find the file in terminal - I have looked at Linux commands but can't see how to it !   Many thanks,  Colin

---

### Post by shareMenaPeace on 2007-02-05
Hi to extract a tar archive, rightclick the file and choose "extract". This extract the archive to a relative folder.

For a fast start and new to the linux world i can recommend using 

[http://getautomatix.com](http://getautomatix.com)

This is a application installer which works very EASY.
Download the installer (depending on which ubuntu version you have installed) and run it.
This installs automatix2 on your computer - accessable from Applications -> System Tools

Automatix let you install the most needed things like FLASH plugin for browser, MP3 Codecs, Many Sound and Video tools ...much more. And all with just a few "Clicks" :)


Cheers

---

### Post by r4ik on 2007-02-05
Just something you might want to have a look at,

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Good luck !

---

### Post by taurus on 2007-02-05
Or this since you have already downloaded the .tar.gz file.

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

### Post by aysiu on 2007-02-05
> **r4ik said:**
> Just something you might want to have a look at,

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) More specifically, [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by ColinP on 2007-02-06
Hello ShoreManaPeace, R41K, Taurus and Aysiu,

Many thanks for your help !  Flash Player is now installed !      

Cheers,  Colin

---

### Post by Starry on 2007-02-09
YAY!!

i have been having this same issue myself and following the exact instructions given by adobe and came here finally to see if there were others having the same issues i was with this craptastic thing.  following the great advice i'm trying to get this done, my very first EVER coding thing in a terminal done on linux.

it'll make my internet surfage much easier and prettier and i am much obliged.

i have gotten almost ALL the way through this problem but now i am stuck at the LAST STEP.  the last site quoted is what i have been following and it works up the last commands: 

sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

its telling me that they don't exist.  everything else worked though.  went through no problem.  i'm at a loss.

---

### Post by dannyboy79 on 2007-02-09
when I installed flash I don;t remember having any flashplayer.xpt file. to figure out if your sudo is broken just try this. sudo cat /etc/fstab, if it asks you for a password and then it it displays information than your sudo is NOT broken. as far as flash being installed it should be. habe you tried youtube.com yet? don't foget to restart firefox if you haven;t closed it yet prior to installing flash. good luck

---

### Post by Starry on 2007-02-09
> **dannyboy79 said:**
> when I installed flash I don;t remember having any flashplayer.xpt file. to figure out if your sudo is broken just try this. sudo cat /etc/fstab, if it asks you for a password and then it it displays information than your sudo is NOT broken. as far as flash being installed it should be. habe you tried youtube.com yet? don't foget to restart firefox if you haven;t closed it yet prior to installing flash. good luck

thank you.

according to this my sudo is fine lol.  that is at least good news.  i haven't screwed things up..............yet.

---

### Post by dannyboy79 on 2007-02-09
well you didn't state whether or not you got flash to work? this is important since you changed your subject line of the thread to solved but then didn't state whether or not you got it working.

---

### Post by Starry on 2007-02-09
> **dannyboy79 said:**
> well you didn't state whether or not you got flash to work? this is important since you changed your subject line of the thread to solved but then didn't state whether or not you got it working.

oh this isn't my thread.  i just posted in it because i followed the same directions that this person did but didn't get flash installed like they did hence i started that sudo thread that you followed to this one...i'm still working on it.

---

### Post by SpikeyB on 2007-02-10
> **shareMenaPeace said:**
> For a fast start and new to the linux world i can recommend using 

[http://getautomatix.com](http://getautomatix.com)Nice one.  I have spent ages trying to install flash only to find out there was not a version for my AMD64.  I installed Automatix and downloaded 32 bit Swiftfox which came with a flash plugin.

Thank you very much.

---

### Post by mimsmall on 2007-02-11
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash) worked for me. Just copy/paste each step, reloaded Firefox and viola! 

The person who put the site up mentioned that they were a regular visitor to this forum. Thank you.

---

