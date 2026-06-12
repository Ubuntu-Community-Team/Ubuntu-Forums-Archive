---
title: "installing flashplayer"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by robeec on 2007-04-18
i've been trying to install flashplayer for about 6mos now. i've dl-ed the file about 50 times and installed it, but i still can't open flash video. today i decided to try again, and after doing some web reading, i found a page that said to copy "libflashplayer.so" to the mozilla plugins folder and "flashplayer.xpt"  to the mozilla components folder. well after an exhaustive search, i found the folders and tried to drag the files to copy them, i got "you do not have permission". so i read about permissions...and came out more confused than i went in. is there a way to get these two files into their appropriate folders from the root terminal?

any help will be greatly appreciated.

---

### Post by Antman on 2007-04-18
Here is a good link. Just follow the instructions for your Ubuntu version (dapper, edgy, etc).
[https://help.ubuntu.com/community/RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash")

:guitar:

---

### Post by starcraft.man on 2007-04-18
While this question already answered... I'd just like to direct ya to [ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox"), great place to learn all the commands. It lists almost anything you want to install and its searchable :).

---

### Post by MindRiot on 2007-04-18
Download the file to your desktop, then double-click the file and the archive manager should open. Select  All files and click extract. This should create a folder.  Change directory to the folder and then type ./install_flash_player, or something like that (see instructions at [www.adobe.com)](www.adobe.com)).  This will run a self-executing installation program, which should automatically place the link in the mozilla/plugins folder.  The mozilla/plugins folder is located at:  /home/username/.mozilla/plugins   To see the .mozilla folder, enable view hidden files from the view menu in file browser and look in your username folder.

---

### Post by robeec on 2007-04-19
thanks great ppl! i'm gonna give your advice a try. i'll let you know how it goes.
thanks again!

---

### Post by robeec on 2007-04-19
i tried mindriot's suggestion first. i got the message "plz ask your administrator to remove xpti.dat from the components directory of mozilla or netscape browser". so i'm gonna try to get a grip on permissions. truthfully i never understood permissions even w/ mac or windoze.
thanks folks...you rule!

---

### Post by philip360 on 2007-04-19
Hi Robeec: 

[http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

This is a good reference as well. I have followed it several times for 6.06, & 6.10K. 
Lots of other good info too. 

Philip

---

### Post by robeec on 2007-04-19
well i tried all the suggestions and i did not get flash to play but i dl-ed mplayer and that is playing the flash vids. anybody having difficulty installing flashplayer may want to try mplayer--mp seemingly took over embedded video too--but the quality's pretty good too and so i'm happy.

thanks! i've learned a lot reading this forum. my goal is to eventually be smart-enough to give advice.
rob

---

### Post by oilchangeguy on 2007-04-19
you can use automatix to install flash and much more. go to [www.getautomatix.com](www.getautomatix.com)

---

### Post by robeec on 2007-04-20
> **oilchangeguy said:**
> you can use automatix to install flash and much more. go to [www.getautomatix.com](www.getautomatix.com)

wow! thanks for automatix! i got errors back on flashplayer, and it wouldn't install but i did get real player and some codecs too. i installed kubuntu which i like. i installed dapper drake last year but reinstalled windows vista--the o.s. was so lethargic, i put ubuntu back. i'm keeping ubuntu for good.

---

### Post by jaq_im on 2007-07-14
thanks Phillip after trying many different sugestions yours was the one that worked
:)

---

