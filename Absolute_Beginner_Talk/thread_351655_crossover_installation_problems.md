---
title: "crossover installation problems"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-02-02
Hi all,
I'm having some trouble installing the crossover standard demo. I checked the forums and found this: [http://ubuntuforums.org/showthread.php?t=350515](http://ubuntuforums.org/showthread.php?t=350515). It seemed like I had it licked, but I keep getting "Permission Denied" replies, even when I'm logged in as root. Any suggestions?

---

### Post by Jussi01 on 2007-02-02
Where exactly are you getting permission denied? can you give us the output of your terminal? I had some problems with my crossover install - check out my post in[ this thread]("http://ubuntuforums.org/showthread.php?t=326198&page=2") for more help.

---

### Post by lyceum on 2007-02-02
If you saved to your desktop, copy and paste this into terminal:

> 
cd ~/Desktop
ls -l


then:

> 
sh install-crossover-standard-demo-6.0.1.sh


---

### Post by handyguy33 on 2007-02-02
Re: crossover installation problems
If you saved to your desktop, copy and paste this into terminal:

Quote:
cd ~/Desktop
ls -l
then:

Quote:
sh install-crossover-standard-6.0.0.sh
__________________
We know what we are, but know not what we may be. -Ophelia
Reply With Quote

OK I tried that and got:
sh: Can't open install-crossover-standard-6.0.0.sh

I know I'm close, but what am I missing?

___________________
If we're not supposed to eat animals, why are they made from meat?

---

### Post by lyceum on 2007-02-02
First, it is saved to desktop, correct?

Second, are you putting those codes in one at a time? (all of the first, all of the second)

Third, you may want to trash the copy you are trying to install and start over with a freshly downloaded copy(?) Something may have gone wrong with the download.

Fourth, you are cutting and paisting, not typing correct?

---

### Post by handyguy33 on 2007-02-02
First, it is saved to desktop, correct?

Second, are you putting those codes in one at a time? (all of the first, all of the second)

Third, you may want to trash the copy you are trying to install and start over with a freshly downloaded copy(?) Something may have gone wrong with the download.
__________________
We know what we are, but know not what we may be. -Ophelia 

First: yes

Second: yes

Third: This is like the third download of this package, but I haven't gotten an error during the download process. Although, I did try to open it with GDebi, and it said that the file could be corrupted. I don't know if GDebi is the right thing to open it with anyway. 

A side note, I'm trying to get this to work so I can install Microsft Office. I have wine. it's configured to winxp, and has ie6, but it drops the installation of Office for some unknown error

I'm just digging myself deeper, aren't I?

---

### Post by rwhillman on 2007-02-02
I am having exactly the same problem with Crossover install.

---

### Post by handyguy33 on 2007-02-02
I finally got crossover to install. that thread in my original post worked after a reboot. However, the MS Office didn't take. I guess I'll post a question about that soon enough.

Thanks

---

### Post by lyceum on 2007-02-02
> **handyguy33 said:**
> I finally got crossover to install. that thread in my original post worked after a reboot. However, the MS Office didn't take. I guess I'll post a question about that soon enough.

Thanks

Just a quick thought... Are you trying to install access too? It said that it would not install access. 


Glad you got it working though. :)  Mine works great, I have been using it for about 3 weeks now. I will be shelling out the cash as soon as I get my tax refund back.

---

