---
title: "Ubuntu CRASH on startup"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Pwn* on 2006-05-27
Hey, I have been having a little problem, the install goes smoothly then when i boot it crashes as soon as the mouse and the ubuntu logo comes up, but the logo is all glitched out with lines going through it

I am running a compatible motherboard (i have seen it work on it ) but i am useing an nVidia Geforce 7800 GT

Plz help ](*,)

---

### Post by nudnik on 2006-05-27
You should check your install CD to make sure it isnt flawed, then proceed from there.

What are your system specifications?

---

### Post by JoshHendo on 2006-05-27
Does Ubuntu work with the live CD?

---

### Post by Pwn* on 2006-05-27
its a good cd because it is shiped here, a non burn ( an extra cd i had that i was handing out to my friends) NON scratched.

I have the same exact problem with the live CD.

i have a hp a720n motherboard (getting a new one like next week :D)
A nVidia EVGA 7800 GT
1.5GB of supertallent ram DDR
Intel P4 running at 2.8 GHz ; 800Mhz 



NOTE i have seen ubuntu run on all of the listed hardware accept the processor and Video card

---

### Post by nudnik on 2006-05-27
Have you run Windows or other Linux distros successfully on this machine? If so, you might want to download the latest Dapper (6.06 LTS) and give that a try. 

I am running a Pentium D 820 on an Intel 945PSN motherboard with an 80GB SATA drive, Nvidia 7300GS video card, and Dapper is much more compatible with my system than Breezy.

---

### Post by Pwn* on 2006-05-27
Yes, i am currently running OSX 10.4.1,  and xp pro

like i said, i have used ubuntu on this board, actualy my friend did and i bought this off of him for $30

but i know it is not the board

---

### Post by nudnik on 2006-05-27
Your video card and processor are pretty standard fare. Ubuntu has custom drivers available for the card, and I doubt the processor is a problem either.

I still suggest giving Dapper a try since your hardware seems to be ok.

That being said, I would also wait and see what other responses you receive since there are many others lurking about who are more experienced than I.

---

### Post by Pwn* on 2006-05-27
Hmm, I will try dapper but i will wait until i see a few others responces


is it possible i selected the wrong linux kernel durring installation

---

### Post by Pwn* on 2006-05-27
errm, this might be a stupid qustion but where do i get/ how dapper without being in ubuntu

BTW i can get into the text mode

---

### Post by nudnik on 2006-05-27
See this page for Dapper downloads: [http://www.ubuntu.com/testing/dapperrc](http://www.ubuntu.com/testing/dapperrc)

Use either HTTP or bittorrent client, either way a broadband connection is really needed as you will be downloading nearly 700MB of material. If that isnt possible, wait until June 1st, when Dapper should be available for shipping on pressed CD.

If you were able to access the command line from 5.10 you could also type : gksudo "update-manager -d" and Breezy will update to Dapper...although it takes forever, almost as long as downloading the CD. ;)

---

### Post by tseliot on 2006-05-27
Try this:
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "vesa" (instead of "nv", "ati", ecc.) in the Section Device of the file.

Then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

If the suggestion above doesn't work you can try with "vga" instead of vesa.

---

