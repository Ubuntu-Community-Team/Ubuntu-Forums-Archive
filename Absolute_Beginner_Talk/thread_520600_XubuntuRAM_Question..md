---
title: "Xubuntu/RAM Question."
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Dionysus135 on 2007-08-08
Hi im new to Linux, Ubuntu and Xubuntu. Im planning to insall Xubuntu on a Windows 98, Dell Dimension 4100 Cpu, Pentium 3.Now my question is that I have EXACTLY 128 Mb RAM. Would it work smoothly and fast?

---

### Post by oilchangeguy on 2007-08-08
> **Dionysus135 said:**
> Hi im new to Linux, Ubuntu and Xubuntu. Im planning to insall Xubuntu on a Windows 98, Dell Dimension 4100 Cpu, Pentium 3.Now my question is that I have EXACTLY 128 Mb RAM. Would it work smoothly and fast?

it will be somewhat slow. if you've got onboard video, you'll need to up the ram.

---

### Post by tgalati4 on 2007-08-08
You will also benefit from a 256 to 512 MB swap file.  You will need the swap file to use the graphical installer otherwise use the alternate CD.

Memory is cheap.  Load up Xubuntu, then add the RAM and you will see the difference.  Your machine will probably take 256 MB per slot (assuming PC100).

It will be decent for web and email and routine tasks.  It will certainly be better than win98.

---

### Post by Rocket2DMn on 2007-08-08
> **oilchangeguy said:**
> it will be somewhat slow. if you've got onboard video, you'll need to up the ram.

Agreed, 128 is the minimum required, so you will probably be swapping a lot, which is slow.  I suggest finding some more RAM or considering a lighter distribution like Puppy Linux or Damn Small Linux (DSL).
Use the alternate install cd if you go with xubuntu.

---

### Post by Dionysus135 on 2007-08-08
Sorry for asking another question but what is a file swap?Sorry again im a complete noob at ubuntu/linux.

---

### Post by oilchangeguy on 2007-08-08
> **Dionysus135 said:**
> Sorry for asking another question but what is a file swap?Sorry again im a complete noob at ubuntu/linux.

same thing as page file in windows. the os uses space on the hard drive to create virtual ram.

---

### Post by Rocket2DMn on 2007-08-08
> **oilchangeguy said:**
> same thing as page file in windows. the os uses space on the hard drive to create virtual ram.

It is also where memory is written when/if you use the hibernate function.  This takes everything from RAM and loads it onto the hard drive and shuts the computer off.   The next time you reboot it will load all that back into RAM without having to run the full bootup process, hence saving time - and your desktop will be exactly as it was when you went into hibernate.  Consider it like extreme standby mode.

---

### Post by Dionysus135 on 2007-08-08
Last question whats the difference between the LiveCD+Install CD and the alternate install CD besides how much ram it uses?Is there a difference on the graphics?

---

### Post by oilchangeguy on 2007-08-08
> **Dionysus135 said:**
> Last question whats the difference between the LiveCD+Install CD and the alternate install CD besides how much ram it uses?Is there a difference on the graphics?

the alt. cd uses a text based installer.

---

### Post by cobrn1 on 2007-08-08
if you use the alternate install CD, you will be able to install and use xubuntu at 128mb (hell you  can do it with ubuntu, but I wouldn't really recommend it...)

You may want to use GParted CD to do the partitioning graphically.

---

### Post by Dionysus135 on 2007-08-08
If its a text based installer will i get the same graphics like the livecd+install cd?

---

### Post by oilchangeguy on 2007-08-08
> **Dionysus135 said:**
> If its a text based installer will i get the same graphics like the livecd+install cd?

uh, no. not during the install process.

---

### Post by Dionysus135 on 2007-08-08
But i mean like the desktop and login screen in general.

---

### Post by cobrn1 on 2007-08-08
Once installed, yes you'll have all the normal graphics of a xubuntu desktop...

---

### Post by Rocket2DMn on 2007-08-08
After you install Xubuntu, everything should be fine, you will have the X-server (GUI) and all.

---

