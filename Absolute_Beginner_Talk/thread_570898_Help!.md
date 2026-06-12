---
title: "Help!"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-08
My ubuntu is like in safe graphics mode or something, because everything is like 5 times bigger, and I cna't change it, I alreafy rebooted.

---

### Post by laidback on 2007-10-08
This has happened to me when the VGA cable is not properly attached, at boot up system defaults to something else. Check cable connections.

---

### Post by TaiQui on 2007-10-08
I am using a notebook laptop.

---

### Post by TaiQui on 2007-10-08
bump..:(

---

### Post by om1 on 2007-10-08
which version of Ubuntu are you using
was it like this when you installed or did you change something and it started to be like that

---

### Post by jpyanowski on 2007-10-08
Have you searched through the other forums for this problem? You can find many answers that way..

---

### Post by TaiQui on 2007-10-08
I didn't change anything and it was normal before, and also, its in my sig, ubuntu 7.10

---

### Post by n3tfury on 2007-10-08
what resolution does it say you're in currently and what was your resolution before?

---

### Post by om1 on 2007-10-08
try this ... 
run this in terminal 
```
sudo dpkg-reconfigure xserver-xorg
```
and only choose 1024x768 as your resolution

---

### Post by TaiQui on 2007-10-08
I get this and am not sure how to continue

Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474;  ISA:1                                                                    &#8593;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.                            &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; You may wish to use the "lspci" command to determine the bus location of  &#9618;  
 &#9474; your PCI, AGP, or PCI-Express video card.                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; When possible, this question has been pre-answered for you and you        &#9646;  
 &#9474; should accept the default unless you know it doesn't work.                &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by om1 on 2007-10-08
press enter
or press tab it enter isnt highlighted read
then press enter

---

### Post by TaiQui on 2007-10-08
What do I do here?

                                                             
                    &#9484;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                     
                    &#9474; Mouse port:                         &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;           /dev/input/mice           &#9474;                     
                    &#9474;           /dev/psaux                &#9474;                     
                    &#9474;           /dev/ttyS0                &#9474;                     
                    &#9474;           /dev/tts0                 &#9474;                     
                    &#9474;           /dev/gpmdata              &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9474;               <Ok>                  &#9474;                     
                    &#9474;                                     &#9474;                     
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by om1 on 2007-10-08
if you have a normal mouse
choose 
/dev/input/mice 
and tab then hit enter

---

### Post by TaiQui on 2007-10-08
I have a laptop mouse...

---

### Post by om1 on 2007-10-08
ok it will work for that

---

### Post by philinux on 2007-10-08
Basically with xorg reconfigure answer yes as it finds your stuff by default.

---

### Post by TaiQui on 2007-10-08
What do you think I should do here? Simple?

                                                                     
             &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;             
             &#9474; Method for selecting the monitor characteristics:  &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                      Simple                        &#9474;             
             &#9474;                      Medium                        &#9474;             
             &#9474;                      Advanced                      &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                                                    &#9474;             
             &#9474;                       <Ok>                         &#9474;             
             &#9474;                                                    &#9474;             
             &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by philinux on 2007-10-08
simple

---

### Post by dz0004455 on 2007-10-08
wow, this is why i stick to the most recent reales, and upgrade the day the new one comes out

---

### Post by TaiQui on 2007-10-08
For color depth, should I do 16 or 24?

---

### Post by om1 on 2007-10-08
24

---

### Post by TaiQui on 2007-10-08
Okay, I just finished and got this.

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071008191221

---

### Post by om1 on 2007-10-08
that is normail

---

### Post by TaiQui on 2007-10-08
ok, thanks, should I just reboot now or something?

---

### Post by om1 on 2007-10-08
yeah

---

