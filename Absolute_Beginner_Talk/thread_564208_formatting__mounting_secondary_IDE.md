---
title: "formatting / mounting secondary IDE"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Wolfie Lee on 2007-09-30
Hi, all.

I have searched way too many threads unsuccesfully for a solution to my problem, but will have to post new on this...

I am running a Feisty (alternative, non - graphical install) with KDE (not sure [sky blue spash with white "swirly" and boot - up]). This is a Maxtor 41 GB HD.
I have installed a Maxtor 20GB HD with a mountable Feisty LIVECD install.....I can read/write/delete files in home folder, but I  just want to format said 20GB HD to ext 3, and use it as my main music repository and be able to build a data base for it through an app (such as RythmBox, Amorak, whatever...) running in the alternative OS / primary IDE drive (41 GB Maxtor), and have OS automatically mount the drive without haveing to boot-up, click on places, click to mount 20 GB HD, and enter my password every time. I hope this is specific / clear enough...if not, let me know....

Please help...:confused:

---

### Post by Pumalite on 2007-09-30
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(the stand alone, burn to CD, boot from, program)

---

### Post by Wolfie Lee on 2007-09-30
Thank you for info...Have downloaded / installed in Synaptic...and found gparted.exe file in /usr/bin... but need Rooot privileges, I thought I was root on MY OWN SYSTEM?!?! If not, please tell how to open just this file with root privilages, in terminal is fine...

---

### Post by Pumalite on 2007-09-30
You have to download the iso from the site I gave you. Then burn the iso to CD as 'Image', then boot from it.

---

### Post by Wolfie Lee on 2007-09-30
ok, just trying to take the lazy way out, I guess...but will I have to boot from that every time? I am looking for permanent results I won't need to boot from anything but Primary IDE...

---

### Post by Wolfie Lee on 2007-10-01
O.K. --

Guess I wasn't clear enough...SORRY --

Burnewd ISO, booted, but ran into same / similar prob;em with gparted as I did with Ubuntu... For WHATEVER reason, This box will NOT accept any LIVE, GRAPHICAL install. I am Running Dell Optiplex GX400, PIV 1.4 GHz, Nvidia Riva TNT2/TNT2 Pro 32 MB, and had to use Alternative (i386) Text-line install...Does Gparted HAVE a Text-line install version, or am I S.O.L? Is ther any other way to do what I want to do? I Have moved to gparted forum on this, but want to keep thread going for any possible alternative to gparted, or a way to get it installed / running properly.......

---

### Post by Pumalite on 2007-10-01
Try rescuecd and use it's partitioner: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Wolfie Lee on 2007-10-02
I'm sorry---I really don't understand what another program is going to do for me---ALL I want to do is FORMAT an EXISTING  Hard Drive, and have it mounted AT START UP....Nothing NEEDS to be rescued , here....

---

### Post by Wolfie Lee on 2007-12-01
Seem to have reached a viable solution, however I still have to have a seperate OS installed on secondary HDD to use it for music storage. It seems I should be able to FORMAT it BLANK, without an  OS in place, and mount it with the OS on my primary Drive.....any one have any ideas?

---

