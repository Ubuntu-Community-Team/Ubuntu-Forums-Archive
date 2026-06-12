---
title: "Need to burn old mac cd image - imac G3 can't boot from cd burned in Linux??"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by jimmy the saint on 2008-08-01
I am attempting to get an old imac G3 working for my grandmother.  The imac came from a buddy who had his discs all backed up in .toast images. What a pain!!

Long story short, I have gone through 9 cds so far trying to get the imac to boot.  I searched around and have tried many solutions, VERY slow burning, audio grade CDrs, various burning apps (brasero, gnomebaker, K3B) in linux and in a windows virtual machine.  I also tried cleaning the cd drive lens.  

Theoretically, a .toast file can be renamed .iso and burned.  And the imac does seem to read the cds burned very slowly quite well.  They just won't boot from them.  When the imac tries to boot from the cd the little graphic with a question mark blinks for a bit, then it boots form the HD.  

I am at a loss.  I don't know if it is an image compatibilty problem??? K3B says the image is unsusable, and the other two report errors after the integrity check.  Is there an imac trick that I am missing?  I will post the results of "file" when perfomed on the disc image.

```
MacOS9Retail.iso: Apple Partition data (block size: 2048): first type: Apple_partition_map, name: Apple, number of blocks: 63, second type: Apple_Driver43, name: Macintosh, number of blocks: 56, third type: Apple_Driver43_CD, name: Macintosh, number of blocks: 120, fourth type: Apple_Void, name: , number of blocks: 0, fifth type: Apple_Driver_ATAPI, name: Macintosh, number of blocks: 56 sixth type: Apple_Driver_ATAPI, name: Macintosh, number of blocks: 120
```

Any input would be greatly appreciated.  I need to get this up and running, or come up with a new plan by tomorrow!

Thanks

JTS

---

### Post by marshag63 on 2008-08-01
JTS, are you holding down the "C" key when the computer starts?  - That makes it boot from the CD-ROM.  (I hold the "C" key until I get "Boot: ??"

The other thing you should do is reset PRAM by holding down the Option + Apple + P + R keys all at the same time - let chime and cycle to the next chime at least twice, then press and hold down the "C" key until it boots from the CD-Rom.  

Let us know how it goes

Marshag63
G4 iMac/700

---

### Post by jimmy the saint on 2008-08-02
i appreciate the response.  I did the C key thing, as well as setting the cd to be the boot device.  For some reason These cds wont boot.  k3b and gnomebaker wont even touch the images.  The mac reads the cds just fine.  Everything seems to be readable.  Unfortunately, they just wont boot so i can reinstall the system!!

---

### Post by jimmy the saint on 2008-08-03
I found a post somewhere else that indicated that the blue imacs (Summer 2000 I believe) are unable to load any non-official cds.  Does anyone know if there is any truth to this?  I figured it was a "burning from Linux" issue, maybe its an imac issue.

---

### Post by tiresia on 2008-08-04
Can you please give us more informations? 
If I understand right, at the moment your imac has no OS. And you are trying to burn the CD's on a PC running Linux. 
Can you mount the .toast images? If yes, which command do you use?

---

### Post by jimmy the saint on 2008-08-04
The .toast files will not mount.  If I change it to .iso, it still won't mount, as it says it is not the correct file system.  The fact that the imac will read the cd tells me that the burn is good, it just won't boot.  It is a blue imac (summer 2000 I believe) g3 350mhz.  I am not 100% sure that the information I found about that particular run rejecting non-apple cds is accurate, but it would sure explain a lot.  I am working on getting my hands on official cds and I will see how that works.

---

### Post by cyberdork33 on 2008-08-04
I have a blue G3 iBook that has a terrible CDROM that is likely similar to the one in the iMacs of the time. It is REALLY picky about booting from CDs.

---

### Post by DRM_free on 2008-08-04
Make sure you **unplug all USB devices** except the Apple keyboard (which of course you need to use in order to press C).

My Blue iMac G3 used to spit out the boot CD every time, until I finally figured out (by tedious trial and error) that I needed to unplug the USB mouse before boot.

I'm not sure what these .toast files you are referring to are. If you want to boot, download the latest [PowerPC Ubuntu ISO]("http://cdimage.ubuntu.com/ports/daily/current/").

---

### Post by jasex on 2008-08-05
My iMac -HATES- linux. I've tried so many different ways, and then ya... removing the mouse did allow me to boot... Couldn't get it then to read the second memory chip :D so slow as hell... couldn't get xORG to run properly... because I have -NO- idea as to how the hell they work on iMacs. I have the blue one myself... and yeah... it is a pain in the *** for some reason, who knows... installed on a similar green one with -NO- problem.


On up the road they were thinking "Someone may try to put linux on this, let's piss 'em off" 

My advice? find a different imac... E.g. Craigslist

---

### Post by stream303 on 2008-08-05
I think it might be time for a new plan. :)

If you could get that machine up with OS9, would Grandma be happy with super old browser technology, mail, etc?

If you can obtain some ram, you might be better off doing a clean Ubuntu install.

---

### Post by tiresia on 2008-08-05
Let's say that your MacOS9Retail.toast file is on your Desktop, and you want to mount it. Make a directory, e.g. /mnt/MacOS9

```
mkdir /mnt/MacOS
```

To mount the .toast file, mount it as hfs

```
mount -o loop -t hfs /mnt/MacOS9 Desktop/MacOS9Retail.toast
```

If it does not work, try with hfsplus

```
mount -o loop -t hfsplus /mnt/MacOS9 Desktop/MacOS9Retail.toast
```

To unmount it

```
umount /mnt/MacOS9
```

Now, if you want to burn it, use wodim

```
wodim -dao -v Desktop/MacOS9Retail.toast
```

Now you should be able to start from the MacOS9 installer.
Anyway I agree with stream303, Ubuntu would make a better job:)

---

### Post by jimmy the saint on 2008-08-07
I agree with stream303 and teresia about ubuntu.  I gave up on the imac for the time being and just set her up with Ubuntu.  I never realized what an absolute pain it is to set up a modem though.  I don't mean to complain, but geez, I didn't feel this much frustration when I first switched to Ubuntu from windows!!  oh well, I will figure it out and she will be happy, which will make me happy, and I can spend a few weeks playing with the imac.  

I will definitely try your commands out tiresia.  Based on the responses I've recieved, though, I am pretty sure it is the cdrom drive and not the burn.  I'll post back if I happen by a perfect solution.
Thanks for all the help guys!

JTS

---

