---
title: "misc problems running Dapper on MacBook Pro 15 inch"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by goneskiing on 2006-08-21
I think most of these have been noted but for reference:

1) kernel panic happens with and without usb mouse plugged in.  usually only takes another reboot to get past

2) sound doesn't work

3) display isn't right, only getting sxga 12?? x 768 instead of 1440 x 900

4) I have it set for hibernation upon lid close.  hibernation actually turns off machine but upon boot up does return to previous screen.  this might be right but is not same as mac. Does suspend work ?  When I tried to set as suspend I got a bad warning so I used hibernation instead.

5) haven't tried out wireless yet.

6) I really miss the home, end, and delete keys - can any single key be set as these ?

---

### Post by idn on 2006-08-22
1 - yeah this is a problem, afraid you are just going to have to deal with the occasional panic for now

2 - you need to make a patch to the also source code and reinstall - see this post - [http://www.ubuntuforums.org/showthread.php?t=198453](http://www.ubuntuforums.org/showthread.php?t=198453)

3. See the above thread - you need to install the latest ati drivers and install the posted xorg.conf file, I have also attached mine

4. Havent tried to get this to work

5. It works ok for, you have to install the restricted drivers module for your current kernel, you may also want to backup then remove everything in the /etc/network/interfaces - mine is attached so you could just use that.

6. Hold down the fn key and you can then use the top, left, down and right keys to go page up, end, page down and home. Holding fn with delete uses the other kind of delete


Make sure you remove the .txt file extensions

---

### Post by goneskiing on 2006-08-23
[I]6. Hold down the fn key and you can then use the top, left, down and right keys to go page up, end, page down and home. Holding fn with delete uses the other kind of delete
[/I]

This still involves using 2 hands, 2 keys - I was hoping there was a key binding that would restore these to a single key each.

---

