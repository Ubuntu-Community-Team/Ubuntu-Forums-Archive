---
title: "Live CD won't boot on an iMac G3"
date: 2006-10-08
forum: Apple PPC Users
---

### Post by EricJD on 2006-10-08
Hi,

I just downloaded and burned the PPC version of Dapper.

I put it in my iMac G3 and restarted, holding down the C key on bootup. It booted like it should, but then the screen just went black and I heard the bootup sound. Nothing at all appears on the screen.

What's going on?

---

### Post by markd1216 on 2006-10-08
Do a search on some of the words in your post subject and you will find a host of similar difficulties.  I was faced with this problem and found the solution -- I wish I remembered the post and poster for credit, but here is the crux of the fix I printed out for reference. The issue seems to be one of the CD not having the correct display settings.  

When you eventually come to the black screen, the boot is completed you just can't see the desktop.  
Hit control-option-F1   > may take a couple of tries  > will get you a terminal screen
Type:  sudo nano/etc/X11/xorg.conf  >return
Make these edits.  I was not very adept, but using my arrow cursors I was able to navigate OK
   Go to the Monitors section and modify HorizSync to 60-60 and VertRefresh to 75-117
   In the Modules section disable DRI by putting a hash mark (#) at the beginning of the line containing load dri

When done hit control-O  > return (writes to the edited file) then, 
Hit control-X  > to exit nano back to command line, then
Type sudo killall -HUP gdm

I also found a similer fix at:
[http://ubuntuforums.org/showthread.php?t=212723&highlight=iMac+G3+boot](http://ubuntuforums.org/showthread.php?t=212723&highlight=iMac+G3+boot)

which was similar but did have some different numbers for the edit -- but what I typed out worked for me.  Be careful to type carefully. Thanks again to the mystery poster.     Mark

---

### Post by markd1216 on 2006-10-08
As I looked over my post, please note that the ">return" is not to be typed.  After you type out the command the >return just means to hit return to move on.  Hope this didn't throuw you off.

Mark

---

### Post by Aspirin on 2006-10-08
one thing you could also do (i went through this a few days ago) -

download the "alternate install" iso. if you dont necessarily need the live cd and just wanna install ubuntu, try the alternate installer. it should work, if that's what youre looking for.

---

### Post by EricJD on 2006-10-08
Thanks guys, the instructions I found [here]("http://ubuntuforums.org/showthread.php?t=212723") worked wonderfully. :D

---

