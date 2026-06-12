---
title: "GRUB hates my XP"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Sspankyy on 2007-07-23
Hey,
     I recently decided to install XP on one of my systems along side Ubuntu, but didn't want to reinstall Ubuntu.  So, to accomplish that, I decided to unplug 2 of my Hard Drives, and install it on the 3rd...   It worked fine....  Then I plugged in the other drives, and started up, Ubuntu popped up without a problem... Just as I expected...  So, I edited the Boot Loader, adding XP, and rebooted.

    The Boot Loader Popped up as I had hoped, and I had all of the options I should have..  So, I told it to start in XP, the screen blanked for a fraction of a second, then the words "Starting up ..." appeared in the top right hand corner... I was happy, for about 2 seconds, then I noticed that those words didn't go away, and it didn't "Start up", It just froze... 

    So I turned it off, thinking that maybe something happened to XP,  Unplugged the 2 drives I use for Ubuntu, started up, and XP started fine...  I'm now kinda lost... It "Should" work as far as I know..  I even went as far as to compare /boot/grub/menu.lst  against the one on my laptop (dual boot) and everything seems to be in order..  What am I doing wrong?

Scott

---

### Post by Orochi on 2007-07-23
Post your grub menu.lst here, it's hard to figure out what might be wrong without seeing it.

---

### Post by subaru on 2007-07-23
might i suggest super grub disk  . . . .

---

### Post by davidjmayo on 2007-07-23
> **Sspankyy said:**
> Hey,
     I recently decided to install XP on one of my systems along side Ubuntu, but didn't want to reinstall Ubuntu.  So, to accomplish that, **I decided to unplug 2 of my Hard Drives, and install it on the 3rd.**..   It worked fine....  Then I plugged in the other drives, and started up, Ubuntu popped up without a problem... Just as I expected...  So, I edited the Boot Loader, adding XP, and rebooted.

    The Boot Loader Popped up as I had hoped, and I had all of the options I should have..  So, I told it to start in XP, the screen blanked for a fraction of a second, then the words "Starting up ..." appeared in the top right hand corner... I was happy, for about 2 seconds, then I noticed that those words didn't go away, and it didn't "Start up", It just froze... 

    So I turned it off, thinking that maybe something happened to XP,  **Unplugged the 2 drives I use for Ubuntu, started up, and XP started fine.**..  I'm now kinda lost... It "Should" work as far as I know..  I even went as far as to compare /boot/grub/menu.lst  against the one on my laptop (dual boot) and everything seems to be in order..  What am I doing wrong?

Scott

Unless I get this wrong there will be nothing in /boot/grub/menu.list as the ubuntu disks weren't connected in the pc.
I haven't had to use Super Grub but heard it's very good. Will it be able to pick up the XP MBR which is on disk 3??

Scott: This is not a fix but it should help others to help you. I don't know the solution.

---

### Post by Orochi on 2007-07-23
> **davidjmayo said:**
> Unless I get this wrong there will be nothing in /boot/grub/menu.list as the ubuntu disks weren't connected in the pc.

He said he edited menu.lst after plugging the drives back in.

I suspect your problem is that in menu.lst your entries are pointing to the wrong drives or partition numbers. You said you compared your menu.lst against the one on your laptop, but the drive and partition numbers would be different for your desktop. If you didn't change these, then that is probably why your XP boot isn't working.

---

### Post by kittyhawk63 on 2007-07-23
[quote=Sspankyy;3067549]Hey,
     I recently decided to install XP on one of my systems along side Ubuntu, but didn't want to reinstall Ubuntu.  So, to accomplish that, I decided to unplug 2 of my Hard Drives, and install it on the 3rd...   It worked fine....  Then I plugged in the other drives, and started up, Ubuntu popped up without a problem... Just as I expected...  So, I edited the Boot Loader, adding XP, and rebooted.

I suggest you download a copy of Super Grub, burn it onto a CD and boot to it. It fixed by Grub problem. It could just fix yours. It is easy to use. Just read carefully and follow the instructions. It has a nice GUI. Hope you get your Grub working.
kh

---

### Post by MQMike on 2007-07-23
It does sound like the hard drive reference (to your new XP) might be wrong, as Orochi suggested above.

Your Windows boot entry in menu.lst will be something like:

title Windows XP on the third HD or something
rootnoverify (hd?,0)
chainloader +1


Now you need to find out how BIOS sees the drive where you put your new XP.
GRUB sees drives the same way BIOS does.
GRUB numbers drives starting from zero and it numbers partitions starting from zero.
It does seem that Windows prefers to be on the “first” drive to boot, but, ignoring that, I’d first try to edit your menu.lst again for the correct (hd?, 0).

At a GRUB prompt you can investigate your drives by typing geometry (hd0) (or (hd1), or (hd2)) to see which drive has what on it.  (You get a GRUB prompt, grub>, by typing sudo grub at a command line in a Terminal.)

---

### Post by Sspankyy on 2007-07-23
I do have it pointing to the correct hard drive and partition... after a couple trials, I found the right one... When it was going to the wrong drive, it would just report a problem, telling me that either there was no operating system on that disk, or that it didn't exist,  when i got the right one, it told me that it was starting...  then froze...

 Scott

---

### Post by MQMike on 2007-07-23
I think you might need to do a map-dance in your menu.lst, in the boot menu for the new XP.
Windows likes to be on the first hard drive, and you can perform a virtual switch of hard drives using the map command in menu.lst.

GRUB manual (pdf):  GRUB, GNU GRUB Manual 0.97 at:  [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
(free, quick download, say in pdf or whatever you are used to)
See Section 4.2.6  DOS/Windows.

It’s worth a try.  I’ve gotten the same thing you got many times:    Starting …. Freeze, 
and every time, it calls for a map-dance because of drives shifting or Windows not on first.

Again, you must use the correct hdx designation for that XP drive, and the boot menu will be like:

title              Microsoft Windows XP
map             (hd0)  (hdx)     
map             (hdx)  (hd0)     
rootnoverify (hdx,0)                   # rootnoverify ensures no attempt is made to mount windows
makeactive
chainloader +1

---

### Post by nbeerbower on 2007-07-24
I'm glad I'm not alone. This happened to me too. I think if myabe I remove Ubuntu I can use Windows again..

---

### Post by Sspankyy on 2007-07-24
Wow!

   It works!  Thank you MQMike,  I did the "Map Dance", and It works Flawlessly!   That just saved me a LOT of headaches....   

    Scott

I just can't wait for the day when I can totally get rid of Windoze..... Gimme some time... It'll happen...

---

### Post by MQMike on 2007-07-24
Nbeerbower, 
You should post your situation and see if we can all get you going.  Most (all?) dual-boot cases can be fixed so you can have a choice to boot either your XP or Ubuntu.  This particular case is only somewhat complicated by the fact that Windows was installed * after * Ubuntu AND on a non-first hard drive.  Blame that on Windows -- it does not like to be non-first in terms of booting.  If you have XP existing on a drive (first partition -- the normal Windows case), and you install Ubuntu on that drive, it’s a piece of cake getting it to boot.  (It’s also easy if you have two IDEs or two or more SATAs; if you have a mixture or an external HD, it may take a few tweaks).  (Here’s my very basic, easy-to-use How-To if you are simply adding Ubuntu to your XP drive or a second drive:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0) )

---

### Post by MQMike on 2007-07-24
Sspankyy – That’s great!  Congratulations on your persistence and obviously your ability to get down on these details.  Windows was the problem – in terms of booting, it likes to be on the first bootable HD (as seen by BIOS).

For your future reference, I want to mention something for you to keep in mind.  The two maps were:

map (hd0) (hdx) 
map (hdx) (hd0)

I’ve never figured out why the second one is needed, I have often commented it out and things still work, like:
#   map (hdx) (hd0)

There must be some subtle reason for it, or maybe there are certain applications where it’s needed.
However, as we all know very well, if it ain’t broke, don’t try to fix it!  Yours works as is!

- - - - - - - - - -

A note about drive shifting and fixing Windows on non-first hard drive:
I’m going to mention one more thing about this map-dance thing, which in on-topic here.  I learned this from adrian15 (owner, Super Grub Disk project).  It comes up if you want to put GRUB or say GParted on a thumb drive (USB Flash Drive, UFD), where again, the UFD shows up as (hd0) in BIOS when  the UFD is plugged in, thus bumping the XP drive to a non-first position, and problems occur (like you had with that message Starting…).  Here’s a How-To where I did got the thumb drive to boot using a new usbshift command included with the new SGD USB; and the How-To also references where I did it with map commands.  I’m including this because it pretty much covers a lot of the material most of us would ever need about these map dances with Legacy GRUB (I hope GRUB2 includes adrian15’s usbshift!).  That would be the following:
How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)

- - - - - - - - - -

Again, way to go, Scott, and glad you’re back on the road here!

--Mike

---

### Post by MQMike on 2007-07-24
The following solution is added to my basic GRUB how-to:

Install Windows XP after K/Ubuntu, and assume
You install XP to a non-first hard drive

(@ How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(scroll down to July 24, 2007))

Includes basically what we used here:
An explanation and example of the map command (editing the GRUB boot menu to include the map dance) and general drive-shifting issues is discussed.

(This was motivated by this thread and may be a handy reference for helping others with the same setup.)

---

### Post by kittyhawk63 on 2007-07-25
Computers can be like people...different strokes for different folks. I always have my Linux set as master, while Windows is set as slave. The only time I set Windows as master is when I am installing it to my hard drive. I then set it as slave and the HDD I want to install Linux, I set as master. I then install Linux and it recognizes my Windows HDD. When it writes Grub, it set Linux as my default boot OS.
kh

---

