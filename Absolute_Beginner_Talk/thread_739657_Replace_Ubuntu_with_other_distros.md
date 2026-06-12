---
title: "Replace Ubuntu with other distros ?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by xxxamazexxx on 2008-03-29
Sad as it is, I've got enough awful experience with Ubuntu. I was about to remove it straight away before deciding to give Linux a second try. Now I wish to install Fedora to replace Ubuntu right on the ext partition where Ubuntu was installed. What I concern is ifl the Fedora bootloader works properly after this replacement. Before installing Fedora will format the whole Ubuntu partition and the configuration of Ubuntu's GRUB as well, after that it will install its own bootloader. May there be any conflict ? Or should I try uninstalling Ubuntu first ?

---

### Post by herbster on 2008-03-29
If you format the partition, install Fedora and then install the new bootloader, you're overwriting whatever's there. None of the current data/bootloader will remain.

---

### Post by xxxamazexxx on 2008-03-29
Yes. So it is alright, I suppose ?

---

### Post by herbster on 2008-03-29
Of course, so long as you are installing to the same partition with regards to the OS AND the bootloader (if Ubuntu was on /dev/sda1, you'd install Fedora to /dev/sda1 and the bootloader to /dev/sda).

---

### Post by Saint Angeles on 2008-03-29
everything should work as well as fedora says it does...

i totally recommend trying ubuntu again (hardy heron) because rpm distros (as opposed to deb) are a little more dificult to maintain.

if you don't mind, could we convince you to try ubuntu again?

---

### Post by iSplicer on 2008-03-29
Before switching to Fedora, why not make use of (in my opinion) Ubuntu's  best feature -> community support before switching to fedora? What problems occured? Its natural to have problems, 99.9% of them can be solved =)

---

### Post by dcstar on 2008-03-29
> **xxxamazexxx said:**
> Sad as it is, I've got enough awful experience with Ubuntu. I was about to remove it straight away before deciding to give Linux a second try. Now I wish to install Fedora to replace Ubuntu right on the ext partition where Ubuntu was installed. What I concern is ifl the Fedora bootloader works properly after this replacement. Before installing Fedora will format the whole Ubuntu partition and the configuration of Ubuntu's GRUB as well, after that it will install its own bootloader. May there be any conflict ? Or should I try uninstalling Ubuntu first ?

As an option for anyone wanting to evaluate/use other OS's, I recommend installing VMware Server and then installing other distros as VMs.

I have 4 other Ubuntu releases, OpenSUSE and Mandriva all installed as VMs so I can see all the different desktops and features easily - I even have enough grunt in my underlying Ubuntu system to have them all running simultaneously.

They all have their strengths and weaknesses, but the standard Ubuntu install stands up pretty well when it comes to ease of installation and "out of the box" functionality - both vital for inexperienced Linux users.

---

### Post by xxxamazexxx on 2008-03-30
Thank you guys who have replied me or are going to do so very much :X
Actually at first I thought Ubuntu was quite pleasing. But it doesn't detect my sound card and graphic card (whilst I listen to music most of the time my computer is on). Then I tried to install driver for my Mobile Intel (R) 965 Express Family Chipset. It was probably the wrong driver, but somehow I couldn't revert it. Even minimal desktop effect can't be activated.
Trouble continued to haunt me when I tried to install driver for my sound card. I found that another guy in the forum has the same sound card as me and succeeded in installing it. I followed his steps, everything seemed perfect. But at the end of the installing my computer crashed. Not the kind of crashing experience in Windows like Blue screen of death, Ubuntu crashed 'peacefully'. However, unlike Windows which crashes frequently but always reports correct error and recovers, my Ubuntu after restarting displayed a puzzling error notice: YOUR LAST SESSION LASTED FOR LESS THAN 10 MINUTES BLAH BLAH BLAH TRY FAILSAFE SESSION BLAH BLAH BLAH .. I did try, but the outcome remained the same.
And that means now I can't go any further with Ubuntu than the logon screen.
One of my cousin installed Fedora on his laptop and everything works. I wonder if I should give it a try. After all Linux are the best, just that the hardware compatibility is simply insufficient.

---

