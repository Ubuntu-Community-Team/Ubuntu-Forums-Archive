---
title: "Boot Menu Problems"
date: 2007-05-03
forum: Apple PPC Users
---

### Post by edekba on 2007-05-03
Hi, I recently tried to get my feet wet in Ubuntu and thus decided to format my powerbook g4. I first reinstalled Mac OS X 10.4 using Disk Utilities to format my 60gb hdd into two partitions. Once it worked and I got OS X up and running i installed ubuntu onto the 2nd partition. 

That worked nicely and i saw the boot menu selection which i thought would be perfect, since it allowed me to type either "l" for linux, "c" to boot via cd or another command to go into mac os x. I first decided to config ubuntu and i got to install some applications for ubuntu and configured some of the settings. However since i needed to do some work on my laptop and i knew i wasnt profient with ubuntu yet, i went back into OS X and made sure everything in OS X worked to my liking.

This is when the problem started occuring. After installing the update to 10.4.9 and i rebooted, the boot menu doesnt come up any more. I try hitting "l" while booting and it still cant get to boot into ubuntu. Is there something I did wrong? Did the 10.4.9 update overwrite the bootmenu thing?

Basically how can I get back into my ubuntu? 

Thanks!

---

### Post by Auria on 2007-05-03
To get back into ubuntu, hold down the alt key during startup. it will shw you a list of bootable systems.

to get back the old menu, you'll need to reinstall yaboot, i don't remember the command though

---

### Post by Auria on 2007-05-03
I found the commands you must run here:
[http://www.gentoo.org/doc/fr/handbook/hb-install-ppc-bootloader.xml?glang=fr](http://www.gentoo.org/doc/fr/handbook/hb-install-ppc-bootloader.xml?glang=fr)

its in french though

bascially its

mkofboot -v

to replace apple's boot loader by yaboot and

ybin -v

to update boot laoder when you change config info. As always use with care since we're dealing boot laoders.

---

### Post by edekba on 2007-05-03
thanks! I'll try that right now. Hopefully it works.

---

### Post by edekba on 2007-05-03
Thanks that works fine. It doesnt seem to need yaboot reinstalled though. It works fine, i just gotta hold alt when I want the boot menu.

Thanks again

---

### Post by airbon on 2007-05-20
I am having an ibook G3 600Mhz. I too was not able to see the boot menu at bootup. But by pressing the alt button doesnot work for me. I try the mkofboot and the ybin , it doesnot work either. can anyone help

---

### Post by stmiller on 2007-05-20
Boot into Linux via holding the Alt key, then run

$ sudo yabootconfig

press Enter for all prompts questioned.

That will complete.

and then do:

$ sudo ybin -v

Enter.

to repair yaboot.

---

### Post by airbon on 2007-05-21
I try the sudo yabootconfig, but i get no such file or directory.

---

