---
title: "cannot save firefox downloads to fat32 drive"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by tux21 on 2006-12-28
my entry in fstab for windows drive (/dev/hda5) is

UUID=7CB3-798D  /media/hda5     vfat    user,defaults,utf8,umask=007,gid=46 0       1


I cannot save my downloads from firefox to this drive.
the download completion window doesn't show up at all and the downloaded file is stored as a zero byte file in that drive.

Unfortunately it only happens with firefox and not konqueror etc.

Similarly i get extraction errors in some of the zipped files
in that drive.

This problem never occured in 6.06 LTS

---

### Post by PriceChild on 2006-12-30
*thread moved and approved*

---

### Post by tux21 on 2007-01-06
plz reply

its the only major problem in edgy

---

### Post by taurus on 2007-01-06
Why not modify your /etc/fstab and make it look like this?

```
/dev/hda5   /media/hda5   vfat   iocharset=utf8,umask=000   0   0
```
Then reboot and see if you can write to /media/hda5!  How big is the file you want to save to /media/hda5 anyway?

---

### Post by tux21 on 2007-01-06
i'll try

what are these weird names UUID=7CB3-798D  

edgy gives to my drives in fstab?

---

### Post by tommytom on 2007-01-06
This should help answer those questions,
             
[indent][/indent][http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by tux21 on 2007-01-06
did not work !!
[http://www.mozilla.com/en-US/products/download.html?product=firefox-2.0.0.1&os=linux&lang=en-US](http://www.mozilla.com/en-US/products/download.html?product=firefox-2.0.0.1&os=linux&lang=en-US)

is the test file i tried 
it is firefox 2.0

I can write to that drive but problem is with firefox downloads and while extracting some compressed files in that drive i get 

"An error occurred while extracting files."

and details of that as

"tar: install_flash_player_7_linux/flashplayer.xpt: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: install_flash_player_7_linux/flashplayer-installer: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: install_flash_player_7_linux/Readme.htm: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: install_flash_player_7_linux/Readme.txt: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: install_flash_player_7_linux/libflashplayer.so: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: install_flash_player_7_linux: Cannot change ownership to uid 1000, gid 100: Operation not permitted
tar: Error exit delayed from previous errors"

---

### Post by tux21 on 2007-01-07
any hopes?

---

### Post by fsando on 2007-01-14
Same problem here
1. firefox will not save to fat32 (saves a file of the correct name but 0 size)
2. gedit complaints that it is not able to make backup when saving a file to fat32

Gone through the advice above but it is not obvious what to do with it. My drive is already umask=000.

Any help here?

---

### Post by tux21 on 2007-01-15
Finally BLAG 6000 has being released

its an amazing 1 cd distro based on fedora core 6
(thats why 6000) They had about 50 alpha releases
and 2 beta releases after fc6 was relased to get to 
this much of stability. Those who grumble and rant about fedora's bugs and problems (like mp3 support, 5 cd downloads etc ) must try this. In short it is 1 cd fedora which behaves well !!

[http://forums.blagblagblag.org/viewtopic.php?t=3477](http://forums.blagblagblag.org/viewtopic.php?t=3477)

what more it has adopted the ubuntu model of Shipping cd's to you for free!

[http://forums.blagblagblag.org/viewtopic.php?t=3486](http://forums.blagblagblag.org/viewtopic.php?t=3486)

Belive me guys they have a small yet strong forum at
[http://forums.blagblagblag.org/index.php](http://forums.blagblagblag.org/index.php)

and their developer named jebba will actally reply to your queries.

So stop wasting your time reading this and grab it.

---

### Post by tux21 on 2007-01-15
no gedit prob with me.

as for FIREFOX (with flash 9) i discovered that it was making my life miserable. so i switched to konqueror. same tabbed experience but no crashes. hangs etc

---

