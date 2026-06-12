---
title: "wont boot.. error 15 :S"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Rioku on 2008-02-26
Ok so I installed 7.10 on a USB hdd, I installed the grub loader aswell, so when i set bios to boot from USB i come to the grub loader and then the list of things I can boot into..

When i try to boot Ubuntu... i get error 15, I do not have a clue how to fix this.. can anyone help.?

I did try editing the boot which was hd(0,1) to hd(0,0)  then pressed B too boot... This began the ubuntu logo booting up and i thought ah this might be it...! but it wasnt :(

It runs through the script very slow and shows a constant message of failure to load camera or something (my laptop has a built in cam) and it does this for a while until it eventualy shuts off... so i tried booting back again to find the settings I had changed to be reset back to what they used to be

someone pleaaase help

---

### Post by giga_user_66 on 2008-02-26
Hi there,

Did you remove "splash quiet" from the boot options so you can see where it hangs?

---

### Post by Rioku on 2008-02-26
Hey, Thanks for the reply and a fast one at that, really apreciated. Well no.. actualy I havnt done that, Do i just select and remove it then try booting?

---

### Post by giga_user_66 on 2008-02-26
Just like you edited with 'b' the hd thing. you edit the line that has the number of your kernel in it. If im not mistaken its the second line. you have to use the right arrow to scroll all the way to the back so you see the options, by default they are "ro, quiet, splash" if im right. You have to change those.
I'm waiting for someone to help me with my issue so I saw you post this I figured I might be able to help.

---

### Post by gorgon on 2008-02-26
Hi,


On Grub:
> **Rioku said:**
> 
so i tried booting back again to find the settings I had changed to be reset back to what they used to be

This is normal. You'd have to edit a file that grub reads called menu.lst which is somewhere similar to /boot/grub/menu.lst . Until you change this you have to change (hd0,1) to (hd0,0) manually at starup.

Do you have several ubuntu versions installed?

Did you try booting without your webcam in? What exactly are the last things you see on the screen?

---

### Post by Rioku on 2008-02-26
I have no other OS's other than windows XP installed. The webcam is inbuilt into the laptop so I cant remove it :S, the last thing I saw on the screen was loads of lines of text with something about webcam failure

---

### Post by gorgon on 2008-02-26
As giga_user_66 mention above, remove 'splash' and 'quiet' from the boot options and post the last things you see on the screen here. 'splash' gives you the ubuntu logo on startup and 'quiet' hides all the text.

---

### Post by Rioku on 2008-02-26
I just tried that there and i still get a list of "failed to configure camera" messages that this just keep appearing one after another and dont stop ( I waited 10 mins or a little longer) and still kept doing it.

Gonna give it another go incase I didnt do it right

---

### Post by Rioku on 2008-02-26
Ok guys I did it this time right i think, it showed allot of things then eventualy it ended up back at a failure to configure camera error... :(

I guess this means 7.10 will not work on my laptop...

---

### Post by gorgon on 2008-02-26
hm. sorry I cant help you with this, but it seems strange that it'd stop booting because of a webcam. try searching around with your laptop name and possibly the name of the webcam + ubuntu ..

---

### Post by torgrot on 2008-02-26
You were able to boot, run and install from a live cd and now it won't run?  That is very odd.  Try searching for "install usb hard drive" there was quite a few threads about that.

torgrot

---

### Post by Rioku on 2008-02-26
well.. actualy I installed it on another machine 1st (well to a USB HDD) then placed it in my laptop to boot.

I still get the camera issue when booting the DVD up on the laptop i want to run it on.. but if im only running the LIVE CD it shows the error but eventualy stops and goes into the live CD and lets me play around or whatever. :S

I might try installing 7.04 and then upgrade it within 7.04 to 7.10

---

