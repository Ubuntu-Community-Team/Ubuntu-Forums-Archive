---
title: "Network Printer Driver"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by BiggoCharley on 2006-02-25
I have a Brother MFC5840CN which is not shown as being supported by the kernel when I go to install it (add a new printer). However i found a debian driver package on Brother's website. I downloaded and ran the dpkg inst-I program.  The install seemed to go ok but Ubuntu can't see my printer.  The printer is plugged directly into my router and my windows machines can use it with no problems.  Where (in what directory) will the driver have been put in the install process.  I've searched but can't seem to find it. During the install a directory was created /var/spool/lpd/mfc5840cn.  I looked at this directory but it is empty.  I've run out of ideas --any suggestions will be welcome.

---

### Post by nikopol on 2006-02-25
try a find on the hard disk or look in synaptic to see what has been installed by that package.

sudo find / -name "*.ppd" | more

will turn up all the printer drivers on your system. Mine happens to be in /etc/cups/ppd/ . Maybe worth a look...

---

### Post by Mack1 on 2006-02-26
Hi Biggo,

Have a look @ this thread: [http://www.ubuntuforums.org/showthread.php?t=105703&highlight=mfc](http://www.ubuntuforums.org/showthread.php?t=105703&highlight=mfc)

Bobsongs has made an excellent HOW-TO for this problem.
My Brother MFC425C works like a charm now due to his HOW-TO!
(identifying it as MFC 210C, the printer is connected to my network-router)

The Brother site isn't quite good for a newbie like me so i found Bobsong's thingy
in these nice forums.

Too bad the scanner cannot be made to work over the network at this time :(

I'm fairly new to linux and am running Ubuntu on two pc's now, the 1st one i tested loads of things on that i found and printed out manuals-of-sorts for later reference. The 2nd is 'stress-tested' on by my girlfriend for her study. So far so good!

Ubuntu looks very promissing and if i get mythtv finally running i will definately be switching over to Ubuntu!

---

### Post by niknak on 2006-03-25
Mack1, could you help? I have a MFC5840, connected via my router and I followed bobsongs thread. I had a problem with the c shell instructions, whereby it told me (unbuntu 5.1) the csh file couldn't be found, without this I guess nothing else would work. 2 years from now, I might know a little more but I've just installed this system and just like to install the printer.. Any clues? I have downloaded various files with rpm and deb type files, neither of which the fileroller will recognise

---

### Post by Mack1 on 2006-04-16
Hi Niknak,

Sorry i haven't responded sooner, i haven't been online much lately due to personal reasons.

Also i'm sorry that i have to say this: im fairly new to linux so im stumbling to get things done that i do in windows in a jiffy.....

The only thing i can say is read this forum well, use the search button lots and you'll get there!!

Most of the things (except scanning through the network) that i did with my windows machine i can do with (k)ubuntu now too, all thanks to the help of people that are/were willing to help me.

I hope you get the answers that you need soon!!

---

