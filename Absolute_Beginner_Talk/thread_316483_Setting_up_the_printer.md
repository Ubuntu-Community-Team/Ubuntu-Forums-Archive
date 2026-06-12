---
title: "Setting up the printer"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Tzumli_D on 2006-12-10
Would someone please give me a complete set of instructions (code) for installing my brother 5150D printer. I've read the tutorials, and have tried to set up the printer, but because of my newness, still do not understand all the words, and more significantly do not really know how the file system works. 
I have sort of figured out what I need to do to install the printer and cups, and this is what I have done so far:
First I looked for the cups files and found them in /etc, but the folder was empty.
I used synaptic to fetch the cups files.
Then I checked the files again and there now was a .ppd file folder which is empty.
After a bit of a struggle I managed to copy the .ppd file off the Brother driver disc (CD ROM) and it's on my desktop.
I tried to click and drag it into the empty .ppd folder under cups but was told I did not have permission to modify the folder.  ](*,) 

So could you tell me please what I have to do to install the .ppd file in the correct place?

And then I presume I need to restart the cups daemon as follows:

"Restart the CUPS daemon.
Log in as root and enter one of the following commands:
killall -HUP cupsd
/etc/init.d/cups restart"     I presume here that login as root, I should do using sudo? And do I have to do the killall?

Is init.d/cups equivalent to making cupsd.conf run?

Thanks
Denise :-?

---

### Post by ciscosurfer on 2006-12-10
Try going to System > Administration > Printing and then Add Printer and follow the instruction there.

This page will help as well: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/printing.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/printing.html)
If you want to manage your printer from a Web interface, then check here: [https://help.ubuntu.com/community/PrintingCupsWebInterface](https://help.ubuntu.com/community/PrintingCupsWebInterface)
If found this page on the Forums, and think you may find it useful: [http://ubuntuforums.org/showthread.php?t=71104](http://ubuntuforums.org/showthread.php?t=71104)

Post back if you have trouble. :-)

---

### Post by ciscosurfer on 2006-12-10
Added more links above :-)

---

### Post by Tzumli_D on 2006-12-10
Sorry, I forgot to mention that that was what I did first. I just have two dialogue boses and the little timer thing saying rading printer database. How long am I supposed to let that run. 50 minutes?
I thought my request for help was quite specific.

---

### Post by Tzumli_D on 2006-12-10
I've looked at all those things. I've done about as much as I can.

---

### Post by ciscosurfer on 2006-12-10
> **Tzumli_D said:**
> Sorry, I forgot to mention that that was what I did first. I just have two dialogue boses and the little timer thing saying rading printer database. How long am I supposed to let that run. 50 minutes?
I thought my request for help was quite specific.Your request for help was specific, as was my answer. ;)

I'm sorry I couldn't be of more help to you.

---

