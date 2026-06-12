---
title: "updating with mounted .iso"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by craig2321 on 2008-03-19
i have ubuntu 6.04 installed and I have the 7.10  downloaded onto my desktop. I don't have any more blank cd's so I want to mount the .iso image and update that way. I tried mounting it and all it does is open up a folder with a bunch of files. It doesn't autorun.

I mounted using...

sudo mkdir /mnt/ubuntu
sudo mount -t iso9660 -o loop filename.iso /mnt/ubuntu


Reason why i'm updating this way is I don't have an internet connection with this particular computer because 6.04 doesn't recognize my lan chip (realtek something..). I got the .iso from a usb stick from someone. I'm using kubuntu. How do I go about doing this.

---

### Post by Daveth on 2008-03-19
I'm a bit confused by this. You have 6.04 on the hard drive, but are you running 7.10 as a live cd? Why do you not load 7 over 6 as it will have much better lan chip support and your internet connection may work. I personally never upgrade online, preferring a good old cd upgrade with a clean install every time.

Or have I got completely the wrong end of the stick here???

---

### Post by craig2321 on 2008-03-19
Not as a live CD no. I mounted the image while I was in 6.04. I don't want install a fresh copy of 7.10, I want to update 6.04 to 7.10. I thought this was possible by just popping in a CD of the newer version and a window would pop up and say "update to 7.10". I don't have a blank CD so I wanted to mount the image instead to see if that would work...and all I get is a bunch of files in the file browser. There's pop up screen...and I was wondering what I was doing wrong.

---

### Post by mcduck on 2008-03-19
You can't upgrade directly from 6.06 to 7.10. Even if you'd manage to do that it's quite unlikely that you'd end with a fully working setup.

The only supported way is to upgrade from one version to the next, so you'd first need to upgrade from 6.06 to 7.04 and then again from 7.04 to 7.10.

Probably it would be just easier to back up all your personal stuff and setting files (unless you already have a separate home partition) and then do a fresh 7.10 install from the disk you have.

---

### Post by Daveth on 2008-03-19
Mcduck beat me to it. I think you would do better making a separate home partition on 6.06, then just burning 7.10 over it, keeping all your home files safe. This guide

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

will help you through. Then you will be able to safely upgrade into the future.

---

