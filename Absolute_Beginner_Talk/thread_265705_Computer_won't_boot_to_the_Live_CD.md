---
title: "Computer won't boot to the Live CD"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Ladyfirst on 2006-09-26
[COLOR="DarkRed"][I]~ Hello, 
I just received my "Live CD" today and of course, I was eager to try it. 

I followed the instructions on the CD sleeve and restarted my computer, instead of UBUNTU, Windows XP came on; two more trys and the same results. I then thought that perhaps, I needed to choose to have it boot to the CD, so on the next restart, I pressed F12 and selected F1 to boot to a CD, and I again restarted my computer; and again Windows XP came on... one last try, and my computer froze,(I had to do a hard shut down at the tower)which has brought me here, seeking wisdom and help. 

My computer is a Dimension 2400 P4 2.8
512 RAM and I have XP Home/SP2
(If you need any more information, please ask.)[/I][/COLOR]

---

### Post by whizbaby on 2006-09-26
Please try to change the boot priority in your BIOS setup instead of just selecting from boot menu (perhaps F2 instead of F12, but your bootup screen will say which key to access BIOS). Another thing that spontaneously comes to my mind is:
Did you burn the CD right? I mean did you select *burn cd image* somewhere or did you just copy the .iso file to the CD? The latter won't produce a bootable CD but a data CD.
EDIT:
Oh, do you got the shipped CD?

---

### Post by Ladyfirst on 2006-09-26
[COLOR="DarkRed"][I]It's the shipped Live Cd

[IMG]http://img.photobucket.com/albums/v511/Ladyfirst/ubuntu.jpg[/IMG][/I][/COLOR]

---

### Post by whizbaby on 2006-09-26
Yes, you mentioned *sleeve* before. There's not much possibilities:
(1)your computer does not try to boot from cd (make sure in BIOS)
(2)computer tries to boot but CD is not bootable (will not be the case with shipped CD)
(3)everything is right except your CD/DVD drive can't read this special CD (stars are alligned ...)
So try changing boot priority in BIOS or download the CD and burn it on your own (not fast, 2x,4x or 8x). Anyway, CD standards seem to be a little unprecise: one of my computers has a burner that can't read the disks it burned itself (all other computers can), it has always problems reading some CDs, some others are read without an error. I only say this to show that trying different disks can solve the problem (doesn't have to, though).
If all of this doesn't work please get a knoppix 5 CD
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
and try to boot from that to see if it can boot (this should boot on nearly any (386-like) hardware).

---

### Post by Ladyfirst on 2006-09-26
[COLOR="DarkRed"][I]~ Thank you Whizbaby, for your reply. 

I tried a different CD and changing the boot selection in my BIOS and it still will not work, so perhaps your correct with it possibly being a compatibility problem with my CDROM.

I ordered a Knoppix CD at the same time that I ordered this one, and I'm eagerly awaiting it's delivery...I'm hoping to be more successful with that one, then I've been with this. :) 

Again, thanks! [/I][/COLOR]

---

