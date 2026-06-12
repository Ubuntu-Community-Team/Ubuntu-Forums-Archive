---
title: "Now what?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by pixiesnoot on 2008-04-16
I downloaded ubuntu onto my computer, and put it on my desktop because i didn't know where else to put it? where should i put it so that it works? or is my desktop ok?

---

### Post by northern lights on 2008-04-16
On what desktop did you put what?

Should you have downloaded an .iso and put it on your Windows desktop -  that ain't gonna do jack sh*t.

1. Burn the .iso
2. Reboot
3. Boot from the just burned CD
4. Install Ubuntu

---

### Post by pixiesnoot on 2008-04-16
Thanks, but is there a way to do it without burning it? i have nothing to burn it onto :P, and yes, i put it on the windows desktop

---

### Post by northern lights on 2008-04-16
Please don't feel offended if I ask this question, but since you had been asking "where to put it":
Do you realize Ubuntu is an OS, just like Tiger, Leopard, XP or Vista?!

mkey. Now your question:
Yes, it can be installed without burning. Either from a USB/flash drive, or from the net. The latter I have done and will describe here:

Navigate to [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411") and download one of the two .exe files, depending on whether you've got a 32 or 64 bit system. Run  (double-click) the .exe from, for instance your windows desktop. Reboot. A bootmenu should pop up, giving you the choice to start windows or install Ubuntu. Good luck.

P.S. It might be an idea to wait till the 24th of April, as the newest stable (comes every half a year) will be out as of that day...

---

### Post by Tom--d on 2008-04-16
Do you have a blank CD? or DVD? 
Do you have a CD/DVD burner? 

Do you know how to boot into? 

Look here for more information [http://ubuntuforums.org/showthread.php?t=706813]("http://ubuntuforums.org/showthread.php?t=706813")

Anymore help just post back in here :)

---

### Post by pixiesnoot on 2008-04-16
i downloaded the thing off of sourceforge and rebooted, and then it did ask me which i wanted to use, once i hit the ubuntu one a bunch of white words flashed down the screen and then it just stopped. the last couple things it said were "boot with apic=debug and send a report. Then try booting with the 'noapic option." i eventually hit restart on my computer. The second time it didn't give me a choice, and it said "are you sure you want to completely remove unetbootin ubuntu710rev113 and all of it's components?". I hit no. any ideas on how i can get this to work? thx for trying to help, btw

---

### Post by Tom--d on 2008-04-16
I got a better Idea: 

**you will need RAM. I recommend 1GB of ram. Any lower - Dont do it.**
Download VirtualBox [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI")

Chose your OS and is its 32bit or 64bit.
Install it. 
Run Vitualbox then click New and follow the steps. (Ubuntu is Linux 2.6 in Vitualbox)

Once created your vitual machine. Chick it and go onto settings. Go to CD/DVD rom > Mount CD/DVD rom > ISO image > Find the image and add it. 
Also, make sure the RAM for the Virtual Machine is over 400mb (or just have it at 400mb) 

Then ok. 
After that just click Start and it will load. 

Its straight forward after that :)

---

### Post by pixiesnoot on 2008-04-16
I have enough RAM. For the OS, would that be Windows x86? I have windows xp

---

### Post by Paqman on 2008-04-16
When you get to the boot menu hit F6 and add the bit it suggests: 
```

noapic

```

After the word splash. It might also help to change "quiet splash" to "nosplash". It won't look as pretty, but it'll tell you a lot more about why it isn't booting.

---

### Post by Tom--d on 2008-04-16
To find out if you are running 32bit (x86) or 64bit Windows.. 

Press Windows key + pause/break (it shows your system spec)

If it doesn't say anywhere there that you are using 64bit that means you are on 32bit Windows. (which it generaly is) 
If it says 64bit, then you are running 64bit windows.

---

### Post by pixiesnoot on 2008-04-16
I tried, both, F6 didn't seem to do anything and I tried to install the virtualbox. it says It hasn't passed testing to verify that its compatible with windows. it could seriously mess things up. any other ideas?

---

### Post by pixiesnoot on 2008-04-16
oops, i messed up and submitted the message twice.

---

### Post by pixiesnoot on 2008-04-16
I'm running a 32 bit and got the x86 version

---

### Post by tvtech on 2008-04-16
okay can I for suggestions sake suggest WUBI  what a great concept install it without installing it.  HAVE FUN check it out if you love it wipe windows away and send a nasty letter to M$cr0suX
if you hate it then your clearly not a geek and must re-evaluate your position in life. 

[[COLOR="Red"][SIZE="7"]WUBI!!!![/SIZE][/COLOR]]("http://wubi-installer.org/")

---

### Post by pixiesnoot on 2008-04-16
thanks, now I'm waiting for it to install. hopefully this works. I've been trying for too long

---

### Post by tvtech on 2008-04-16
did you get wubi?   wubi is the easiest way to linux.  well of course theres also [cygwin]("http://www.cygwin.com/")  but it's really more for running linux programs in a windows api environment.  Now who in their right mind would do that when you can just run windows in vmware under linux!

---

### Post by pixiesnoot on 2008-04-16
yay, it worked!! thanks everyone

---

### Post by Tom--d on 2008-04-16
Wubi does seem better than virtual box under windows :)

---

