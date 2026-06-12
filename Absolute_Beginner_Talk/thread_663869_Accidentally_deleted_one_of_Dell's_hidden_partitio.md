---
title: "Accidentally deleted one of Dell's hidden partitions..."
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by smacattack on 2008-01-10
In a moment of stupidity, I deleted one of the hidden partitions that shipped with my Dell Dimension 4600 and now I can't boot anything...  (searching through the Dell forums, I now believe the partition I deleted (it was about 47MB) had the MBR on it?

I've tried re-installing Gutsy on a partition but no luck... (just says 'cannot boot, press F1 to retry)

In using the live CD's, I can see that both my primary and secondary hard drives are intact, I just need to restore the MBR i think. Any ideas? (i don't think I can find my original Dell CD's)

---

### Post by ajgreeny on 2008-01-10
Try the supergrub CD, which ought to find all your OSs and allow you to boot them, or just use the ubuntu liveCD and reinstall grub wherever you want it.
Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

Best of luck, I hope it works for you.

---

### Post by Crumpets and Jam on 2008-01-10
> **smacattack said:**
> In a moment of stupidity, I deleted one of the hidden partitions that shipped with my Dell Dimension 4600 and now I can't boot anything...  (searching through the Dell forums, I now believe the partition I deleted (it was about 47MB) had the MBR on it?

I've tried re-installing Gutsy on a partition but no luck... (just says 'cannot boot, press F1 to retry)

In using the live CD's, I can see that both my primary and secondary hard drives are intact, I just need to restore the MBR i think. Any ideas? (i don't think I can find my original Dell CD's)

I think that hidden Dell partition contained a image of what your PC was like when you bought it. Booting into this partition would allow you to 'reset' your operating system to how it was when you got it out of the box. At least, this is what I think it is. I had something similar on my Dell 5150 desktop.

This is what I suggest you do. Download a ISO of the latest Ubuntu release. Burn it to a disk and boot into it. Install the operating system and when you come to the partition bit select "Guided - Use Entire Disk". After the installation is complete, you should be able to restart and boot into Ubuntu.

Get in contact with Dell. I used their e-mail service and they were way more helpful than the people on the phone. Explain to them that you want to install Linux on your hard drive and you didn't get any recovery CDs with your PC encase you ever need to install Windows again. I got a response in about 2 days. The guy wanted my address and a contact number. He said that the CDs would arrive in about 5 - 7 days. I didn't have to pay for shipment or anything.

I hope that I have helped you a little bit.

---

### Post by nowshining on 2008-01-10
how old is ur Dell 4600? 

anyway an answer to u Q, yeah it's prob. XP in the hidden partition, if u don't want XP or whatever OS they shipping with that hidden partition then don't worry about it, MBR shouldn't be a problem either once u install another OS. :)

---

### Post by smacattack on 2008-01-10
thanks for all of the responses!

I have tried the guided installation of Gutsy but when I restart it just says 'strike F1 to retry, F2 to run setup utility'. So then I formatted, installed winXP and when I restarted... same message...

So anyways, when I go into the BIOS, and i check the hard drive boot sequence, it just says 1._____ <it's just blank> and 2. hard drive- not installed. 

The odd thing is that I am able to access my 2 hard drives right now on the LiveCD, as I'm typing... and I'm able to install OS's so how can it be that my computer isn't able to boot to them?

What a mess....I guess I'll try that supergrubCD... any other input would be greatly appreciated.

---

### Post by nowshining on 2008-01-10
what is ur BIOS version? A12 is the latest version?

AS for the HArd Drive thing, that's probably the problem, I don't know why it is happening, maybe u got an older BIOS as stated above and need to upgrade it. I also have a 4600(i) (i = integrated video card :)   ) A12 bios and mine is working fine?

---

### Post by smacattack on 2008-01-10
I'll reboot and have a look now, I'm not sure if it's A12. Quite honestly I'm never updated it. In the event it's not updated, how might I update it? I know I can find it on the Dell website or whatever, so I guess I just put it on a floppy? or a CD?

---

### Post by Don1500 on 2008-01-10
if you have a floppy you should put the new Bios file on that, then there are specific instructions for reloading your bios. You have to let the computer know you are doing this before you boot. In a desktop there is a jumper on the Mother board to remove. I don't know about a laptop. Read the Dell site.

---

### Post by smacattack on 2008-01-10
okay thanks I'll have a check now at my BIOS version and the Dell Site. (Things take me a while to do haha, cause I have to keep loading from the liveCD to get on the net.).

---

### Post by nowshining on 2008-01-10
u can do it via flash dirve or CD, :P There is a thread on how do it somewhere on the forums I think as I forgot how I did it from a flash drive.

u can take a look at this tho [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

in the meantime have u opened up the computer and made the hard drive is connected the computer, make sure there are no loose cables, etc..?? Look in the computer manual and consult it for more info.

---

### Post by Don1500 on 2008-01-10
No worries mate, I did it the first time I screwed the bios and I didn't have a place to get this info.

---

### Post by smacattack on 2008-01-10
ya so I checked my BIOS version. It's A10 so I'll definitely update it to A12. Thanks for that tip once again...

As for the hard drives, I know they are fine cause I can access them now off the liveCD so I'm sure that's not it.

I am going to give the USB option a shot... I don't know I'f id be able to find a floppy disk haha. Thanks again for all the help I hope I can get this fixed in the next hour or so. Thank god for live CD's...

---

### Post by nowshining on 2008-01-10
hehe, ur welcome :)

---

