---
title: "Install KDE using Kubuntu CD.."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-08-20
Hello everyone,
After having used Ubuntu for over a month, i decided to give Kubuntu a try. I really liked the KDE GUI, and i want to use it in my Ubuntu..my question is: Is it possible to install KDE from the Kubuntu CD? And if yes: How? 
I would be very glad if some-one posts a solution to my problem...
Thanks in advance..

---

### Post by foolsh on 2006-08-20
```
sudo apt-cdrom add
```
it will ask for the cd
after its finished adding it
```
sudo apt-get install kubuntu-desktop
```
enjoy!

---

### Post by kitt on 2006-08-20
OK thanks...but theres a problem: heres what i get :
 sudo apt-cdrom add

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d251c204c5513e9470c11bf645950d27-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wednesday 31 May 2006 09:03:59 AM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.

After this, when i install kubuntu-desktop....it downloads the packages from the internet! Whats wrong here...?

---

### Post by foolsh on 2006-08-20
you may have to 
sudo gedit /etc/apt/sources.list
and comment out "put a # infront of" any thing that is not a cdrom
i.e.  #deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
then sudo apt-get update
sudo apt-get install kubuntu-desktop

---

### Post by kitt on 2006-08-20
I did as u told, foolsh....commented out the non-cd rom lines..and i get this message:
sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop

Now what??
Once again, thanks for ur help/....

---

### Post by true_friend on 2006-08-20
oops same problem is here. 
so what we do know.

---

### Post by kitt on 2006-08-20
I did sudo apt-get install <tab> and it returned the folders on the disk..
it means ( i presume ) that "kubuntu-desktop" may not be the right package needed for install..so the question is:
What do i(we) need to install in order to get KDE..what package..?

---

### Post by foolsh on 2006-08-20
then let me apologize most sincerely and hang my head in shame :confused: 
[IMG]http://www.firstfoot.com/Tartan%20Army/images/ally.JPG[/IMG]

---

### Post by kitt on 2006-08-20
@foolsh
U have been of great help..maybe something is wrong with something else ;-)
Anyone here knows which packages to install??

---

### Post by kitt on 2006-08-20
C'mon all you KDE fanboys...help me out!!!

---

### Post by aysiu on 2006-08-20
You can't install it from the **Desktop CD**. You need the **Alternate CD**.

---

