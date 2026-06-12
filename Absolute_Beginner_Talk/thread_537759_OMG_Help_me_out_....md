---
title: "OMG Help me out ..."
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by rohit88 on 2007-08-29
I Finally decided to install ubuntu....I am keeping it on dual with XP

I did that boot from cd nd all things....Then there were a installing menu..
i selected start and install option...AND AFter that it poped up this message..


[ 40.41129]..MP-BIOS bug:8254 timer not connected to IO-APIC
[ 40.41129] kernel panic -not syncing :IO-APIC +timer doesn't work!boot with apic-debug and send a report.Then try booting with 'noapic'
option
[ 40.591247]



what shall i do????
ma machine config-amd64 5000+
                  2gb ram 250hd asus m2nmx mb


can ne1 help me out ??please:(

---

### Post by LaRoza on 2007-08-29
When booting form the live cd, press F6 and then type "noapic". Press enter.

then install.

---

### Post by tchoklat on 2007-08-29
When you get the menu list, choose the option that allows you to add a command to the boot line. Add the command <noapic> without the <>
 
 
Should work.
 
 
tchoklat

---

### Post by rohit88 on 2007-08-29
is it that simple???

---

### Post by LaRoza on 2007-08-29
> **rohit88 said:**
> is it that simple???

Yep.

---

### Post by rohit88 on 2007-08-29
I'm askin cause i m sittin at cafe ...So i have to go home nd do this things 
so will it work??

---

### Post by rohit88 on 2007-08-29
Thanks guys

---

### Post by LaRoza on 2007-08-29
> **rohit88 said:**
> I'm askin cause i m sittin at cafe ...So i have to go home nd do this things 
so will it work??

Yes, it is a common issue.

You just have to pass the extra parameter to the kernel.

You'll see a difference in the above advices, they do the same, just mine starts the cd with the option which will pass on to the installation, and the other just installs with the option. It doesn't matter which one you follow, but if you booting from the cd, the first will be easier.

---

### Post by asathorny on 2007-08-29
Hi Rohit.

I also am a newbie and had some worries with the live CD install, then after some  research switched to the TXT install.  This does not answer your question, that has already been dealt with by someone far more knowledgeable than I, however this info may be of some interest to you.

good luck
asathorny

---

### Post by LaRoza on 2007-08-29
> **asathorny said:**
> Hi Rohit.

I also am a newbie and had some worries with the live CD install, then after some  research switched to the TXT install.  This does not answer your question, that has already been dealt with by someone far more knowledgeable than I, however this info may be of some interest to you.

good luck
asathorny

Text install solve some problems, but not this one. 

If the cd boots and runs, a graphic install is best, for a beginner.

---

### Post by asmoore82 on 2007-08-29
FYI...

[http://ubuntuforums.org/showpost.php?p=3000074&postcount=3](http://ubuntuforums.org/showpost.php?p=3000074&postcount=3)

---

