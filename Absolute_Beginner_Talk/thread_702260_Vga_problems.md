---
title: "Vga problems"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by vinniepearl on 2008-02-20
Hello. Ok so basically I ran the disk in safe vga mode. I clicked on the install icon and it installed my file system. I downloaded the nvidia drivers, yet I don't know how to install them. 

Then I rebooted and took my disk out, it started loading then It said my nvidia drivers weren't installed so I couldn't even get to my desktop yet. Then I put the live cd back in loaded it in safe mode and my drivers were gone. 

So now I re-downloaded my nvidia drivers. What do I do?

---

### Post by Crooksey on 2008-02-20
```

$ sudo sh ./PATH/TO/NVIDIA_DRIVERS
```

---

### Post by vinniepearl on 2008-02-25
I have one problem here. when I reboot the computer, the drivers that I downloaded are no longer there, because I booted in safe mode with the disk. 

 I can't place them on the hard drive while in safe mode because I don't have privileges to do that because I have to be on my actual account. 

So how do I get them installed like this if I don't have them?

---

### Post by vinniepearl on 2008-02-27
*bump*

---

### Post by uberlube on 2008-02-27
Use ENVY to install your video drivers. Its less of a headache.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by vinniepearl on 2008-02-29
But I can't get my drivers on the physical hard drive. They are only stored temporarily. I can't run ubuntu unless I use safe mode off the disk. How do I get the drivers to my physical hard drive?

---

### Post by vinniepearl on 2008-03-01
*bump*

---

### Post by vinniepearl on 2008-03-02
I just realized that I can burn the drivers to a disk. How would I install them from my cdrom drive?

---

### Post by vinniepearl on 2008-03-02
K so I have my driver on a disk. 

How do I mount my cd rom drive in command line. or i guess what I'm asking is.

$ sudo sh ./cdrom0/NVIDIA_DRIVERS  

would that be the correct line?

So I can install the driver.

---

### Post by vinniepearl on 2008-03-03
*bump*

---

### Post by vinniepearl on 2008-03-03
Ok... can someone atleast point me to where I can learn how to mount my cdrom drive on my own?

---

### Post by sanddgroper on 2008-03-04
Hi 
Not sure exactly what you are trying to do.
Can you boot into Ubuntu on the hard drive.
Why do you need to boot using the live cd.
Will your computer boot off the live cd normally.
Could you tell us what version of Ubuntu you are using
and on what hardware.

Cheers
Sandy

---

### Post by vinniepearl on 2008-03-09
My specs are
amd athlon 64
nvidia 6800gs pci express
soundblaster audigy soundcard
and an msi ms-7135 mobo.

Basically I have to boot in safe mode off the live disk. 
If I try to boot from the hard drive it crashes because it can't load my video drivers,
so what I was going to try to do was burn the drivers to a disk, and then install them from the disk from command line, before ubuntu boots.

---

### Post by vinniepearl on 2008-03-09
oh and I'm running the latest version of ubuntu 64 bit version.

---

### Post by vinniepearl on 2008-03-10
bump

---

