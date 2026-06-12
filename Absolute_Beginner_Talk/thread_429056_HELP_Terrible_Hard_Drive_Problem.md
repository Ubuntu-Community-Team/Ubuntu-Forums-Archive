---
title: "HELP Terrible Hard Drive Problem"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-04-30
Hey,

I recently installed Ubuntu 7.04 on my computer on which I am also running Windows.  I was just 'playing around' when I put it on, just to experiment with Ubuntu... But, the hard drive on which I installed Ubuntu has recently been failing A LOT.  It doesn't bother me as much, as long as I can boot from it, but I also have a huge school project on my Windows hard drive that will be finished this week.

So.... Is there any way that I can bypass/remove the GRUB bootloader so that I can continue to work without failure on my Windows Drive?  I believe that only the Ubuntu drive is bad, but I dont know how to make it so that I can remove it and still use the Windows one.

Any Ideas?

Please Help!
Thanks

---

### Post by taurus on 2007-04-30
Insert your XP CD and boot from it to the rescue mode.  Then, remove GRUB from MBR with fix/mbr.

---

### Post by mdknaebel on 2007-04-30
Will this keep all my windows files and everything intact?

I cannot lose the files that are on my computer right now, I just want to stop having Ubuntu for a bit

---

### Post by oilchangeguy on 2007-04-30
read this,i think it is a clearer answer:
In Windows XP, you can uninstall GRUB as follows:

Boot from the Windows XP CD and press the "R" key during the setup in order to start the Recovery Console. Select your Windows XP installation from the list and enter the administrator password. At the input prompt, enter the command "FIXMBR" and confirm the query with "y". The MBR will be rewritten and GRUB will be uninstalled. Press "exit" to reboot the computer. don't use the " with your commands. and i belive you'll have to type exit at the prompt and press enter to reboot.

---

### Post by pistcivet on 2007-04-30
):P 
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by oilchangeguy on 2007-04-30
pistcivet, this is not a complete answer, Windows XP 'Recovery Console'
Just put in your Windows XP install CD, and boot into the recovery console and use the so-called 'FIXMBR' command. use the steps outlined in my previous post.

---

### Post by mdknaebel on 2007-05-01
Is it FIXMBR or fix/mbr ???
Also is there any risk to doing this?

Thanks

---

### Post by Terl on 2007-05-01
Are you using the windows cd?  You need to boot from the cd, not access it from windows.  When you boot from it, you will get a description of all the options.  One is to go into recovery.

---

### Post by mdknaebel on 2007-05-01
ok, thanks

but is it FIXMBR of fix/mbr and what do I type at first once I get to the console?

(sry, ive never done  this)

---

### Post by Terl on 2007-05-01
it is FIXMBR - works like a charm :)

---

### Post by ubnewbie2 on 2007-05-01
that's OK, try typing help, it will list all the recovery commands

but it's fixmbr

---

