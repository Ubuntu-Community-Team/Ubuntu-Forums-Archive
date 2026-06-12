---
title: "Mac Mini ppc boot from pc"
date: 2012-04-08
forum: Apple Hardware Users
---

### Post by Counder on 2012-04-08
Hey, 
I just got an old Mac mini with Ubuntu 10.10 installed. Username and password unknown so right now this Mac is not usable. I do have the original Mac os 9 and os x install disc but I am not able to get it to boot from the cd. I don't care if I can install another Ubuntu or Mac os x,  I just want to be able to use this computer again. :)
Pressing the c button doesn't do anything. I have also tried to boot from another Ubuntu cd, but it s the same problem. It says yaboot version 1.1.13, but when I enter boot: cd it says 
/pci@4000000/ata-6@d/disk@0:3.\\cd: no such file or directory
Any kind of help is greatly appreciated! :)
Thanks.

---

### Post by Mk32 on 2012-04-08
Do you have another Mac with FireWire ports? 

You could try restarting with Target Disk mode, although that depends on what you'd like to do: is there critical information on it?

Does it show the GRUB 2 boot menu?

---

### Post by Counder on 2012-04-09
I don't have one but I could try to get one in the next few weeks..
Could I access the computer with another Mac?
There is no critical information on it and I haven't seen the grub loader.
What's target disc mode?
Thanks for your help.

---

### Post by rsavage on 2012-04-09
You won't have grub, you have yaboot.
 
If you've got a standard ubuntu installation then you can boot a cd by pressing 'c' when prompted.  If you are not prompted then you can hold 'c' when you turn the computer on.  Keep it pressed until you hear the cd booting.
 
If that doesn't work then you can try resetting the pram.
 
It is possible though to change the password of your ubuntu user account.  See [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) .  You have to adjust the instructions slightly because you don't have grub.  At the yaboot prompt type:
 
Linux single
 
and choose the "drop to a root shell prompt" option when you eventually get it.

---

### Post by Counder on 2012-04-09
Thanks!! That worked out great :-)
I changed the password and am now able to login. I installed kde but now I can't find the cd drive. Maybe it didn't install the correct driver for that drive?  That would also explain why I wasn't able to boot from my cd. Any ideas what I can do?
Thanks again! :)


Edit: nevermind: I inserted a DVD movie and it recognized it. So it seems to be a problem with the Mac os cd.
Since Ubuntu is running so slow right now I kind of want to go back to Mac os. I have a Mac os 9 install disc and a Mac os x install disc but none of them seems to be able to get booted. Any ideas on how I can install either Mac os or a smoother version of Ubuntu?

---

