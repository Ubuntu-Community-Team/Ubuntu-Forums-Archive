---
title: "install with alternate cd install"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by BenLi on 2007-06-04
Hey all,

I had problems with the regular installer so I am currently using the alternate cd. However, going in , I'm overwhelmed by the stuff. Can someone provide a detailed walkthrough of how to install ubuntu 7.04 with the text bas4ed installer? I wish to dual-boot ubuntu by partitioning a portion of my C drive for Ubuntu. 

Here are my specs, if it helps:

Inspiron e1505
C2D T7200
2GB ram
ati x1400 HM

Thanks in advance

---

### Post by jonward0690 on 2007-06-04
Well if you stick with the defaults you should be just fine.

---

### Post by overdrank on 2007-06-04
> **BenLi said:**
> Hey all,

I had problems with the regular installer so I am currently using the alternate cd. However, going in , I'm overwhelmed by the stuff. Can someone provide a detailed walkthrough of how to install ubuntu 7.04 with the text bas4ed installer? I wish to dual-boot ubuntu by partitioning a portion of my C drive for Ubuntu. 

Here are my specs, if it helps:

Inspiron e1505
C2D T7200
2GB ram
ati x1400 HM

Thanks in advance

Hi and well all I can add to this is when you get to the partition part of the program then select manual, then resize your current partition to have enough space to install ubuntu and then remember to build a swap partition and select the main partition of ubuntu as root!:popcorn:

---

### Post by confused57 on 2007-06-04
For me, using the alternate installer is easier than the live cd's installer, excellent screenshots here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by overdrank on 2007-06-04
> **confused57 said:**
> For me, using the alternate installer is easier than the live cd's installer, excellent screenshots here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Great idea and great piece of advice! [-o< Have to bookmark that for future use !!!!!!!!

---

### Post by daimaru on 2007-06-04
i would always recommed partioning your harddisk using partion magic first then install using the manual partion option. somehow the gnome partioner never works right..... --> it sucks in other words.
so what you should do is:
start partion magic create or rezise ( dont know how many hds u got) your partion to make space for 4 partions. what i usually do is create one logical (extended)  partition of like 200gb. course that depends on your hd size. 
create a boot partion of 100mb (50mb would be enough) --> format as ext3
create a swap partition of 2x our ram ( mine being 1gb i use 2gb) --> format as swap
create a root partion ( / ) of 10gb --> ext3
create a home partition using the rest of the space e.g. 188gb

then during install select manual partion, choose the right partions (hda1 - 7) sda sdc whatever and assign them to the right mount points --> root, home, boot, swap
... damn its kind of hard to explain if you have never done it before. so make sure you dont have any data on your hd that you dont want to loose. (never lost anything, but if you format the wrong partition your going to loose alll the data on it) . 

!!!!!!!!!! before you partition anything you should run defragmentation on your harddisk, so partitioning can actually work.

---

