---
title: "Driver help"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Superfiend on 2006-01-08
I looked around, but could not find out how to do this...

I am extremely new to Ubuntu...love it, except for one problem...it doesn't recognize my onboard ethernet port.  I found linux drivers for it, but don't know how to install them.  There is a set of install instructions that came with the drivers, but where do I type those in at? thanks

---

### Post by Terry of Astoria on 2006-01-08
What is your card model? And where did you get those drivers? 
Tell us more about your problem. Someone will help.
This is a nice sort of challenge. Not insurmountable if the drivers are good!

---

### Post by Superfiend on 2006-01-08
Sorry, i knew i was forgetting something....The card is an IC Plus IP1000...it is the onboard for my Abit AX8.

I googled Linux drivers for it and came up with a hit.

it says the drivers are good for Linux kernels 2.4 and 2.6

---

### Post by Superfiend on 2006-01-08
okay, maybe this will help.

I'm pretty sure i need to type in the instructions in Terminal
but when i do it does nothing

here is what comes wtih the driver
----------------------------------
#make all  => generate ipg.ko
#insmod ./ipg.ko
#ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy

eth0 is your network adapter,use "dmesg" to check it, ex: eth0,eth1...
xxx  is your ip address, ex: 192.168.102.211
yyy  is your netmask address, ex:255.255.255.0 


what do I do with this?

---

### Post by Arktis on 2006-01-08
Please post the link for the driver; I can very likely tell you exactly what to do with it if I can have a look.

---

### Post by Superfiend on 2006-01-08
[http://www.icplus.com.tw/driver-pp-IP1000A.html](http://www.icplus.com.tw/driver-pp-IP1000A.html)

---

### Post by Superfiend on 2006-01-09
anyone?

---

### Post by Arktis on 2006-01-09
Okay.  No configure script, but that's not unusual.

Assuming you didn't disable the CD in your repositories list, insert the CD you used to install ubuntu and open a terminal:```
sudo apt-get install build-essential
```Then do ```
sudo apt-get install linux-headers-2.6.12-10-386
``` making sure that you replace 2.6.12-10-386 with YOUR kernel version.  Then in nautilus, go to where you downloaded the driver archive, right click it and extract it.  Go back to the terminal and cd to where you extracted the archive.  Now do```
make all
```and then test it with ```
sudo insmod ./ipg.ko
```  Go to System > Administration > Networking and I believe you should now be able to configure your ethernet.  Keep that terminal open.

If I actually HAD this hardware I'd be a little more certain, but I believe it *should* work this way.  But it's only temporary.  You'll need to run ```
sudo make install
``` and then add a line to a startup script somewhere... I'm checking that out now.

**EDIT:** [color=darkred]Okay, I really don't know which file to edit here.  But I do know you would need to add something like **insmod /lib/modules/2.6.12-10-386/kernel/drivers/net/ipg.ko** to one of your startup scripts, again making sure to replace 2.6.12-10-386 with YOUR kernel version.

Can anyone tell us what the right file to add this to is?[/color]

---

### Post by Superfiend on 2006-01-09
thanks, i'll give it a shot

---

### Post by Arktis on 2006-01-09
I did some heavy editing there.  The instructions are missing the final step because I don't know what file to edit, but at least you still have the ability to test the driver!  The alternative to not editing the proper startup script is that you'll have to manualy insert the module each time you reboot.  Anyways, let me know if it works.

---

### Post by Superfiend on 2006-01-09
okay, how do I edit the startup script?

---

### Post by Arktis on 2006-01-09
I don't know, bud.  I don't know which script it is.  Did the driver work when you ran the insmod ./igp.ko command, though?

---

### Post by Superfiend on 2006-01-10
no, the make command didn't work...said something about the directory not existing....i was in the directory where I unpacked the file.

---

### Post by Arktis on 2006-01-10
Okay, post the exact ouput it gives.

---

### Post by bsh on 2008-07-08
dunno if anyone is still interested in this, but i have the same card (piece of ****, useless crap) and i got slow speeds over gigabit lan, plus no support for ethtool...
then i decided i try out the newer driver that is available.
followed the instructions.
could not install the new driver, got some error messages about "file exists" or something.
could not get this to work.

then i used the brute approach... :)
removed the kernel module first.
then i found the existing ipkg.ko file in the filesystem, and removed it :)
then copied the new, compiled file to the same place.
installed the module as in the instructions...
and voila, it worked! the new driver is in use.

however, it did not solve my speed issues and still not supporting ethtool... :(

---

