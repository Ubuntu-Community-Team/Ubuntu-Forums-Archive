---
title: "wondering of hardware will support linux"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by rohitdcosta on 2006-11-02
Hello,

I'm a newbie to Linux and am considering shifting to Ubuntu coz im simply sick of microsoft and other propreity corporates.

I have a P4 HT 3GHZ, ASUS P5RD1 mobo, 1GB RAM, PINNACLE 50i tv tuner, RAZER COPPERHEAD mouse, 120 GB SAMSUNG SATA.

Some of my doubts are...

1)
When I install Windows I need to put in a floppy and install sata drivers so that windows will recognise the hdd. will i have to do the same thing for Ubuntu? coz i dont know where to get SATA drivers from?

2)
will my Razer Coppherhead work on Linux and will it support on the fly sensitivity changing?

3)
will my tv tuner card work with Linux (Pinnacle 50i), and what software will i have to use to watch tv

4) 
how will i get stuff like my bluetooth dongle, infared dongle et all to work...

I know its a long list of problems but please find the time to answer them. I would really like to be a part of the linux community and be a part of the open source way of life  8) 

Thanks.

---

### Post by steve.horsley on 2006-11-02
1) Your SATA drive shouldn't be a problem. There are still a few makes of SATA drive that Linux can't handle, but most of them just work.

2) I think on-the-fly sensitivity changes are unlikeky. You will have to try it to see if the mouse works at all.

3) I don't know about TV tuners.

4) Most likely they will all "just work".

Most of these questions are best answered by using a live CD. A live CD runs the normal Ubuntu OS but from CD. It doesn't need the hard disk (but you can check if it can see the hard disk). You can try the mouse and dongles. You can even downoad and install new software (into the RAM-disk) to try TV software.

The live CD is apallingly slow compared to a hard disk install, but will give you a taste of what Ubuntu is like, and whether it can drive your hardware.

---

### Post by azharc on 2006-11-02
To test whether all your hardware will work with Linux, just run Ubuntu from the LiveCD and see if everything is working fine.

Best of luck on installing Ubuntu, welcome to Linux!

---

### Post by thornomad on 2006-11-02
On a related vein, if one were preparing to build a new custom system from scratch, where might one find compatible hardware in order to avoid any "extra legwork" after the install to get things working?  

Are there any Ubuntu-Certified parts ?

---

### Post by bluenova on 2006-11-02
What about your graphics card?

4) Bluetooth will be fine, Infared you may have trouble.

---

### Post by lordgibbness on 2006-11-02
TV card should work (but may require some extra config - I had to for my Pinnacle PCTV-Rave). Best TV app is TVtime!

---

### Post by Bartender on 2006-11-02
thorno -
The closest thing we have is [this]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by thornomad on 2006-11-02
> **Bartender said:**
> thorno -
The closest thing we have is [this]("https://help.ubuntu.com/community/Repositories/Ubuntu").

Enabling repositories?  Hmm.  

Pardon me if I am being silly, but how would that help me know which hardware is plug-and-play compatible (optimized) for Ubuntu?

---

### Post by compmodder26 on 2006-11-02
Try this out:

[https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport")

---

### Post by Bartender on 2006-11-02
Sorry sorry my bad :-#

---

### Post by MattJ100 on 2006-11-02
And this: [http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

### Post by rohitdcosta on 2006-11-02
graphics is handled by a nvidia 7300gs but im assuming ubuntu will support this card out of the box?

---

### Post by Bentov on 2006-11-02
For what it's worth, I have a logitech G5 mouse and the on the fly dpi changing works fine.  No speical drivers or anything needed.

Bentov

---

### Post by Raemir on 2006-11-18
I'm designing a new system so I was curious about the Razor mouse as well (I've got one on a Windows system and love it so I wanted to use one on the new Ubuntu system as well).

According to Phoronix Linux Compatible Hardware [here]("http://www.phoronix.com/lch/?k=entry&l=16&t=Razer") the Razer Copperhead works reasonably well under Linux.

The Sourceforge site referenced for RazerTool is [here]("http://sourceforge.net/projects/razertool/").

---

### Post by rev_b on 2006-11-18
My motherboard, ethernet and sata controler and HDD were recognised without problems by edgy. And it has a not-so-mainstream chipset, the ULI 1695... My Pinnacle PCTV-pro was also working by default in TVtime, my Audigy soundcard also works fine with alsa, even the integrated firewire controler works just fine with my DV cam! My HP PSC-1215 all-in-one works both the scanner and printer, as my Epson R200.

For Linux, your best bet are Nvidia cards, they really do a nice job in Linux drivers.

So try with the live CD. After booting, you can easily see what's being properly detected or not.

---

