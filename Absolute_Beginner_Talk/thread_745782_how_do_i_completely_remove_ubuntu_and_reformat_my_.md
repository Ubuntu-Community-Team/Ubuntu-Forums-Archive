---
title: "how do i completely remove ubuntu and reformat my hard drive?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by pugofdestiny on 2008-04-04
how do i completely remove ubuntu and reformat my hard drive from ubuntu?

yes i want to completely REMOVE ubuntu and reformat my hard drive. how do i do this?

btw its not an external hard drive

---

### Post by Inxsible on 2008-04-04
Put in the live CD. Go to System>>Administration>>GParted and just format the drive to whatever filesystem you want. It will get rid of Ubuntu too.

---

### Post by pugofdestiny on 2008-04-04
> **Inxsible said:**
> Put in the live CD. Go to System>>Administration>>GParted and just format the drive to whatever filesystem you want. It will get rid of Ubuntu too.

thankyou

---

### Post by Tatty on 2008-04-04
Boot into a Live CD, run gparted (i think its under System->Administration->Gnome Partition Manager) and from there you can edit your partitions to your hearts content.

Just delete your ubuntu partitions and create any new partitions you would like to have.

**Edit:** Woah im slow, not only was i beaten to the post but the op even managed to thank the reply before i finished! lol :)

---

### Post by Inxsible on 2008-04-04
> **pugofdestiny said:**
> thankyouYou are welcome. Hope you decide to give it another chance :)

---

### Post by pugofdestiny on 2008-04-04
alright but say i cant boot into the live cd can i just browse th cd from my already installed ubuntu and find and run gparted?

---

### Post by Tatty on 2008-04-04
> **pugofdestiny said:**
> alright but say i cant boot into the live cd can i just browse th cd from my already installed ubuntu and find and run gparted?

No.  Your hard drive has to be unmounted before you can change the partitions.  So the only way to do this is to boot into a live CD first.

Are you having problems booting from CD?

---

### Post by JoshuaRL on 2008-04-04
[http://ubuntuforums.org/showthread.php?t=734329](http://ubuntuforums.org/showthread.php?t=734329)

A little backstory for everyone.

---

### Post by pugofdestiny on 2008-04-04
well you see im formatting my hd because something got messed up i have no clue what and i cant boot into my other os's anymore or live cd's etc because its as if my keyboard doesnt exist at startup until ubuntu boots which means cant browse in boot menu cant edit bios settings etc...

---

### Post by Tatty on 2008-04-04
> **pugofdestiny said:**
> well you see im formatting my hd because something got messed up i have no clue what and i cant boot into my other os's anymore or live cd's etc because its as if my keyboard doesnt exist at startup until ubuntu boots which means cant browse in boot menu cant edit bios settings etc...

This leads to a burning question... How did you install Ubuntu in the first place?

---

### Post by pugofdestiny on 2008-04-04
well i was able to before i installed it but then once it was installed it stopped working

---

### Post by Tatty on 2008-04-04
> **pugofdestiny said:**
> well i was able to before i installed it but then once it was installed it stopped working

Ubuntu loads after the BIOS, so there is no way installing ubuntu could have stopped the bios booting from CD or from loading a USB keyboard.

Aside from that im really not sure what to suggest next im afraid.  If you cant access the bios then theres nothing you can do.

There is no possible way to format your hard drive whilst it is mounted.

---

### Post by JoshuaRL on 2008-04-04
I would suggest you completely unplug the computer and pull out the CMOS battery to see if that will reset the BIOS.

Like Tatty said, Ubuntu doesn't affect the BIOS.

---

### Post by pugofdestiny on 2008-04-04
> **JoshuaRL said:**
> I would suggest you completely unplug the computer and pull out the CMOS battery to see if that will reset the BIOS.

Like Tatty said, Ubuntu doesn't affect the BIOS.

ummm whats the cmos battery i dont have a battery its a desktop not a laptop

---

### Post by Inxsible on 2008-04-04
Sometimes, just shutting down the computer for a couple of hours will also do the trick. 

I know I did that in one of my machines...and a couple of hours later it went thru the BIOS and gave me options of loading my OSes

---

### Post by Tatty on 2008-04-04
> **pugofdestiny said:**
> ummm whats the cmos battery i dont have a battery its a desktop not a laptop

Every motherboard has a battery on it... this is how it keeps the clock 'ticking' even when you turn your computer off.

open up your computer, locate the battery (it is small silver and roud) and pull it out.  leave it a minute or two to make sure all power discharges from teh system, put it back in and turn your computer on again.

[http://www.computerhope.net/issues/ch000239.htm]("http://www.computerhope.net/issues/ch000239.htm")

---

### Post by Inxsible on 2008-04-04
> **Tatty said:**
> Every motherboard has a battery on it... this is how it keeps the clock 'ticking' even when you turn your computer off.

open up your computer, locate the battery (it is small silver and roud) and pull it out.  leave it a minute or two to make sure all power discharges from teh system, put it back in and turn your computer on again.

[http://www.computerhope.net/issues/ch000239.htm](http://www.computerhope.net/issues/ch000239.htm)I don't think the op wants to do that, given that its a laptop.

Doing something like that will void all warranties on the machine.

---

### Post by Tatty on 2008-04-04
> **Inxsible said:**
> I don't think the op wants to do that, given that its a laptop.

Doing something like that will void all warranties on the machine.

he said its a desktop...

> **pugofdestiny said:**
> ummm whats the cmos battery i dont have a battery its a desktop not a laptop

:popcorn:

Though Inxsible does have a good point... you better check if your computer has any warrenties on it which prevent you from opening it before you do that.

---

### Post by JoshuaRL on 2008-04-04
> **pugofdestiny said:**
> ummm whats the cmos battery i dont have a battery its a desktop not a laptop

> **Inxsible said:**
> I don't think the op wants to do that, given that its a laptop.

Doing something like that will void all warranties on the machine.

Nope, fortunately its a desktop.  So taking the CMOS battery out won't be a deal.  Just make sure you have the computer unplugged while you do it just to be sure.  You're trying to take the power completely away from the BIOS so you can start it fresh.

---

### Post by Inxsible on 2008-04-04
> **Tatty said:**
> he said its a desktop...



:popcorn:

Though Inxsible does have a good point... you better check if your computer has any warrenties on it which prevent you from opening it before you do that.HAHAHA

I did read too fast there. Sorry Tatty

---

### Post by pugofdestiny on 2008-04-04
k ill try the turn off for a few hours idea and if that dont work ill take it into firedog so i dont void my warranty lol

---

### Post by diplomat.x on 2008-04-05
**Will only removing the CMOS battery for sometime reset the BIOS? He might have to do the jumpers too.....** ;)

[B]Pugofdestiny...have u assembled your computer or bought a branded one?

What are the specs.?[/B]

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-05
hey so you cant boot windows because you keybord dosent work until ubuntu is up all the way
so no grub selecting
wile ubuntu is up you can get in to the grub file and change witch one is the defalt that way you can boot windows 
now you can get drivers for windows to read and right to ext3 partions so install thoughs and then you just have to edit that file back to ubuntu when you would like to load that

ummm were is that file some thing with the grub i for get but i got to go to bead now so body will know or google it :)

---

