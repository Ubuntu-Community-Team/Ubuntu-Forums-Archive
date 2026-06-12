---
title: "Hard disk power saving features"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by zyberwoof on 2006-08-02
I have two PCs, one with Ubuntu and one with xubuntu.  If there is a way to, how do I set up those computers to perform like the Windows power saving features?  

My biggest desire is to be able to shut down hard drives that have been idol for a while.  Features like system standby and monitor standby would be helpful too.


Also a random question... are there any weekly or monthly newsletter type things out for Ubuntu?  I am really new to the Linux enviornment (like most people in this forum) and the 100's of documents, webpages, wiki's, man pages, forums, ect. can be overwhelming.  Something that basicly brings you random good information instead of relying on you finding it yourself is what I mean.

---

### Post by sparkov on 2006-10-24
*bump*

I'd also like to know if this is possible, i.e. can the hard drives be set to power down after a period of inactivity?

---

### Post by jdong on 2006-10-24
See /etc/hdparm.conf, and also /etc/laptop-mode/laptop-mode.conf.... In short, by editing one of the two files above, it is possible to configure your hard drives to spin down.

However, there isn't really much to be gained from it. Hard disks use very little power in comparison to the display, the CPU, or any other subsystem. In fact, it's most power-inefficient when spinning up, so repeated spinups can actually reduce battery life.

For a more etailed explanation of why hard disk spindown isn't as good as it sounds, see: [http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-spin-down-hdd](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-spin-down-hdd)

---

### Post by hank_freid on 2008-04-04
It is possible to set it for Power Saving Features but it is very difficult to teach you in this short span of time. I will try me best to have visual aids to solve your problem. If you contact me on chatting then i will easily solve out your problem

---

### Post by jdong on 2008-04-04
As I mentioned above, keeping the hard disk spinned doens't take much power -- your laptop battery can do that for 50 hours.

However, spinning up a spun-down hard drive is VERY costly in terms of power usage. Spinning down the hard drive will end up costing you more battery life than you save unless your entire OS is primarily loaded into RAM, which is certainly not the case with the default Ubuntu setup unless you have a laptop with ridiculous amounts of RAM.

---

