---
title: "Faster Performance with Radeon Driver"
date: 2005-01-30
forum: Apple PPC Users
---

### Post by cybergypsy on 2005-01-30
Hi All

I have found I get better performance on my Powerbook G4 when I change the XF86Free driver in /etc/X11/XF86Config-4 from ati to radeon

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9000 M6 (R250 LY)"
        Driver "radeon" 
#
# changed this line
# Driver "ati"
#

Any comments ?

cybergypsy

P.S. Thanks to all responsible for making Ubuntu

---

### Post by Viro on 2005-01-30
yes, that is to be expected. The ati driver is for the Rage line of cards. The Radeon series should use the radeon driver. I'm surprised Ubuntu defaulted to the ati driver though...

---

### Post by khc on 2005-01-30
hmm I didn't know that, thanks.

---

### Post by t.rei on 2005-01-31
[QUOTE=khc]hmm I didn't know that, thanks.[/QUOTE]
 well... what would be the optimum driver for the ati 9600 running xorg on hoary (powerbook g4 5,2)

---

### Post by Viro on 2005-01-31
[QUOTE=t.rei]well... what would be the optimum driver for the ati 9600 running xorg on hoary (powerbook g4 5,2)[/QUOTE]
 The radeon driver. Ideally, it would be released by ATI, but till then, the open sourced radeon driver is the best you can do.

---

### Post by JoWilly on 2005-01-31
[QUOTE=t.rei]well... what would be the optimum driver for the ati 9600 running xorg on hoary (powerbook g4 5,2)[/QUOTE]

Go to [this](http://www.ubuntuforums.org/showthread.php?t=13342)  thread to install the fglrx ati drivers.

Edit: Sorry, I just saw you are searching for Powerbook.... don't know if the linux kernel module is in the repositories for PPC.

---

### Post by Viro on 2005-01-31
[QUOTE=JoWilly]Go to [this](http://www.ubuntuforums.org/showthread.php?t=13342)  thread to install the fglrx ati drivers.

Edit: Sorry, I just saw you are searching for Powerbook.... don't know if the linux kernel module is in the repositories for PPC.[/QUOTE]
 The fglrx drivers are x86 only. The only PPC option is to use the open sourced radeon drivers that come with XFree86 and xorg.

---

### Post by t.rei on 2005-02-02
[QUOTE=Viro]The fglrx drivers are x86 only. The only PPC option is to use the open sourced radeon drivers that come with XFree86 and xorg.[/QUOTE]
 thats what I thought. Too bad - I shure hope DRI will work some day. *sigh* - The shadows look kewl, but I want the transparency ;) - It works, but speed is a absolute no-go!

---

### Post by Momo on 2005-02-02
I read on a site that ATI were looking for feedback on their linux drivers from users. Seems they might be trying to make more of a go at the linux market. Might be a good opportunity to tell them that there's a not-insignificant amount of PPC users who want some drivers written ta very much.

[http://www.driverheaven.net/showthread.php?t=67117](http://www.driverheaven.net/showthread.php?t=67117)

---

