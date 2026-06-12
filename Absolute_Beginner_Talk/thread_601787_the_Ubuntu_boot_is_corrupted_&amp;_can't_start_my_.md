---
title: "the Ubuntu boot is corrupted &amp; can't start my PC"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by nichos on 2007-11-03
I loaded Ubuntu on my XP pro PC & worked fine, but is very frastrating to find my way around things.

Then  stupitly tried to decrease the Ubuntu partition size & corrupted the boot & can't start my PC.

When it starts says:-
GRUB Loading Stage 1.5
     "-----"          play wait (or something)
Error 17

Then I run the CD ubuntu, & in Terminal I type this:- sudo gedit /boot/grub/menu.lst     

which in turn opens :-

"menu.lst (boot/grub)-getid"  window with a small file icon in it on the left but will not open to show me the boot sequence to see if it can be corrected.

When I click the icon says:- Mime Type plain text, & Encoding Unicote NTF

Can anybody help me to get my computer back?

If I could be sure, in The CD Ubuntu, which is its directory on my HD I would try to delete hoping my PC would be free to start XP.

Thanx                    nick

---

### Post by akiratheoni on 2007-11-03
I think you mean the LiveCD, right? 

If I recall correctly, you will need to mount your hard drive on the LiveCD before editing the menu.lst.

---

### Post by sandysandy on 2007-11-03
> **akiratheoni said:**
> I think you mean the LiveCD, right? 

If I recall correctly, you will need to mount your hard drive on the LiveCD before editing the menu.lst.

the code for mounting the hard drive (assuming sda is ur ubuntu hard disk):-

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst

regards

---

### Post by defrex on 2007-11-03
If your getting grub error 17 then editing menu.list probably won't fix the problem. I would say you need to reinstall Ubuntu. You can use the mount instructions above to recover what data can be recovered first, if there's anything you need.

---

### Post by Duck2006 on 2007-11-03
Run the live CD and in the terminal type

sudo fdisk -l

and post the output.

---

### Post by nichos on 2007-11-03
Thanx gents,
I will do all the bits you instructed and post again, AFTER I recover from the shock of loosing all from my stupidity.

Because am a bit familiar with XP, as somebody sugested, I booted from the XP cd, used R>fixmbr>fixboot & by the grace of God it booted in XP & lost nothing.

I would like to learn how to use Ubuntu but what are all those #### and other jiberys printed about in the forum instructions?. 

I need an idiot's approach to learn.

Is this Gutsy much more easier to use?                        nick

---

