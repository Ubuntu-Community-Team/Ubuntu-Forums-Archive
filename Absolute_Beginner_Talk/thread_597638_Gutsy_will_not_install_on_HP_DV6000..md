---
title: "Gutsy will not install on HP DV6000."
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by t1hall on 2007-10-30
Having a bit of problems..I need some help. I bought this HP Pavilion DV6000 laptop,dv6119us(Nvidia 6150), and cannot install Feisty or Gutsy on this laptop. The laptop is running a AMD64 . After rebooting the machine at least 15 or 20 times the Live CD might run. If it does run, when I try to install Gutsy it just hangs up. I have had this problem since I bought the laptop and its probaly my lack of experience with Linux. Is there anybody who knows how to resolve this issue. I run Ubuntu on a lot of desktops, but the main computer is my laptop. So can someone help me out, I would greatly appreciate it.

---

### Post by Incense on 2007-10-30
That's odd that the live CD won't run. Have you tried the alternate install CD?

---

### Post by Pumalite on 2007-10-30
It's more probably your hardware. Can you give as detailed specs? I will give you a link to examine. It might help you understand the problem. To start with you should be using Alternate CD if you are going to have any luck at all.
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by plinydogg on 2007-10-30
I have no idea if this will work for you but I had a similar problem on an HP dv5000. This is what I had to do to get it to work (although I have no idea what it means):

(1) When the initial screen is displayed press [F6] and 
(2) Then type: Linux acpi=off

[Edit: I didn't have to do this for the Gutsy LiveCD, only Feisty]

---

### Post by rudeboyskunk on 2007-10-30
Assuming he has not upgraded anything in particular, [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00771277&lc=en&cc=us&dlc=en&product=3257768&rule=44523&lang=en]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00771277&lc=en&cc=us&dlc=en&product=3257768&rule=44523&lang=en") should be his product specs.

---

### Post by t1hall on 2007-10-30
Yep, thats my setup. Where do you download the alternate CD? Thanks for your help.

---

### Post by Pumalite on 2007-10-30
Here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'

---

### Post by motokitn on 2007-11-09
I have been having similar issues on my dv6000. With every livecd or install of Ubuntu I have done on this machine, I have needed to add vga=791 to the boot parameters in order to have my screen load properly. Gutsy would not boot at all from the livecd, so I had to install Feisty and upgrade. When I try to boot the default kernel, I get nada. Zip. No splash, no messages, just a black screen forever and no hd activity. This is with kernel 2.6.22-14-generic. However, when I boot from 2.6.20-16-generic I get a perfectly operating system. I have tried all the boot parameters suggested above to no avail. This is an issue for me because I need to be able to build kqemu for virtualization- yes, on my laptop- and I am unable to fetch the right kernel source and headers. (Windows XP runs soooo sloooow without kqemu!)
I hope this has been of some help to somebody out there!

---

### Post by hegex on 2007-12-19
i have to confirm alots things u have said.
First issue is nvidia drivers. If u start with boot paraments like acpi=off, u MAYBE will get something on screen, even u use or not nvidia drivers, but u are not able to use bcm43xx (wlan driver) and sounds will messup. it gives looping sound. others paraments like noapic, pci=usepirqmask worked on feisty but not in gutsy. I will give just black screen or will force u to choose something else than nvidia-drivers.
I am used ubuntu on that laptop since dapper, and nothing had worse than gutsy.
and yeah. trying to install with alt-cd is the best way to do the install in this case. Good luck for u. Dont expect too much from gutsy.

---

### Post by magaltavor on 2008-03-14
[http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87) 

Thanks

---

