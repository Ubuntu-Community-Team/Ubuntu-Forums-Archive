---
title: "Newb to ubuntu need help"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by TekMek on 2007-10-27
Hi, 

I have a dell poweredge 800 server, pentium 4, with 4 gigs of ram. I installed ubuntu on it and im wondering why its so slow. Its a first time fresh install and i havnt messed with any settings, but i do see that it says its running 2 cpu's when i only have one pentium 4. Could that be the issue? if so, how can i fix this problem? I have a graphics card installed and its running ok at about 950 fps but i dont think thats the problem because it takes very long for anything to load.

Thanks for any help. :guitar:

---

### Post by TekMek on 2007-10-27
bump :confused:

---

### Post by Unicycle on 2007-10-27
Correct me if I'm wrong, gurus, but I believe that if you're on a non-NTFS partition, loading will be slower.  Again, I am not sure about this.

---

### Post by santiagoward2000 on 2007-10-27
> **TekMek said:**
> Hi, 

I have a dell poweredge 800 server, pentium 4, with 4 gigs of ram. I installed ubuntu on it and im wondering why its so slow. Its a first time fresh install and i havnt messed with any settings, but i do see that it says its running 2 cpu's when i only have one pentium 4. Could that be the issue? if so, how can i fix this problem? I have a graphics card installed and its running ok at about 950 fps but i dont think thats the problem because it takes very long for anything to load.

Thanks for any help. :guitar:

I don't know about the CPUs thing. But to make it clearer, which version of Ubuntu have you installed? Which graphics card do you have?

---

### Post by TekMek on 2007-10-27
i have version 7.10 and i have an ati 256mb graphics card

---

### Post by TekMek on 2007-10-27
bump

---

### Post by icechen1 on 2007-10-27
Have you installed the ati driver? [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
And did you downloaded the x86 or x86-64 version?
Go to System>Administration>Screen and Graphics and in the graphics card tab,what it says?

---

### Post by staticvoid on 2007-10-27
google "envy" it sets up nvidia and ati graphic cards automatically. but you said you don't think thats the problem...

perhaps try making your swap partition bigger? I have absolutly no clue why. so actually, perhaps don't do that...

what exactly loads slowly? the booting of ubuntu? programs?

staticvoid

---

### Post by argie on 2007-10-27
Disable hyperthreading. I don't see why it should cause slowness but it's worth a try.

Run this in the terminal:
```
gksudo gedit /boot/grub/menu.lst
```

Locate the line where your kernel is. It should look somewhat like this:
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
**kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=61fdbdf7-2fd1-411c-9a4d-60d6a792834e ro quiet splash**
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

Right after the word 'splash' add the word ```
noht
```

Save and quit. Now restart the computer. 

Alternatively, if you want to give it a shot without changing any files, when you get the grub loading screen, press 'e'. You will see a list of lines similar to that stuff in your menu.lst. Then add noht there and press 'b' to boot.

---

### Post by TekMek on 2007-10-27
> **icechen1 said:**
> Have you installed the ati driver? [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
And did you downloaded the x86 or x86-64 version?
Go to System>Administration>Screen and Graphics and in the graphics card tab,what it says?

i downloaded the x86 version and in the graphics card tab it says

Graphics card (VESA driver (generic))

Driver: fglrx

Video memory: Automatic

and

Graphics card (VESA driver (generic))

Driver: vesa-Generic VESA-compliant video cards

Video memory: Automatic

---

