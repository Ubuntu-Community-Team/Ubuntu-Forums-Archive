---
title: "[SOLVED] Which filesystem is most stable? Gutsy not starting"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by shareMenaPeace on 2007-12-24
I just had to hard turn off teh notebook because off a screensaver i could not exit (black screen).

Now i need to reinstall gutsy

Questions i have

What is teh best filesystem in lunix for this kind of issue? I used reiserfs?

Is there maybe a way to fix this?

Can i install hardy? And how?

I outlined the issue here
[http://ubuntuforums.org/showthread.php?t=648971](http://ubuntuforums.org/showthread.php?t=648971)


Please respond as im in hurry .... meh

---

### Post by shareMenaPeace on 2007-12-24
PLEASE someone tell me which filesystem i should use for most stableness ... i had this haoppen in the past to hardware reset ... on a dell notebook and this never happend but im not sure if i had ext2 or 3 ....

I need to reinstall now ...please some answer, thx

---

### Post by philinux on 2007-12-24
Ext 3 is a journaled file system. supposed to be better than ext2.

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3) 

Your black screen might not be file system related though.

---

### Post by shareMenaPeace on 2007-12-24
I know but i had to hard reset the notebook because of either this issue here or because of the screensaver which brought a black screen ... and didnt let me exit - i had this tooo very often on my old notebook dell d620 ...and now thsi happend iek 3 times ..ahhhwww
I just was about to stick with my installation i had EVERYTHING setup ...AWN was teh last touch ....menno!

[http://ubuntuforums.org/showthread.php?t=648949](http://ubuntuforums.org/showthread.php?t=648949)

---

### Post by LowSky on 2007-12-24
blank screen isnt cause by the file system, and ext3 is the best option right now.

the blank screen is a bios option, what is the make and model of the computer you using now? Plaease give all the specs you can.

Why not turn off screen saver or change the settings for idleness

---

### Post by philinux on 2007-12-24
+1 Lowsky

---

### Post by shareMenaPeace on 2007-12-24
ASUS x50v apo48c refurbished
intel core duo t2450 2ghz 2mb 533mhz fsb
ati xpress 200 128ram
2gb ram

---

### Post by LowSky on 2007-12-24
ok im guessing the issue lies with the ATI graphics, what driver are you using, did you use Envy to install the driver?

\BTW: thanks phil

---

### Post by shareMenaPeace on 2007-12-24
Because till 30 misn ago i always got a blank screen when have random screensavers, but could always exti exept for liek 3 times since i got this notebook 4 days ago.
I just set a special sreensaver (on the bootom of the menu of screensaver choose). btw SNOWFLAKES screensaver was working ...

---

### Post by shareMenaPeace on 2007-12-24
I used envy, and i turned on restricted drivers last night, and all was working very well and smotth (see my gallery)

What i tried last is to install AWN and i got a segmentation fault .... well thank you i go and use EXT3 now instead of reiserfs!

---

### Post by LowSky on 2007-12-24
ok theres your problem.. envy installed the driver and then you installed ubuntus version with restricted drivers. just use envy to reinstall the ati driver

---

### Post by shareMenaPeace on 2007-12-24
but its not booting or do you mean when i reinstalled ubuntu? And this happend before ..before i turned on restricted drivers

---

### Post by shareMenaPeace on 2007-12-24
So i need to reinstall now? (And go to use ext3 for more stableness, because of random screensaver crashes) ?

Or can i try soemthing?

Well itz have to wait ...xmas is now lol AND JUST NOW THSI HAPPENS this is so sad i was about to show off ubuntu to my family ...meh

(now i can just show vista) :)

---

### Post by LowSky on 2007-12-24
ok im confused... what issues is going on right now

And for clarification the scrensaver crashes have nothing to do with the filesystem!!! It is your graphics driver!!

If the computer is not booting you have other issues, probably a bad hard drive or memory.

It has nothing to do with the filesystem

---

### Post by The Cog on 2007-12-24
Any journalled filesystem should be OK for you. That includes ext3, reiserfs and jfs. I have powered a laptop with reiserfs off several times in the past (pull the mains adapter and remove the battery) without problems when it froze. I guess you were unlucky. 

It is worth noting that there is this last report reboot procedure that may save you next time:
[http://www.ubuntugeek.com/how-to-reboot-your-ubuntu-system-only-if-all-else-fails.html](http://www.ubuntugeek.com/how-to-reboot-your-ubuntu-system-only-if-all-else-fails.html)

---

### Post by shareMenaPeace on 2007-12-24
lowsky

this happend often on my d620 dell notebook for liek 1 year .... np .... now it still happens on asus (random screensaver lockups).... i want to use other filesystem so teh system is more stable to survive this crashes... btw THIS NEVER happend with XP and i have lots of hard resets ...

Well i need to prepare myself now for xmas....it has to wait soooo sad....

---

### Post by shareMenaPeace on 2007-12-24
If someone knows anything what i can try to get my filesystem back please post ....


Why is it that always the worst case scenarios happen :) ??? 


Happy X-Mas!!!!!!!!!!!  <3

---

### Post by philinux on 2007-12-24
Ok so is this it. You had to hard reset and now it wont boot at all.

Can you press esc when grub stage 1.5 comes up. If so then when the list of boot options appears press edit and remove quiet and splash from the boot line. This will let you see the errors as it tries to boot. Then press B to boot up.

Alternative is select recovery mode from the boot options see if that works.

It's important to note down any error messages.

---

### Post by shareMenaPeace on 2007-12-24
recovery want boot, i report back in .... 6  hours or somehting ... thank you!!!!!!!!!!!!!!!!


:popcorn:

:guitar:

---

### Post by shareMenaPeace on 2007-12-24
LOL I  could boot again .... i think it could have todo i had the power switch not connected correct LOl ...sorry for the trouble ;)  Thanx! ...doh i was omg

Happy XMAS!

:guitar:

---

### Post by shareMenaPeace on 2007-12-24
Id liek to add its scary as i could still boot vista, so this means ubuntu uses more power than vista to boot up :)

:popcorn:

---

