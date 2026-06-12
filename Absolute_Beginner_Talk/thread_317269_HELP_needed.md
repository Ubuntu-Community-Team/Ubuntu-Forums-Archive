---
title: "HELP needed"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by Mueez on 2006-12-12
i am using intel D845GLAD, along with 256 MB ram and 1.8 Ghz processor.

I can not install ubunto on this system .....
if some one is using a similar system please tell if faced any problems????and if so how did you overcome them????

---

### Post by Sef on 2006-12-12
> i am using intel D845GLAD, along with 256 MB ram and 1.8 Ghz processor.

I can not install ubunto on this system .....
if some one is using a similar system please tell if faced any problems????and if so how did you overcome them????

What problems are you having?  Could you please be as specific as possible.

---

### Post by ajgreeny on 2006-12-12
You may need the alternate install CD, not the live install CD.  256MB ram is at the bottom of the spec for the live CD to run and install at the same time.

---

### Post by housam on 2006-12-12
Could you please list the partitions on your HDD and its format type.

---

### Post by Mueez on 2006-12-12
5 all with FAT32 I want to install it on E i.e 3 rd partation.

---

### Post by housam on 2006-12-12
Do you have a dual boot ? what is the size of each partition ?
you need to resize and format at least two partitions to install ubuntu, as ubuntu needs the format of ext3 for installation and also a swap partition.

---

### Post by Mueez on 2006-12-12
2 are of 4.75 Gb each.3 have around 9 Gb ..

i have XP installed already...and if Ubunto installs than i will have dual .....

Ok I will fuse the two with 4.x Gb.And how can I format with ext3????

---

### Post by Mueez on 2006-12-12
And what IS THIS 'alternate' CD???

---

### Post by HokeyFry on 2006-12-12
go to ubuntu.com, click on Download in the side bar, Choose Ubuntu 6.10, keep clicking on the location nearest to you, and eventually you should see a link that says "Other Installation Options". Click that and it should take you to a page with all the files. since its kinda hard to tell with architecture each one is for on this page heres a simple guide the respective torrents are one link below):

5 links down = amd64
10 links down = i386
15 down = powerpc


it is much easier to install using this CD

---

### Post by Mueez on 2006-12-12
cant we Ship these CDz?????

i have a really really solw internet connection
](*,) ](*,)

---

### Post by housam on 2006-12-12
Ok, set your pc to boot from the CD-ROM and then insert the live CD and from the top click system >> admin >> Gnome partition editor ( it is a partition tool to resize and format partitions).
if you don't have any important data on the two 4.7G , delete them to have an unallocated space of around 9.4G. then divide it to a /root partition of about 8.5G  ext3 and another one about 0.8G as a swap partition.( you choose the format from the list).
After preparing the partitions , you start the installation and choose the manual partitioning when it comes to asign the partition for ubuntu.the / partition is the important one for the root installation.

---

### Post by housam on 2006-12-12
I forgot to ask from the begining. Do you have an ubuntu live CD ? what version?

---

### Post by Mueez on 2006-12-12
thanx. will try that...

but th problem is I never reach that point...

my instalation halts when I choose language and the next screen never loads comletely.....

---

