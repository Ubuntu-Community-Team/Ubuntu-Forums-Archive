---
title: "Advice for partitions and back-ups."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by DigitalRanger on 2007-03-06
Hi
I'm an XP user who is working towards making a complete switch over to FOSS.

I'm planning to install Feisty when it comes out. Currently toying with Edgy in VirtualBox.
(I'll be installing Feisty to the laptop in my signature, which means only one physical drive).

In the past with Windows I've experimented with putting my data and applications on different partitions, but in the end I have found it more convenient to have everything in one partition. Although at the same time, I maintain a strict backup regime.

I know in Linux that it's common to segregate things into separate partitions. So I'm posting here to ask for advice on how and why to partition the drive up into different sections.

I know I could go everything in /root plus /swap. Or the other common one is partition for /root, /home and /swap. Beyond the latter set-up, is there any more advantages to partitioning off for other system directories?

Speaking of all the other system directories (such as /var, /usr, /etc, etc). Could someone point me towards a guide on what all of these contain?

One last question, apart from backing up my personal data (which should all be within my home directory, yes?), are there any other locations that contain config files I'd benefit from backing up as well?

(BTW, I will either be backing up personal data to a DVDRW with UDFTools, or onto a 4GB USB stick. I also have an external Firewire drive to back up or mirror the whole hard drive to)

Thanks for reading, and apologies for any overly-newbish statements :)

---

### Post by mikewhatever on 2007-03-06
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Hope it is helpful.

---

### Post by randiroo76073 on 2007-03-06
I use the /root, /home, /swap combo for the simple reason that I'm muliti booted[14 distros], they all share /swap & have seperate /root & /home cause I do alot of fiddling with the distros, so my basic config is safe on all :)

---

### Post by DigitalRanger on 2007-03-07
> **randiroo76073 said:**
> I use the /root, /home, /swap combo for the simple reason that I'm muliti booted[14 distros], they all share /swap & have seperate /root & /home cause I do alot of fiddling with the distros, so my basic config is safe on all :)

When you say your "basic config" - do you just mean your own data?

Otherwise, I'd have thought basic config includes /usr/local/ too, or am I getting confused?

---

### Post by DigitalRanger on 2007-03-07
> **mikewhatever said:**
> [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

Hope it is helpful.

They have been a great help, thank you.

I'd already seen the psychocats page, which is where I got the idea of separate partitions for root and /home, but she doesn't suggest partitioning other directories off.

The tuxfiles site is great, I'm having a good read around the whole site.

---

