---
title: "Radeon 9250 + Ubuntu 6.06 LiveCD = sad noob"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by NicoleM on 2007-03-24
I want to preface this by saying that I'm rather experienced with windows support/troubleshooting, but I'm a complete newbie to Linux in any form, and these forums seem like the friendliest place to find information so I really commend you guys for creating such a welcoming environment.

I've done a lot of reading lately about Ubuntu and decided it sounded great.  I decided to download and run the LiveCD to mess around for a little while.  I downloaded and burned Ubuntu 6.06 ISO as a bootable CD.  I verified the burn in windows and also did the disc check in the boot options and can verify that my issue is not related to a disc problem.  I figured I'd get that basic check out of the way first.

I tried starting ubuntu both in normal mode and with the safe graphics options and received the same error in each scenario.  I'll have to start the process over again as I didn't get a chance to write it down, but it happened as it was supposed to be "loading gnome desktop" and the error message referenced loading gnome. there was also an error regarding the X-server environment.  I know specifics are helpful when it comes to error messages, so I'll update with that info as soon as I can.

I'm currently using a ATI Radeon 9250 Pro PCI video card (full specs below).  While doing some searches both on this forum and on google I came across a few possibilities and was wondering if any sounded valid for my situation.  One was that the default ATI drivers shipped with Ubuntu are a little on the wacky side and you have to modify the boot (or install?) line to load a different driver: [http://ubuntuforums.org/showthread.php?t=389278](http://ubuntuforums.org/showthread.php?t=389278) (specifically post #7)

The other issue i came across was that this version of Ubuntu is not compatible with the Radeon 9250 PRO video card without a patch: [https://launchpad.net/ubuntu/+source/linux-meta/+bug/31527](https://launchpad.net/ubuntu/+source/linux-meta/+bug/31527)


Before anyone recommends the alternative install ISO, I want to make it clear that I am not interested in installing Ubuntu at the current point in time.  I need to purchase a new hard drive and am seriously comteplating dual booting Ubuntu and XP once I get the drive until I can train myself to become comfortable with Linux, but my main goal at the moment was to mess around with the LiveCD to get an idea of what I was getting myself into.  If you think the alternative CD would benefit me, however, I will mark it down as somethign to try when i receive my new hard drive.

is it possible to pursue any of the solutions I've come across in a Live environment (in other words without an install) or do I need to bite the bullet and fix the problems after the install?  I can usually catch on relatively quickly, but if the links I've provided don't pertain to my situation please let me know.

system specs
pentium 4  2.0 ghz processor
1 GB RAM
RADEON 9250 Pro
2x Seagate Barracuda 300GB IDE hard drives
BenQ 1640 DVD writer
BenQ 1655 DVD writer

if you guys need any more information I'll try my best to provide any and everything.  I'm going to pop the cd back in and hopefully be able to document the exact error in some more detail.

Thanks for your time
-N

---

### Post by lamalex on 2007-03-24
why don't you just try edgy? I have had better luck with edgy and hardware.

---

### Post by NicoleM on 2007-03-24
> **Iamalex said:**
> why don't you just try edgy? I have had better luck with edgy and hardware.

Thanks for your quick reply.  I'll download it and give it a shot.  I've been reading so much about Linux and specifically Ubuntu lately that I can't remember why I chose the 6.06 version, but I'm sure there was a good reason behind it...maybe :)

I'll let you know how it goes with Edgy.

---

### Post by NicoleM on 2007-03-25
ok here's a series of photos of my (mis)adventures with Edgy.  This seems to be the same issues I encountered previously.

not sure what this site's policy is on images as I'm new here, but I'm hosting them on photobucket and just linking them as they're rather large in size.  If you'd prefer I embed them in the message let me know and I'll edit the post.  Also, I apologize for not being more descriptive with the pictures, but it's mostly Greek to me at this stage in my linux experience.

Booted from the CD and chose the "start or install ubuntu" option.  Things seemed to be progressing, then I received the following errors for about 2 and a half minutes straight:
[http://i71.photobucket.com/albums/i136/beefaroni5/1.png](http://i71.photobucket.com/albums/i136/beefaroni5/1.png)

i decided to let it do it's thing to see what would happen.  an [OK] came up next to it and ubuntu moved on to it's next few tasks that completed without issue.

Then X-server disaster strikes:
[http://i71.photobucket.com/albums/i136/beefaroni5/2.png](http://i71.photobucket.com/albums/i136/beefaroni5/2.png)

I press enter to view more info and get:
[http://i71.photobucket.com/albums/i136/beefaroni5/3.png](http://i71.photobucket.com/albums/i136/beefaroni5/3.png)

at this point the only key that seemed responsive was ESC and I was presented with the following message:
[http://i71.photobucket.com/albums/i136/beefaroni5/4.png](http://i71.photobucket.com/albums/i136/beefaroni5/4.png)

at this point I was back at the black screen.  all keys were functional at this point though since I don't know any nifty linux miracles I simply rebooted and came back here to cry

same specs as original post, but this occured when trying to run Edgy from the LiveCD.  The errors were the same under 6.06

is this graphics driver related like I suspected or is it something totally different?  and my main question still stands...is this fixable to the point where I can run a LiveCD or would I need to install something before I can mess around with a fix.

Thanks
-N

---

### Post by NicoleM on 2007-03-25
after some more digging it seems as though I've found a possible problem with one of my questions.

I guess you can't install if you can't load the liveCD...I hadn't realized that you aren't presented with the install option until the LiveCD was loaded.  so i guess my question about having to install to fix the issue is null at this point.

I've found this thread [http://ubuntuforums.org/showthread.php?t=190133](http://ubuntuforums.org/showthread.php?t=190133) and the instructions seem pretty noob friendly so i'm going to give that a shot.

i figured I'd bump this thread before I go to bed in case i'm off base in my attempts someone can set me straight :)

looking forward to hearing any input especially from users with ATI cards on whether this headache comes up often or if it's a one-time fix then I won't have to worry about it.

-N

---

### Post by wj32 on 2007-03-25
> **NicoleM said:**
> ok here's a series of photos of my (mis)adventures with Edgy.  This seems to be the same issues I encountered previously.

not sure what this site's policy is on images as I'm new here, but I'm hosting them on photobucket and just linking them as they're rather large in size.  If you'd prefer I embed them in the message let me know and I'll edit the post.  Also, I apologize for not being more descriptive with the pictures, but it's mostly Greek to me at this stage in my linux experience.

Booted from the CD and chose the "start or install ubuntu" option.  Things seemed to be progressing, then I received the following errors for about 2 and a half minutes straight:
[http://i71.photobucket.com/albums/i136/beefaroni5/1.png](http://i71.photobucket.com/albums/i136/beefaroni5/1.png)

i decided to let it do it's thing to see what would happen.  an [OK] came up next to it and ubuntu moved on to it's next few tasks that completed without issue.

Then X-server disaster strikes:
[http://i71.photobucket.com/albums/i136/beefaroni5/2.png](http://i71.photobucket.com/albums/i136/beefaroni5/2.png)

I press enter to view more info and get:
[http://i71.photobucket.com/albums/i136/beefaroni5/3.png](http://i71.photobucket.com/albums/i136/beefaroni5/3.png)

at this point the only key that seemed responsive was ESC and I was presented with the following message:
[http://i71.photobucket.com/albums/i136/beefaroni5/4.png](http://i71.photobucket.com/albums/i136/beefaroni5/4.png)

at this point I was back at the black screen.  all keys were functional at this point though since I don't know any nifty linux miracles I simply rebooted and came back here to cry

same specs as original post, but this occured when trying to run Edgy from the LiveCD.  The errors were the same under 6.06

is this graphics driver related like I suspected or is it something totally different?  and my main question still stands...is this fixable to the point where I can run a LiveCD or would I need to install something before I can mess around with a fix.

Thanks
-N
The first error indicates that there's bad blocks on your hard drive (aka, your hard drive is stuffed).

---

### Post by NicoleM on 2007-03-25
thanks for the insight on the first photo. While I too thought it looked like some sort of drive error, i thought the livecd would not make any changes to my hard drives.  all my hard drives are ntfs anyway so wouldn't ubuntu have problems with that?

i can verify for a fact that none of my drives are full and they SHOULDN'T have errors but as far as errors go I guess anything is possible.

regardless, how do i tell which hard drive it's trying to write to so i can find the problem if i do have some sort of drive error?  I have 3 hard drives connected at the moment.  I wouldn't suspect it's touching my external drive which leaves my master and slave drives.

also, on a separate note i attempted to use different display drivers using the link i posted in my previous post as a guide, but when i accessed /etc/x11/xorg.conf it opened in nano but it was blank.  not sure what to make of that either.

---

### Post by lamalex on 2007-03-25
it really shouldnt be touching any hard drive since its a livecd, it could mean ram issues. try running the memory check... another nice cure all * not always * is to add apic=off noapic to the boot flags. before you hit enter to start or install ubuntu hit f6 and add those two flags. that fixes a lot of livecd issues.

---

### Post by kittyhawk63 on 2007-03-25
At what speed did you burn the ISO? It should not have been burned at a higher speed than 4X. I recommend that you not use the alternative disk. ATI cards are not directly supported by Ubuntu. They need to be updated by installing a fix from the internet.

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by Bartender on 2007-03-25
I had nothing but trouble with an ATI 9200SE.  Bought a comparable Nvidia card ($35 or so) and all the problems went away

---

### Post by NicoleM on 2007-03-25
> **Iamalex said:**
> it really shouldnt be touching any hard drive since its a livecd, it could mean ram issues. try running the memory check... another nice cure all * not always * is to add apic=off noapic to the boot flags. before you hit enter to start or install ubuntu hit f6 and add those two flags. that fixes a lot of livecd issues.

memory checked out fine.  I'll try adding those flags in the morning and see how it goes. thanks again.


@kitty thanks for the recommendations.  the iso was burned at 4x and verified both in windows and with the "check cd" option at the boot screen.  I understand i can dl a separate driver, but i'm not installing anything at the moment.  My goal right now is to get the liveCD working so I can at least play around with the OS before I make the installation commitment.  unless i'm missing something, i don't think it's possible to download a driver and use that driver when running the livecd...or am I mistaken?

@ bartender thanks for the firsthand experience...I was afraid I'd hear something like that.  i'm tight on cash at the moment (recent college grad not yet employed and neck deep in student loans) so a new video card isn't really in my future.  I actually recently upgraded my video card.  my mobo is rather old so i need a PCI card and the ATI I purchased was infinitely better than the nvidia ones in the price range (and a few price ranges above as well)

I appreciate everyone's help.  I'll report back once I try modifying the boot parameters as suggested.  in the meantime I think it's time for a visit to the relatives to try the LiveCD on a not-ATI card system to at least decide if i want to do all the legwork involved in getting it to work for me.

---

### Post by john.nicholls on 2007-03-25
I installed an ATI 9250 last year and it works perfectly with the standard drivers supplied by Ubuntu on 6.06 and 6.10 without any fiddling.

---

### Post by kittyhawk63 on 2007-03-25
> **Bartender said:**
> I had nothing but trouble with an ATI 9200SE.  Bought a comparable Nvidia card ($35 or so) and all the problems went away

Bartender,
Other than possible screen freezes, what other problems did you experience with your 9200SE? Were you able to get 3D to work?
kh

---

### Post by kittyhawk63 on 2007-03-25
NicoleM wrote:
I appreciate everyone's help.  I'll report back once I try modifying the boot parameters as suggested.  in the meantime I think it's time for a visit to the relatives to try the LiveCD on a not-ATI card system to at least decide if i want to do all the legwork involved in getting it to work for me.[/quote]

You won't be sorry for taking the time to get Linux to work for you. I've been a Windows' user for almost twenty years. I was never happy with it and all its bugs and hacker attacks, but it is all I knew. I am completley sold on Linux. I only use Windows when I need something that is not "yet" availabe through Linux with a comparable alternative. BTW, you can run certain Windows' programs through Linux. Check out "Crossover".
kh

---

### Post by Talon2 on 2007-03-25
> **NicoleM said:**
> 

looking forward to hearing any input especially from users with ATI cards on whether this headache comes up often or if it's a one-time fix then I won't have to worry about it.

-N

I'm running multiple Radeon cards here (9250 and 9600).  Edgy and Fiesty detect and setup the open source ati driver which works well with these cards.  A little tweaking is needed to get maximum performance for the new 3d Desktop effects in Fiesty.  I'd say chances are that your problem is not related to the 9250.

---

### Post by NicoleM on 2007-03-25
thanks for all the help and encouragement everyone.  this is starting to get frustrating, but linux has been something I've wanted to tackle for a while, and getting the darn livecd to work is the first step i guess.

I was finally able to get into the xorg.conf file and I found that instead of detecting my ATI Radeon PCI card its been detecting my intel on-board video card (which is disabled in BIOS no less)

based on the last few posts that say yes, linux is possible with my card, i'm beginning to think there's some sort of conflict in what's being detected.

at this point I'm nearly sure it's a video card/driver issue based on similarities in my errors with other posts i've read in not being able to start X, but I now think it's maybe an issue of confusion or detection of the two cards rather than an incompatibility.

I've double and triple checked the bios and the ATI card is set at primary.  there are really no other video options in my bios (and no bios updates available).

I guess now I'd like to know how I get it to detect my Radeon card and NOT my on board graphics.

if it's easier to get it to detect the other way around (on board rather than PCI) I'm open to suggestions, but I do play some games and would rather utilize the better video card.  The eventual goal, although it seems pretty far down the road at this point, is to wean myself off of a windows dependency.  based on my research into program equivalencies and the ability to run World of Warcraft on a linux box, I'm thinking it might be easier than I anticipated (once I actuallyl get it working that is!)

after reading about ATI - Linux history I was starting to get discouraged, but as long as you guys are here to give suggestions, I'm willing to try just about anything :)

also, I tried IamAlex's suggestion of adding apic=off noapic to the boot flags, and still had no luck :(  I still got the "yo, we're not letting you have a GUI because X hates you" message

---

### Post by NicoleM on 2007-03-25
also for the record, it's neither me nor my disc that are cursed.  I was able to boot from the LiveCD without running into X errors on my brother's computer.  unfortunately I can't really narrow down the issue since he doesn't have any onboard video to mess around with and his card is a Nividia of some sort and using "nv" drivers.

---

### Post by NicoleM on 2007-03-25
I'm now posting from the LiveCD!!!!!!!!!

once I finally figured out what the problem was thanks to all the help from here, I was led to a number of sites with suggestions on how to fix it.  I'll try to outline what I did so others can benefit from it.  If you need me to clarify anything please ask.  I'm still a noob and my terminology might not be 100% accurate.

- I ran the LiveCD until I got the error and it stopped.  at this point i could type in commands

- i typed *lspci* (it might have been *lspci -v*) although i honestly don't know what the -v modifier does yet but you can try both until you see what you need.

- what you're looking for in this list is the Bus ID of your PCI video card.  once you find it, write this down.  mine was *01:09.0* although i'm sure your setup will vary

- then i accessed the config files in a text editor *sudo nano /etc/X11/xorg.conf*
(that first "X" is caps...pay attention to that!)

- find the section that references the video card and change the Bus ID to the one you just wrote down.

- in the driver section change to "ATI" this will likely work for many ati cards, but I make no guarantees.  this is what I used and worked for me

- I did NOT change the identification or description of the card itself.  nto sure if that makes a difference.

- exit and save changes then type *start x*

I hope this works for chris87 as well as his problem seemed identical to mine.  definitely post back and let us know.

Thanks again to everyone that took the time to comment on this thread.  as soon as I figure out how, i'll mark it as resolved :)

---

