---
title: "Trying to install this on my old laptop but with a few issues"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by dannyry on 2008-03-13
I have an IBM thinkpad r40 that was one of the first ibm centrino laptops, however it is from my college and I have a little dilemma.  Although they gave me a bunch of stuff with xp preinstalled, I had actually tried to reformat through the recovery system, seeing as that was the only option available (no dos prompt) and no dice.  I could not edit the size of the partition and choose to not install windows after the format.  So my school removed most of the passwords, however they do not give me the option to change the boot order, thus preventing me from installing linux.  

My question is, if I were to just buy a completely fresh 2.5" hd, and put it in, thus removing the hd with xp on it, shouldn't the bios bypass the HD as the primary boot device and then proceed to the cd-rom where ubuntu is housed, and then I can complete the installation process?  To me I think theoretically yes, but this is purely theoretical and would like an experienced user's opinion.

---

### Post by Foxray on 2008-03-13
It may not work if the cdrom drive is not even listed in the bios as a bootable device. If the cdrom entry is not even listed after the hard drive boot order you still may not be able to boot from the ubuntu disc unless you are able to get to the bios screen.

---

### Post by dokdoom on 2008-03-13
Are you assuming you don't have access to change the BIOS because you don't see an option to do so? Or were you explicitly told you do not have control over your own BIOS?

---

### Post by zxscooby on 2008-03-13
Some motherboards have a jumper to reset the bios password. 
maby you can find a schematic online.

---

### Post by dannyry on 2008-03-13
When I press f10 to change the boot device, only the hard drive is listed.  When I go to the bios setup, the startup options look like this

!+removable devices
+hard drive
!cd-rom drive

I can't change any of it either.  To me that looks like a priority list so I don't know.

---

### Post by dannyry on 2008-03-13
> **zxscooby said:**
> Some motherboards have a jumper to reset the bios password. 
maby you can find a schematic online.

the r40 requires a very risky and intricate hack to do so and it's not even guaranteed to work with my model.  so this is a no-go.

---

### Post by dannyry on 2008-03-13
anyone?

---

### Post by dannyry on 2008-03-13
this stuff moves to the 4th page quick; sorry for bumping my own thread but i feel someone knwos the answer to this and is just not online and afraid theyll miss it

---

### Post by CREEPING DEATH on 2008-03-14
You could try [Debian]("http://goodbye-microsoft.com/") if you're so inclined, it isn't so different.

CD

---

### Post by eriqjaffe on 2008-03-14
You could always install Ubuntu using WUBI and dual-boot.  Since it installs from within Windows, it'll work around the BIOS lockdown.

---

### Post by stalkingwolf on 2008-03-14
> **dannyry said:**
> When I press f10 to change the boot device, only the hard drive is listed.  When I go to the bios setup, the startup options look like this

!+removable devices
+hard drive
!cd-rom drive

I can't change any of it either.  To me that looks like a priority list so I don't know.

You may not need to change it.  I have a compaq 6310 that has a list like this.  I just select ( by using
the up or down arrow) which I want then hitting enter.  Maybe that will work for you.

---

### Post by dannyry on 2008-03-14
> **stalkingwolf said:**
> You may not need to change it.  I have a compaq 6310 that has a list like this.  I just select ( by using
the up or down arrow) which I want then hitting enter.  Maybe that will work for you.
I've already tried that; it does not work all I can do is observe this list.  There is no way to scroll up or down it, let alone move it around.

---

### Post by dannyry on 2008-03-14
thanks eriq, i've gotten it running now pretty easily.  i'm working on getting the startup time cut down now, as it's loading significantly slower than xp

---

