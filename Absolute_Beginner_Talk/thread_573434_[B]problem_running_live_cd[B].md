---
title: "[B]problem running live cd[/B]"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by greenleaf on 2007-10-11
My friend wanted to switch to linux from windows.....He receives this error message when running Ubuntu 7.04 live cd
```

int 14 : cr2 df 80000 err 0000000 epco2oc384 cs 00000060 flags 00010003
stack : c00f7 d40 c03f 129b c0371d5c 00000002 c00f7d49 000f7d40 00000000 00000000
```

can anyone help please.....

---

### Post by Dr Small on 2007-10-11
Have you tried burning a second CD ? It could be possible that the one you have is in some way corrupted.

Dr Small

---

### Post by wpshooter on 2007-10-11
Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by greenleaf on 2007-10-11
No problems with the cd.. i had requested it from ubuntu.com itself.... infact right now i'm posting this from my system running on ubuntu installed from the same cd.. He has really liked the OS and wants to install it..(he has reinstalled Windows 5 times in 2 weeks and is really fed up of the virus attacks)

He tried even kubuntu, linuxmint, and sabayon linux with the same error message...allthese were live cds... But on trying Fedora he could install it..but he could not mount his other FAT32 partitions..(this Fedora was not a live cd)... shall i post his system configuration? will that help? (infact my PC is much older than his)

---

### Post by Dr Small on 2007-10-11
Ok. Post the specs of the system.
When does this error message come up at ? Before the bootsplash ? After the bootsplash ?....

---

### Post by greenleaf on 2007-10-11
first it gives me 30s to choose to start/install ubuntu in various modes.. seleccting none of those works (including in safe graphics mode) Immediately after pressing enter it gives the above error (within 5s)


His system specs are

Compaq presario SR 10301L
Intel Pentium 4 2.6 GHz
512 MB DDR RAM
160 GB hard disk
Graphics: Integrated intel extreme graphics
Display: Intel (R) 82845G Graphics controller
Sound: Realtek AC '97

Infact when he bought it a couple of years ago it had come preinstalled with Linux OS!!

---

### Post by adamos on 2007-10-11
try some kernel parameters before you start installing. i was getting all kind of errors and i used **noapic** and problems were solved! when you start your pc with live cd at the first screen press F6 to put your parameters. make a search for kernel parameters and try different ones depending of your hardware to see what is good for you.


Adam

---

### Post by greenleaf on 2007-10-11
I pressed F6.... and it gave some line running like this

```
BOOT OPTIONS: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
```

I deleted this line and entered the following

```
live vga=771 noapic nolapic
```

but the screen went blank without any error message this time..

was i right in doing what you told me.. or is there something else... please explain in detail and in easy words what exactly should i do..and where and how to search for kernel parameters... we're completely new to these computers and all these commands freak us out!!

---

### Post by adamos on 2007-10-11
sorry, i thought you had some knowledge about linux :) DONT erase these lines!! after the dashes -- i.e. -- noapic  

and press enter


thanks
adam

---

### Post by greenleaf on 2007-10-11
Sorry.. it gives the same error message again... 
we also tried     boot:acpi=off     with a different error message...


you told something about kernel parameters... what are they? where to look for them.. and where to enter them

---

### Post by adamos on 2007-10-11
noapic is a kernel parameter. search here in the forum for parameters.

noapic noirqdebug acpi=off

^
try that

---

### Post by greenleaf on 2007-10-11
should these commands be entered in front of those dashes?

---

### Post by LowSky on 2007-10-11
after the dashes

---

### Post by greenleaf on 2007-10-11
thanks guys.... **IT WORKED** !!!!

apparently the following command worked

```
BOOT OPTIONS: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash -- noapic noirqdebug acpi=off
```

he is installing UBUNTU and may take another 20 min for it to be up and running...

Thanks for converting one more frustrated Windows user into a UBUNTU fan!!!


THIS COMMUNITY ROCKS!! REALLY!!! :guitar:

---

### Post by adamos on 2007-10-12
no problem my friend, thats y we are here for. how is it? is it booting ok etc. did u get the wireless working?


Adam

---

