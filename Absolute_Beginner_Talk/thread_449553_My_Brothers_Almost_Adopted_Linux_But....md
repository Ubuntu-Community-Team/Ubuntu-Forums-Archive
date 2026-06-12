---
title: "My Brothers Almost Adopted Linux But..."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-05-20
hi,
i installed ubuntu christmas edition and my brothers couldn't resist. And when they saw how i recovered a friends files using a live cd plus the slick screensavers, They were willing to forsake windows and save us space on the hard disk. But i could get 3d for our nvidia mx400 card i tried using the onboard savage but i dont know what to do. i reverted back to the nvidia, but without the 3d as it hangs the pc even after disabling shared memory in bios. What can i do thanks

---

### Post by brennydoogles on 2007-05-20
> **adewale said:**
> hi,
i installed ubuntu christmas edition and my brothers couldn't resist. And when they saw how i recovered a friends files using a live cd plus the slick screensavers, They were willing to forsake windows and save us space on the hard disk. But i could get 3d for our nvidia mx400 card i tried using the onboard savage but i dont know what to do. i reverted back to the nvidia, but without the 3d as it hangs the pc even after disabling shared memory in bios. What can i do thanks

Download and run Envy[HERE.]("http://www.albertomilone.com/nvidia_scripts1.html") That should get your driver working perfectly!!

---

### Post by Kobalt on 2007-05-20
Which version of Ubuntu (appart from CE) is it you installed ? Unber 7.04 you can install the drivers for your nvidia card from System > Admin. > Restricted Drivers Manager.

---

### Post by adewale on 2007-05-20
i've tried envy and am using edgy. Am kind of scared installing fiesty what if the same issue occurs thanks

---

### Post by Kobalt on 2007-05-20
To install the nVidia drivers in Edgy run the following command lines then : 
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
And reboot. That should do it.

---

### Post by DeadSuperHero on 2007-05-20
Also, try taking out your gfx card, and putting it back in. That worked for me.

---

### Post by adewale on 2007-05-20
i think i've tried nvidia glx but i'll give it a shot
@Mr. Psychopath
was your pc freezing also?

---

### Post by DeadSuperHero on 2007-05-20
> **adewale said:**
> 
was your pc freezing also?

No, it wasn't freezing up, but if I tried to run a 3D program, the window would open up, start to load, and then promptly crash.
So, I experimented with ENVY, and whatever was in Ubuntu's repositories.
Finally, I just took it out, put it back in, and it worked!
Make sure you install Beyrl, and enable desktop effects. Your brother would dig all the eye candy.

---

### Post by adewale on 2007-05-20
ubuntu repos aren't accessible

---

### Post by abhishek456 on 2007-05-20
> **adewale said:**
> ubuntu repos aren't accessible

can you give more details

---

### Post by adewale on 2007-05-20
when i type packages.ubuntu.com in my browser its not able to find it i tried following from goole stiill the same

---

### Post by abhishek456 on 2007-05-20
I can open the page [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
may be some network problems for you.

Try google cached version of the page[http://216.239.59.104/search?q=cache:kHG_JS0n8Z4J:packages.ubuntu.com/+packages.ubuntu.com&hl=en&ct=clnk&cd=1&gl=in]("http://216.239.59.104/search?q=cache:kHG_JS0n8Z4J:packages.ubuntu.com/+packages.ubuntu.com&hl=en&ct=clnk&cd=1&gl=in")

also try accesing it through some proxy server

---

