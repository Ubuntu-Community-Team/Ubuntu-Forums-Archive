---
title: "Fresh Installation"
date: 2010-02-17
forum: Apple Hardware Users
---

### Post by libertyrida on 2010-02-17
Before I start out, i'd like to point out.. that... yes i've searched, yes i've attempted at the numerous 'fixes.'

Well. I'm trying to run Mac OSX Leopard + Ubuntu on my Macbook White 4,1. I've read multiple user guides, but for some reason it screwed up when I hit the partition button on rEFit. I received the 'gpsync' (sp?) error.
   Like I stated above, I've tried the numerous of fixes, but was fed up with nothing working. I couldn't delete any of my partitions or make them go back to normal... As we speak I'm wiping my hard drive. I would really LOVE to start over FRESH. With Mac OSX, then to install Ubuntu.  
   My point? How can I go about installing Ubuntu on my Macbook without getting the sync error, and screwing up my partitions. ...Yes I read the user guide, and yes.. I did it step by step and still received the errors. I would love to fool around on Ubuntu, but the errors were stopping me. Any help is appreciated...
-Thanks

---

### Post by Tycho59 on 2010-02-17
I would suggest that you try using Boot Camp to create the partition that you want to use for Ubuntu (granted you're running Mac OS X 10.5+).  Install rEFIt, boot from the livecd and proceed with installation from there.  Going with that process has worked out well for me several times.  

Hope this works out well for you.

---

### Post by linuxopjemac on 2010-02-17
maybe this one:
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60) and forget about the windows part

---

### Post by Ken147 on 2010-02-17
I'd go with what Tycho59 suggested, I've done this and it works

---

### Post by dryfire on 2010-02-17
> **Tycho59 said:**
> I would suggest that you try using Boot Camp to create the partition that you want to use for Ubuntu (granted you're running Mac OS X 10.5+).  Install rEFIt, boot from the livecd and proceed with installation from there.  Going with that process has worked out well for me several times.  

Hope this works out well for you.


Boot Camp is for Intel macs.
What do we use for G4 Power PC processors?

---

### Post by linuxopjemac on 2010-02-17
you need a bootloader, yaboot is your answer.

---

### Post by libertyrida on 2010-02-17
Great. I'm doing the partition now, downloading rEFIt, then will boot from my CD. Do---


Forget to hit 'enter' to post this. Ha-ha. 
Well... I have a new problem, I think it's pretty big.

I was following these instructions.. [http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)

When it went to 'bless' the partition or w/e it is under OSX terminal. I restarted my computer. Now it AUTOMATICALLY attempts to load under Ubunto but just gives me the flashing  " _ "  cursor.   How the HELL can I load OSX now? I even hold down alt/option!
HELP!!!

---

### Post by libertyrida on 2010-02-17
I think i'm in really big trouble. I placed the liveCD into my disk drive to see if that worked. But now I cannot get the disk out at all... Like I said in my previous post my macbook starts up, flashes the 'red' ubuntu flash, then cursor blinks. I CANT get my disk out at ALL to try to load from Mac OSX install disk.

--Okay, got the CD out. I think it was something to do with myself following the directions and typing this into terminal.> sudo bless --device /dev/disk0s3 --setBoot --legacy
If i'm not mistaken that means that when I boot my computer is auto loads to Ubunto, not the rEFIt program boot. Maybe? Maybe not?  Hmmm


-edit:  I load my Mac OSX install CD in, turn computer off...turn it on, and hit alt/option, but the CD does not boot. Just goes back to the cursor.

---

### Post by libertyrida on 2010-02-17
I'm pretty sure no one will respond to this or have any idea. Do not follow the stickied posts directions and type that into terminal or else you will **** **** up. I just called mac and they had no idea either. They said it must be a problem with the EFI/RFI chip or something. ****. **** **** ****. **** THIS ****.
****

Yeah, a nice $300 he said it was to base-repair it. ...How the hell can a college student afford that?

---

### Post by mfratus2001 on 2010-02-17
I just installed Ubuntu on an IBook G4. I never worked with Mac, only the early Apple computers, so it was blindly following instructions for me.

I found the CD image here:
[http://cdimage.ubuntu.com/non-ports/ports/releases/9.10/release/](http://cdimage.ubuntu.com/non-ports/ports/releases/9.10/release/)
You have to match up your Mac with exactly the right disk.

I followed this page once I downloaded the install CD:
[https://help.ubuntu.com/9.04/installation-guide/powerpc/ch05s01.html](https://help.ubuntu.com/9.04/installation-guide/powerpc/ch05s01.html)

I had installed a new disk, and the customer-supplied disks were borrowed and not the originals to re-install Mac OS. They did not work.

The Install disk for Ubuntu is fairly automated. Once you get past the first few questions, though, you have to partition the disk. You have to be careful here, as it sounds like you were. But you also have to let the installer do its job. With my install, after it installed the bootloader, it scanned for other systems. It would have found a Mac system and installed choices for booting, just like on my dual-booting PC.

I never had to enter anything from the keyboard except user names and passwords.

The install is lengthy, but most of it is hands-off. I had a bad install disk, so the install halted. I made a new disk, held down the power key until it powered down, then as it powered up, I held the touchpad key. 
The disk was expelled, and I slid in the new one, and the install checked a few things and then picked up where it left off.

Try the install disk from the link above. It was simple and easy. Even a caveman could do it! (TM geico.).

Mike

---

### Post by libertyrida on 2010-02-17
I cannot boot from CD, single user mode, safe mode, or anything. It does the same thing, it boots into a failed / frozen Ubuntu. Uploading a video...

---

### Post by mfratus2001 on 2010-02-17
Instructions say "alt otion" + "enter key" brings up a boot menu.

You have not said what model you have. PowerPC or Intel?
The instructions for the LiveCD install are different than the actual Installation CD. I would use the Installation CD, since that is it's sole purpose.

Mike

---

### Post by libertyrida on 2010-02-17
You're missing my whole point. I already installed Ubuntu, --I was following these directions

[http://ubuntuforums.org/showthread.php?t=1192296](http://ubuntuforums.org/showthread.php?t=1192296)
-I have an Intel
-When I start the comp, it goes to grey screen with no apple logo
-After a minute and a half, it flashes red and and top left it flashes a  -  symbol
-I can't boot up my Mac OS X CD
-I can't go into safe mode
-I can't reset pram

-This happened after i typed in the terminal cmd

---

### Post by libertyrida on 2010-02-17
[[URL=http://s68.photobucket.com/albums/i38/erfshortyboy/Mobile%20Uploads/?action=view&current=0217002039.flv][IMG]http://i68.photobucket.com/albums/i38/erfshortyboy/Mobile%20Uploads/th_0217002039.jpg[/IMG]]("http://s68.photobucket.com/albums/i38/erfshortyboy/Mobile%20Uploads/?action=view&current=0217002039.flv")[/URL]

Please click above to view the video. This is what happens when I start my computer AND when I try to boot from my Mac reinstall disks, or do ANYTHING else.

---

### Post by libertyrida on 2010-02-18
Okay... got off the phone with apple.
TO DO: I'm getting an external hard drive casing, placing my macbook HD into the case, and going to /attempt/ to boot up from HD. If I can't.. it's HD issue and I'll reformat.
                                                               If I can, I need to go in termal and REVERSE THIS COMMAND
sudo bless --device /dev/disk0s3 --setBoot --legacy
It will be this -  "  sudo bless --device /dev/disk0s2 --setBoot  --SOMETHING HERE

The problem is, we BOTH had no idea what Mac calls their own OS. We BOTH know that they call other OS's 'legacy'. Obviously.
If anyone knows how to reverse that command, or know what I can type instead of 'legacy' so I can boot back to OSX.
-You will have a reward-

-Eric.

---

### Post by mfratus2001 on 2010-02-18
I read there was supposed to be a boot choice screen.

---

### Post by mfratus2001 on 2010-02-18
Put your install disc in and hold down the “C” key to boot from it.

from "Mac Stuff" at
[http://macstuff.beachdogs.org/blog/?page_id=33](http://macstuff.beachdogs.org/blog/?page_id=33)

---

### Post by libertyrida on 2010-02-19
I have already tried that. It does not boot from CD, single user mode, safe mode, etc etc etc.

---

### Post by mfratus2001 on 2010-02-21
I noticed that you did not try to hit any keys until it already tried to boot. You have to hold down the C key, or the OPTION key, while powering up:

"I kicked it and kicked it and nothing happened...
You can restart your Mac in one of several modes, depending on what you need to do.

To restart with a CD, insert the CD and restart with the C key held down. This will make the Mac use the system on the CD to start up.

To restart with a different system, hold down the OPTION key while restarting. This will make the Mac give you a choice of OS systems installed on your computer.

If you hold down the MOUSE button or the TRACKPAD button, this will force the computer to eject any CD you may have in the CD drive."

(From [http://www.squidoo.com/crashymac](http://www.squidoo.com/crashymac))

Did you do this? Any of it?

---

### Post by Richardcavell on 2010-02-22
Liberty,

Sorry to hear about the problems you're having.

Firstly, don't go buying new hardware.  There is nothing wrong with your hardware.  The Apple employees are trained to regard these sorts of problems as hardware problems.  They're not.

What I see on that video is a classic case of 'partition not blessed'.  Somehow your partition is not blessed.

I suggest that you find out your partition map.  Boot to OS X (hold down C while cold-booting your Mac.  It has to work.)  Then go to a terminal and use diskutil.  

It would also help if you could join #mac or #ubuntu on IRC while trying to fix it.

Richard

---

