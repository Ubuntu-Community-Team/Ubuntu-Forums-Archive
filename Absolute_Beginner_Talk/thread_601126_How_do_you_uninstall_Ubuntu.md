---
title: "How do you uninstall Ubuntu"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2007-11-02
I know how to repartition and reformat the hard disk that Ubuntu is on. The question I have is that I have a dual boot system. Windows is on my C: drive and if we are talking windows Ubuntu would be on my D: drive. What about the boot manager that Ubuntu installs. Does that go away too? If not how do I get rid of it. 

Actually what I want to do is take another look at PCLOS and Mepis but as I was typing I think I thought of the answer to how to do that. I think both are live CD's. 

Still I would like to know the answer to the boot manager question.

---

### Post by overdrank on 2007-11-02
> **bgast1 said:**
> I know how to repartition and reformat the hard disk that Ubuntu is on. The question I have is that I have a dual boot system. Windows is on my C: drive and if we are talking windows Ubuntu would be on my D: drive. What about the boot manager that Ubuntu installs. Does that go away too? If not how do I get rid of it. 

Actually what I want to do is take another look at PCLOS and Mepis but as I was typing I think I thought of the answer to how to do that. I think both are live CD's. 

Still I would like to know the answer to the boot manager question.

Hi maybe this link will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Good luck! :KS

---

### Post by mookie_jones on 2007-11-02
oh snap! i think i got the answer


put in an old win98 cd or anything of the sort and let it boot to DOS

then you wanna type fdisk /mbr

this will repair the master boot record so that only windows is booted

---

### Post by Six_Digits on 2007-11-02
Thanks mookie, I need this about 6 months ago...... GRUB

---

### Post by AzaleaP on 2007-11-02
Is it really safe to use "fdisk"?

And how do you boot to DOS? Now that Ubuntu is installed, instead of running off the cd, I can't "Boot from CD" anymore. If I hold down "enter" it goes straight to Ubuntu without asking.

I need to boot Windows in Safe Mode  so I can attempt to change the 'policy' that is locking me out. (I am the only user of this machine!)

What can I change in Ubuntu to get back the Windows master boot record? (If that is what I need to do.)

If there is nothing to do then what do I do to get Ubuntu off _logical_ disk hda2 or D?

Azalea

---

