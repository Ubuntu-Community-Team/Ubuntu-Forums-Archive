---
title: "!!!!!!!!!!!help!!!!!!!!!!!"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by jgrabham on 2006-07-12
I Get To A Strange B+w Page That Asks Me My Username+password.  Ive Only Just Got Ubuntu So Im Stuck.  I Put In The Details I Enterd During Instillation But Nothing Comes Up.

---

### Post by T700 on 2006-07-12
Did you do a server install?  If so, there is no GUI loaded.  Log in with your user name and password and then type:

```
sudo aptitude update
``` 
Enter

```
sudo aptitude install ubuntu-desktop
``` Enter

 
Also, please post your requests with a more descriptive subject.  It will help you get more eyeballs on your questions.

Paul

---

### Post by Brunellus on 2006-07-12
The number of exclamation points you put in your header has no bearing on the ability of the community to solve your problem.

Questions that DO have bearing:

Did you accidentally attempt "server" or "expert" install options?

What did you try to log in with?  You log in with your user name and password.  Characters for the password are not echoed--nothign will appear on screen, but trust us, they're three.  That prevents people from reading over your shoulder and finding out how many characters are in your password.

---

### Post by jgrabham on 2006-07-12
> **T700 said:**
> Did you do a server install?  If so, there is no GUI loaded.  Log in with your user name and password and then type:

```
sudo aptitude update
``` 
Enter

```
sudo aptitude install ubuntu-desktop
``` Enter

 
Also, please post your requests with a more descriptive subject.  It will help you get more eyeballs on your questions.

Paul

i tried that it said something like there are no files like that to install and then it said 0 files installed 0 files upgraded

---

### Post by T700 on 2006-07-12
What type of install did you do:  Expert, Server, Desktop?  You might just go ahead and reinstall and be sure to do the normal, desktop.

Paul

---

### Post by jgrabham on 2006-07-12
> **T700 said:**
> What type of install did you do:  Expert, Server, Desktop?  You might just go ahead and reinstall and be sure to do the normal, desktop.

Paul

I downloaded this from the web  I booted the instalation from a cd  there were no suitable options apart from "install to hard disk"  - the intel x86

Server install CDThe server install CD allows you to install Ubuntu permanently on a computer.

There are four images available, each for a different type of computer:

PC (Intel x86) server install CD 
For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure. 
Mac (PowerPC) server install CD 
For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks. 
64-bit PC (AMD64) server install CD 
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips. 
SPARC server install CD 
For Sun UltraSPARC computers, including those based on the multicore UltraSPARC T1 ("Niagara") processors. This is an unofficial release, but testing and feedback are encouraged.

---

### Post by T700 on 2006-07-12
You downloaded the wrong version.  Go back to the download page and look for the desktop install.  Just grap that and download it and all will be well.

Paul

---

### Post by steve.horsley on 2006-07-12
T700 is right - your best bet is probably to go and get the desktop install CD. The file name is ubuntu-6.06-desktop-i386.iso

Of course, this time you will have to use the custom partitioning to tell it to re-use the partitions that your last install made. Easier mught be to delete those partitions using windows and then you can just tell the installer to use the free disk space.

Good luck.

---

### Post by jgrabham on 2006-07-12
> **steve.horsley said:**
> T700 is right - your best bet is probably to go and get the desktop install CD. The file name is ubuntu-6.06-desktop-i386.iso

Of course, this time you will have to use the custom partitioning to tell it to re-use the partitions that your last install made. Easier mught be to delete those partitions using windows and then you can just tell the installer to use the free disk space.

Good luck.

i dont have any OS on that PC

---

### Post by T700 on 2006-07-12
> **jgrabham said:**
> i dont have any OS on that PC

Just get the Desktop CD and run the normal, typical, install, accept the defaults, and you'll be swinging to Ubuntu in no time.

Paul

---

### Post by givré on 2006-07-12
In fact the description is quite confusing. I fill a bug, if you would like to add your comment : [https://launchpad.net/products/ubuntu-cdimage/+bug/52799](https://launchpad.net/products/ubuntu-cdimage/+bug/52799)

---

