---
title: "New to Ubuntu, did I just kill my Win XP install?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by everyoshatesme on 2008-01-09
Ok, so I have the following drive setup:

2x 500gb running win XP in raid-0.

I also had one 320gb drive running Vista Home Premium, not on the raid.  I used to just hit esc during my bios post to select if I wanted to run on the raid (xp) or on the solo drive (vista)

Long story short, the 320 gb drive goes out.  I manage to salvage data off of it into my raid-0, and RMA'ed the drive.

The replacement Hdd arrived today.  Not having the Vista disc handy, and being curious about Ubuntu and Linux in general, decided to install it instead.

After burning the .iso to a dvd, I booted from it, and when given the installation option I selected the new 320gb drive to install to.  I took out the dvd once it installed, rebooted, and selected the 320gb drive in my bios.

Nothing happens...  So I reboot once more.  nothing,  So i reboot one more time, this time selecting my raid-0 setup, expecting to see the XP splash screen.  Wait what?  Now Ubuntu suddenly loads.

Uh, so did I just somehow screw myself over here and am now unable to boot into Windows XP?  I thought Ubuntu would play nice after hearing favorable things about it, but this is worse than Vista so far, at least it stuck to it's own hdd quietly.

If anyone can help point me in the right direction here, thank you!  This is the first time I've ever touched Ubuntu, what a beginning.  At least my networking card seems to work.

---

### Post by NovaAesa on 2008-01-09
When you booted into the raid setup, did it get to a screen where you could select operating systems (called the GRUB screen) before it loaded Ubuntu?

---

### Post by everyoshatesme on 2008-01-09
> **NovaAesa said:**
> When you booted into the raid setup, did it get to a screen where you could select operating systems (called the GRUB screen) before it loaded Ubuntu?


Well, actually what I did was pop in the new 320gb drive in place of the old one, and powered on.

I popped in the Ubuntu dvd and hit esc.  My boot option menu showed up, and i selected boot from dvd.  Ubuntu loaded, and I selected install.

I got a screen which offered options like this:

1. hdd modelnumber 500gb
2. hdd modelnumber 320gb
3. hdd modelnumber 500gb.

I selected #2, and let it finish installing.  Once finished, I popped the DVD out, rebooted, hit esc and selected the 320gb drive.  Nothing happened.  I tried rebooting a 2nd time, same results.  The Bios appeared to finish doing it's part, but no splash screen or anything.

So I rebooted once more, hit esc, chose my raid-0, and suddenly I'm loaded into ubuntu, instead of XP like I had expected.  I just rebooted to see if any special menu loaded, but I didn't notice anything.

Thanks for your help!

---

### Post by NovaAesa on 2008-01-09
Okay, I'm not really sure about this (some one else more knowledgable than me might come along), but I think the best thing to do at this stage would be to take out the 320GB drive and try booting from the raids again. This will definately tell us if your XP is gone or not. Once we know if it's gone or not, we can decide what to do next.

---

### Post by everyoshatesme on 2008-01-09
> **NovaAesa said:**
> Okay, I'm not really sure about this (some one else more knowledgable than me might come along), but I think the best thing to do at this stage would be to take out the 320GB drive and try booting from the raids again. This will definately tell us if your XP is gone or not. Once we know if it's gone or not, we can decide what to do next.

Ok I unplugged the 320GB HDD and saw this:

[IMG]http://img.photobucket.com/albums/v201/christos/DSC06904.jpg[/IMG]

So it appears to have at least some of itself on the 320gb drive.

If I open the 'computer' section, it appears to see the raid as it's own entity.

[IMG]http://img.photobucket.com/albums/v201/christos/thefuck.png[/IMG]

but doesn't appear to let me access it.

---

### Post by zabien1970 on 2008-01-09
Out of curiosity why does it  say 'boot from cd' in your screenshot?  Is the live cd still in the drive?

---

### Post by everyoshatesme on 2008-01-09
> **zabien1970 said:**
> Out of curiosity why does it  say 'boot from cd' in your screenshot?  Is the live cd still in the drive?

Good question.  Nope the dvd isn't in the drive.  I might have it in my bios to boot usb/cd/hdd though, I had been using it's simple boot manager by hitting esc to select what hdd i wanted to boot into (previously xp/vista).

Oddly, when I try to open the 931gb volume, it gives me that error.

in retrospect, I really should have unplugged both of the 500gb drives before I tried installing Ubuntu.  :(

---

### Post by everyoshatesme on 2008-01-10
Well i re-installed Ubuntu after disconnecting my other drives.  

I think when I installed Ubuntu originally it somehow jumped across to my raid-0 drives without giving me any indication that it was doing so.  

A nice function for future releases of Ubuntu might be to have it give a warning message such as "warning, detected /windows/ on drive X:\, continuing installation might/will erase your windows installation"

I have a friend who is making me an xp iso which has my raid drivers on board, hopefully with this I will be able to disconnect the Ubuntu drive, re-connect the raid-o drives and have it be able to detect and restore my X installation, as well as all of my files.

I haven't yet tried to boot Ubuntu with the raid-0 plugged back in, but before it wasn't letting me access my raid-0.  The error is posted above in a screencap.

---

