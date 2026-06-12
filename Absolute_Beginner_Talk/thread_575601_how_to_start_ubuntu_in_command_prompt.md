---
title: "how to start ubuntu in command prompt"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by gnw23 on 2007-10-14
I have installed ltsp on ubuntu 6.06

i want to know if i can start in command prompt mode while starting

and will it help to save ram since i want to have atleast 6 thin clients connected to it

and also the thin clients should boot in graphics mode

thanx in advance

Shashikant

---

### Post by Bliepo32 on 2007-10-14
Well, you could do recovery mode, but I wouldn't advise you to do so. Otherwise, just do not log-in, and hit ALT + CTR + F1.

---

### Post by 001100 on 2007-10-14
when booting u see the grub screen with a countdwn get in to the grub menu and hit recovery that should boot you into a single user under the terminal.

---

### Post by steve.horsley on 2007-10-14
Find the file **/etc/rc2.d/S13gdm** and rename it to XS13gdm. This will prevent the Gnome Desktop Manager starting at boot-up. Reason: this directory has a list of scripts to be started, and the system starts everything beginning with Snn in numerical order, S00... first. Removing the X from start of the filename will re-enable starting at boot. 

Notice taht the file is actually a symbolic link to a file in /etc/init.d, but tuat doesn't affect what we are doing here.

---

### Post by gnw23 on 2007-10-14
hi 

thanx to you all for ur valuable suggestions

i am going to try them now

any idea 

as to if it  will  help to increase performance of ltsp server and increased speed in diskless clients 


Thanx and Regards

Shashikant

---

### Post by Jose Catre-Vandis on 2007-10-14
Just gives you more RAM and CPU cycles by not running the GUI, can't say I have noticed much difference, but I have only had one/two clients running at any one time. If your server is up to date (e.g. dual core) and you have lots of ram, shouldn't be a problem running GUI on the server. You could always install the xfce or fluxbox desktop.

---

### Post by oldos2er on 2007-10-14
Weird--can't find Ubuntu's inittab. Anyone know more about this?

---

### Post by RedSquirrel on 2007-10-14
> **oldos2er said:**
> Weird--can't find Ubuntu's inittab. Anyone know more about this?
Starting with edgy, Ubuntu uses upstart by default.

[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

---

### Post by oldos2er on 2007-10-14
> **RedSquirrel said:**
> Starting with edgy, Ubuntu uses upstart by default.

[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

 FAQ says "The example jobs are based on the /etc/inittab file found in Ubuntu,"

 and later "You'll need to examine this file from your distribution, compare it against the one found in Ubuntu or Debian, and modify the example jobs appropriately."

 Sure hope Gutsy has inittab. It would've made answering the OP's question easy.

---

### Post by RedSquirrel on 2007-10-14
gutsy will not have an inittab either by default.

You might want to have a look at the sysvinit package if you'd rather not use upstart.

For the OP's question, from my point of view, 
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm
```
is pretty easy. :)

---

### Post by Alabamian on 2007-12-07
Okay,

I'm with Shashikant.  I NEED to boot Ubuntu to the command prompt, given Ubuntu (and Linux's) ridiculous lack of capacity to deal with a vendor graphics driver.  Gosh, I just plugged in a scanner and printer to a Macintosh yesterday for a client and the Mac AUTOMATICALLY recognized and configured BOTH and (if it needed to download drivers?) did that, too!  I also set up my own scanner on XP last night, and though I had to download the software, I was up and running in no time.  EVERY time I have to fiddle with the graphics on a Linux box, it's like walking on eggshells over a Lion's Den.  So far, the lions have eaten this cat every time!  But enough of the complaint.  I need to know and I need to know NOW how to boot Ubuntu 7.10 directly to the command line -- no mumbo jumbo for subdir and startup methods that no longer work (or are undocumented).

Thanks ahead of time,

Alabamian

---

