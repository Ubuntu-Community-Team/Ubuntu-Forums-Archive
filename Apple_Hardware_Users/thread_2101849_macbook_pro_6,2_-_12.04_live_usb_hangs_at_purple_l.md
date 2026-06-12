---
title: "macbook pro 6,2 - 12.04 live usb hangs at purple loading screen"
date: 2013-01-05
forum: Apple Hardware Users
---

### Post by 2emoore4 on 2013-01-05
Hey guys, this is my first post so I apologize if I'm not following etiquette.

I gave up on trying to install 12.10 on my macbook pro 6,2 because I couldn't get the nvidia drivers to work. Now I'm trying to install 12.04 and I can't even get a live usb drive to boot. It will get to the purple loading screen, then either freeze, turn black and freeze, or get this glitchy looking purple screen then freeze. When it gets to this point, I can still adjust volume and lcd brightness, so it seems like everything is running correctly except for the video drivers.

I've trying booting after removing the "splash" and "quiet" parameters, and adding the "nomodeset" parameter. This will boot straight to the command prompt with absolutely no errors.

I have the same problem with mint 13 (based of of 12.04) but not mint 14 (based off of 12.10). I really don't want to run 12.10 without the nvidia drivers because my battery life suffers and I want to try out steam.

Any ideas? Thanks in advance.

---

### Post by SpaceAviator on 2013-01-05
LiveUSB always hangs for me. Please use a disc. Works like a charm!

---

### Post by 2emoore4 on 2013-01-05
I was afraid someone might say that. The problem is that I replaced my optical drive with a second hdd and one of the screws is stripped so I can't revert. I might be able to bend one of the brackets though, so I might try that.

---

### Post by SpaceAviator on 2013-01-05
external? Also boot the usb in non efi mode.

---

### Post by 2emoore4 on 2013-01-05
I don't have an external dvd drive, only the internal one, which is not installed right now. also, how do I boot the live usb in non-efi mode? I don't know if it makes a difference, but I'm creating the live usb with unetbootin.

---

### Post by SpaceAviator on 2013-01-05
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)

---

### Post by SpaceAviator on 2013-01-05
Let me know if that works

---

### Post by 2emoore4 on 2013-01-05
Tried it once and the usb drive didn't show up when I booted and held down the 'option' key. Going  to image the usb drive and try it again.

---

### Post by 2emoore4 on 2013-01-05
Tried it again. The usb drive shows up as 'Windows' in the mac boot screen. If I select it, it just says 'Missing operating system'.

---

### Post by SpaceAviator on 2013-01-05
Sorry :/ The only OS that has worked for me via usb on this macbook (i have the same as yours) is fedora. Apparently the latest kernel is fedora also solves the speaker popping noise on shutdown.

---

### Post by 2emoore4 on 2013-01-05
I ended up being able to put the optical drive back in. I just booted a live cd for elementary os, which is based off of 12.04. Hopefully the nvidia drivers work with this. Thanks for your help!

---

### Post by SpaceAviator on 2013-01-05
can you tell me if you hear the popping noise from the speakers when you shut down your laptop? Thanks!

---

### Post by 2emoore4 on 2013-01-05
sent a pm.

---

