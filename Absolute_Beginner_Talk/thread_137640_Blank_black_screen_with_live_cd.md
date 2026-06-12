---
title: "Blank black screen with live cd"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by ipod85210 on 2006-02-28
Hello all, i fear that i may be pushing the limits on patience here, but here goes...

I am an absolute and total newbie to Linux. When i say newbie, i mean, i was pretty much clueless as to what linux was untill last night. But the thought of a free OS fascinated me, so, i downloaded the live cd last night. 

Like someone else posted recently, the downloaded file came up as a winRAR archive, but i ignored it, and used CloneCD to burn the rar file onto a CD.

So, i restart with the CD in the drive, and voila, up pops the Ubuntu screen. I opt to hit the newbie recommended 'enter' so that it boots however it wants, and it scrolls through a whole lot of lines of text, then flashes something about frames, then goes black. Entirely. No prompt, nothing. I leave for a bit, come back, nothing. Any suggestions? I have searched the forums for half an hour now, and cant find something similar.

I'm on an HP zv6000 laptop, with an AMD athlon 3200 processor, ATi radeon express 200mobile. XPpro is the OS i'm using to type this (sadly).

I have an md5 checker, but i dont know what the md5 sum is supposed to say--where can i find the correct checksum?

Thanks for your patience, my whole linux experience flourishes or dies on this...

---

### Post by kaamos on 2006-02-28
My laptop had video issues that caused the same. Resolved by entering
```
live vga=791
```
to the **boot:** screen (where you probably pressed enter). Could be worth a try.

The md5sum should be posted on the site where you downloaded the iso from.  Like at [http://releases.ubuntu.com/5.10/](http://releases.ubuntu.com/5.10/) it is posted as a text file called MD5SUMS

---

### Post by rjwood on 2006-02-28
first question is, at what speed did you burn it at? go slow @4x.

---

### Post by ipod85210 on 2006-02-28
I set it to burn at 8x, i will try the vga fix now. I must say, that was a quick response--i now believe what everyone's said about how great this community is!

Also, i just checked the md5 sums--they match.

Thanks, ill let you know if the vga fix doesnt work!

---

### Post by ipod85210 on 2006-02-28
well, the VGA fix got me farther, but not all the way. I got to see the ubuntu loading screen (with the logo, brown bar, and checklist of what programs are going on) but then it sends me to a black screen which tells me it's loading some other things, then, a blue screen comes up telling me that my X something or other isn't configured correctly. Any ideas?

---

### Post by rjwood on 2006-02-28
[quote=ipod85210]well, the VGA fix got me farther, but not all the way. I got to see the ubuntu loading screen (with the logo, brown bar, and checklist of what programs are going on) but then it sends me to a black screen which tells me it's loading some other things, then, a blue screen comes up telling me that my X something or other isn't configured correctly. Any ideas?[/quote]

```
dpkg-reconfigure xserver-xorg
``` let x read you hardware make sure graphics card driver is correct

---

### Post by kaamos on 2006-02-28
The live cds settings don't apparently work for your video card out of the box.

I'm not sure if this works in the live but usually you can log (try ubuntu/ubuntu if it asks for a pass, don't know) in the terminal where the error leaves you. If there is now login prompt, try pressing ctrl+alt+F1.

Once logged on, you can use the command 
```
sudo dpkg-reconfigure xserver-xorg
```
to try to reconfigure you graphics settings. You could try if the driver "vesa" would work better.

Hope this helps.

EDIT: too slow. :P

---

### Post by ipod85210 on 2006-02-28
hmm...perhaps i wasn't clear--
1st boot from CD: Black nothingness
2nd Boot with vga=791 fix: after ubuntu loading screen (with the brown progress bar), a blue screen popped up with a message concerning the X not being configured (and something about my video card). 
i tried to redo the process to write down exactly what it said, but then i got a new problem on the 3rd boot
3rd boot (and 4th, i did it again just to see if it was a fluke), with vga=791: after the ubuntu loading screen, i get a blank blue screen that looks like my LCD is broken (it's not solid blue, but lots of horiz/vert lines missing or white)--so, there's no login prompt, no prompt at all. I have to manually power off the laptop, i can't even ctrl+alt+del a restart.

So, two questions now: 

Do you mean that i need to put the 'reconfigure' code in from the boot: screen? i.e.:
boot: live vga=791 dpkg-reconfigure xserver-xorg

And--
[QUOTE=kaamos]You could try if the driver "vesa" would work better.

[/QUOTE]
--what? how can i switch drivers from the boot screen?

I really appreciate this, guys. Thanks for helping out a complete n00b.

---

### Post by kaamos on 2006-02-28
Sorry, was being unclear.

You boot with **boot: live vga=791** and after the blue screen pops up with the X error, you should get a login prompt straight away or by pressing control+alt+F1. You can then enter the above command there and you get a config screen for your video settings. That is, if you are not getting the corruption and freeze.

You seem to just have bad luck with the video card compatibility. I'm not really sure how to fix this in a live session, but with a installed system you could input the correct refresh rates or install new drivers from atis website (yep, even without a graphical desktop..).

---

### Post by ipod85210 on 2006-02-28
Well, i guess i need to do a full real install then. I'm just hesitant about partitioning my drive--once i've partitioned it, if i later decide to uninstall, can i unpartition? and how much ought i to allot for ubuntu?

---

