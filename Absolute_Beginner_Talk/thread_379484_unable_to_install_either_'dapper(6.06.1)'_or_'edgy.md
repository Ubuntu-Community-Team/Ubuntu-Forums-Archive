---
title: "unable to install either 'dapper(6.06.1)' or 'edgy(6.10)'"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by rks_i1_13 on 2007-03-08
First of all...HELLO to all the community of Ubuntu as this is my first post :) 

I am new to linux, and i am facing certain problems during installation. My PC configuration is as follows:-

Processor:-              Intel Core 2 Duo - 2.13 GHz
Motherboard:-          Intel DG965
RAM:-                     2 GB
Graphics Card:-         MSI Nvidia GeForce 7950GT, 512MB DDR3 RAM
Hard-Disk:-              160 GB  ( currently only 60 GB is formatted on which Windows XP is there)

i have downloaded and burned installation CD's for both 'Dapper Drake'(6.06.1) and 'edgy eft'(6.10) , but was unable to install even after this :( 

- On installing 'edgy eft'(6.10) i got this error (this one is pretty popular on the internet!):-

'can't acces tty'

-On trying 'dapper drake'(6.06.1) i got the following message:-

[17179572.584000] PCI:Failed to allocate mem resource #6:20000@90000000 for 0000:01:00.0

------------------------------------------------------------------------------------------------------------------------

Thanks in advance to anyone who can tell me the solution or at least hint me about anything so that i can search ubuntu website or google 'effectively'. I am desperate to get Ubuntu...WinXP doesn't appeal to me :)

---

### Post by ridgeone on 2007-03-08
I seem to remember seing more on this subject. 

> Re: Any idea on support for Intel 965 chipset? 

--------------------------------------------------------------------------------

The problems are not directly related to the 965 chipset, but rather to the often used JMicron controller alongside the IDE-less ICH8(R) southbridge.

Check the forum for JMicron-related problems.

---

### Post by wpshooter on 2007-03-08
Rks:

First, have you check the integrity of your Ubuntu CDs by running the verification function that is found on the initial Ubuntu boot screen menu ?

I would say that the first problem, at least, is video card related.

Have you tried booting using the safe video mode parameter or have you tried manually specifying a video mode using the F4 key at bootup ?

If neither of these work for you I would suggest that you download and burn the ALTERNATE CDs of both Dapper and Edgy and try the text based install which is supposed to be somewhat more comprehensive/reliable.

My recommendation would be that you stick with Dapper, at least, for the time being.

Write back if you need further help.

Good luck.

---

### Post by ~chinook~ on 2007-03-08
TTY is a cd error I think. It happened to me on my first burn. It worked perfectly on the second one.

---

### Post by rks_i1_13 on 2007-03-08
Thank u guys for such a rapid answer, but....

I get those errors even if i check CD integrity. I have tried safe graphics mode too....but still no results.

Now i'm gonna try ALTERNATE CD's

---

### Post by juice99 on 2007-03-08
i got the same problem and it has nothing to do with CD integrity.

you might be able to install dapper-alternative, but the only one i was able to use was dapper + Installation from USB, then upgraded it to edgy and feisty.

Ubuntu is bugged and doesnt support JMicron/ICH8 , try another distribution (debian works fine) or wait for fix.

---

### Post by bwallum on 2007-03-08
Hiya, I've just been down your way a couple of days ago. Peed off with XP too, I burnt Edgy and went to install. It got to the end and hung. I recall a two button option to restart or continue to use the CD boot. You can wait as long as you like for something to happen at this stage and it doesn't.

This will appear completely illogical but it worked. Switch off your machine to clear the hang. Switch on again after a minute or so and get into your cmos setup. Fiddle with the harddrive settings and leave as auto detect. Back up (Save) your MBR if you have that option. Save changes and exit. Reboot and up pops Ubuntu. You'll find quite a few people have been through this loop. I think it may have something to do with clean installs on newly formatted harddrives where the harddrive has not had a low level format, just a high level one.

I've just got streamed video going if you run into that prob further downstream. Half way to hooking up an ipod and now looking to set up 'skype'. Its worth the learning curve, by the way. Hope that helps.

---

### Post by rks_i1_13 on 2007-03-09
Thanks for the advice....i have done a little hardware fiddling in the cmos...though not like the one 'bwallum' said above.

In the supported hardware list for ubuntu 'edgy(6.10)' , **"nVidia 7950"** was **NOT** mentioned in video cards section. I am afraid whether this has something to do with this.

Also, my hard-drive is SATA and i have read somewhere in this forum (by searching for keywords:- 'can't access tty') that it may be responsible for that.

....ubuntu will run on my pc someday....today...or tommorrow...... :) 

Thanks again for the replies, i have got more from this forum that what i expected. :)

---

### Post by alex77 on 2007-03-20
JMicron is the culprit. I am having the [exact same problems as you]("http://www.ubuntuforums.org/showthread.php?t=376762&highlight=p5w+dh+jmicron")

I keep looking for a fix or workround for this... If you find one, please let me know!

---

### Post by alex77 on 2007-03-23
my problem solved. maybe will fix yours too?

> At install with edgy you have to add :
irqpoll noapic nolapic
before "--" to kernel options

At first boot after install when you see grub menu :
press e
select the kernel line, go to the end of it and add the same sequence
press ENTER
press b

When boot is done from a terminal or console, do :
sudo nano /boot/grub/menu.lst
edit this line :
# defoptions=ro quiet splash
so it looks like this :
# defoptions=ro quiet splash irqpoll noapic nolapic
CTRL + O
CTRL + X
then type :
sudo update-grub

Now edgy will always boot with the required sequence you added

You're done


---

