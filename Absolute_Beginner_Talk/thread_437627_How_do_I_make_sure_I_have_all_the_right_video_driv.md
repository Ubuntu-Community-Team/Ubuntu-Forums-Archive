---
title: "How do I make sure I have all the right video drivers?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-05-09
I have an ATI Radeon 9200.  The ubuntu desktop works fine for me.  However, when I get into anything that involves 3D graphics, ie World of Padman, everything is messed up, models, textures dont show up.  This isnt just a particular instance though, other 3D games have the same problem.  I'm fairly positive that this isnt a processing power problem seeing as I could run far more graphically intensive programs back when I used Windows, but just in case, these are my specs:

AMD Sempron 1.83 GHz
512 RAM
ATI Radeon 9200 (as mentioned above)

My question is, how can I check if I have all the latest drivers installed, and if not, how do I go about installing them?  (Preferably with a GUI since I'm unfamiliar with the terminal)

Thanks for taking the time to look.

---

### Post by jargoman on 2007-05-09
System >> Administration >> Restricted Drivers Manager

this will install the ati proprietary drivers. this is probably the easiest way. 

you should read this page. It's a how to for setting up beryl window manager but it has pertinent information about ATI cards

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by Brucey on 2007-05-09
When I try to use the Restricted Drivers Manager it gives me the error:

You need to install the package

  linux-restricted-modules-2.6.20-15-generic

for this program to work.

How do I do that?

---

### Post by mills on 2007-05-09
you can get the modules in synaptic 

or

sudo aptitude install linux-restricted-modules-2.6.20-15-generic

should work

---

