---
title: "video card installation problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Loki*PI on 2008-03-03
I'll try to keep it simple.  I had an unsupported card the was flaky, so I bought a nvidia mx4000, this is an older box. I put the mx4000 in think there would be some kind of basic video drive that would see it and give video.  No luck, got nothing, black screen.  I put in the original and mx4000 and the system won't come up, won't even boot. So now I have in the old card, I can bring up the system, and get online.  

Here is the question: How do I make the jump from the flaky but working card to the nivida?  I down load the nvidia-glx-legacy drivers for the nvidia and install them? Is the old card going to keep working? Then if I put in the nvidia will the drivers see it or am I going to have a black screen and neither card work? 
 
I have a bad feeling about this.  

Also my copy of ubuntu is not bootable.  If I lose the box I have to install XP so that I can reinstall the Ubuntu; how embarrassing?

---

### Post by forestpixie on 2008-03-03
I'd put the card in boot to recovery - then do 

dpkg-reconfigure -phigh xserver-xorg
can't remember if you need sudo in recovery, don't think so

when you get to graphics card - try nv first, if that doesn't work go for vesa

then once you're in again - try restricted drivers to get the nvidia one

---

### Post by kpkeerthi on 2008-03-03
1. Install the nvidia card (the hardware)
2. Boot into 'Recovery mode' from GRUB menu
3. Make sure your new card is recognized by running
```
lspci | grep -i nvidia
```
4. Now run 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and choose 'nv' for the driver. If 'nv' is not listed, choose 'vesa'. Then choose appropriate resolutions you card is known to can handle.
5. Reboot in multi-user mode (normal mode). Lets hope 'X' works for you.
6. Now install the nvidia binary driver using Restricted Drivers manager. See [here]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") for instructions.

---

### Post by Loki*PI on 2008-03-03
Thanks, I'll try it. then get back on let you know how it went.

---

### Post by Loki*PI on 2008-03-03
humm I'm getting no video at all from this card.  I think it is a trip back the computer store and a new card.

When I get a working card I'll try your suggestions.  thanks again.

---

### Post by forestpixie on 2008-03-03
just so you know when you install a new card you have to run the reconfigure command so that the system knows it's there

---

