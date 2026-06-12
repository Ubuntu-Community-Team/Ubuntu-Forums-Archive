---
title: "Will ext3 recognise external files on NTFS?"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by tjpearson on 2007-11-12
Hello,

Well, I’ve got my disk burnt with ‘ubuntu’ ready for install and rid myself of microshaft once and for all and just about to install my new hard drive to replace the faulty one in the laptop, but………

I believe I should format the new hard drive with ext3 before installation, does the boot up process allow you to do this.  I have an external Maxtor hard drive with loads of personal files on it and that is formatted for XP, I think NTFS.

If I format the new laptop hard drive with other than this will the computer, once up and running with ‘ubuntu’ still recognise files such as my music and pictures on the external Maxtor.

Tried finding this in previous threads but with no joy so I hope this isn’t a stupid question!

Thanks

---

### Post by MikeSz on 2007-11-12
Ive got several machines running different OS's.  When you install Ubuntu, it will format the partition for you if you want it to.  you can play with the partition size, or use an entire hard disk if you like so no need to start formatting partitions before you install - just go through the setup process and all will become clear.  

If you have an external hard disk with windows files on it which you want to keep (as I did) you can connect this up after you have installed ubuntu and it should recognise it and allow you to view files.  You may however find that you cannot write to them or remove them (I had a little problem with this but I believe from looking in here there is a way round it - someone may be able to tell you how you do it)

Does that make a bit more sense?

---

### Post by Hallvor on 2007-11-12
> **tjpearson said:**
> Hello,

Well, I’ve got my disk burnt with ‘ubuntu’ ready for install and rid myself of microshaft once and for all and just about to install my new hard drive to replace the faulty one in the laptop, but………

I believe I should format the new hard drive with ext3 before installation, does the boot up process allow you to do this.  I have an external Maxtor hard drive with loads of personal files on it and that is formatted for XP, I think NTFS.

If I format the new laptop hard drive with other than this will the computer, once up and running with ‘ubuntu’ still recognise files such as my music and pictures on the external Maxtor.

Tried finding this in previous threads but with no joy so I hope this isn’t a stupid question!

Thanks

You just boot from the cd, and you will be able to format the drive from a gui. It is a part of the installation process.

Ubuntu has NTFS read capabilities out of the box, but to write NTFS you need to install something called ntfs-3g and ntfs-config(?) from the synaptic pachage manager. From there, it is just point and click to make it work. (I have an external Western Digital myself with NTFS.)

---

### Post by tjpearson on 2007-11-12
Thanks a lot MikesZ and Hallvor, can't believe how fast my concerns are put to rest on this site.  

Looking forward to installing this now.

---

### Post by tjpearson on 2007-11-12
Sorry I mean MikeSz

---

### Post by bulldog on 2007-11-12
If you plan on installing Gutsy,I have some good news.
It can read and write to an NTFS partition with no problem,it's already build in,you only have to acivate it [checkbox]

Installing and partitioning:
If you plan to use ubuntu only,some advice.
To avoid upgrades and the chance of breaking things consider the following partition plan.

Create 2 partitions 10GB each.
Create one swap 1-2GB max
Create one /home as big as you like

Now you can install ubuntu on one of 10GB partitions [/] and mount the /home partition as /home

Now you can install another ubuntu or what ever,or if there's a new release you can install it without loosing your excisting install.[clean install]
Use the same /home and swap,only,and this is important,use another user name,so there will be a new user created in your /home,and no mixing up between the distro's will happen.
You can,as root,copy files you want between the two users.

---

### Post by tjpearson on 2007-11-12
mmmmmmmmmmm, sorry bulldog but you've completely lost me.  It's a bit like me explaing the suspension setup of a Yamaha R6 to you, if you see what I mean.  

Slowly, slowly if you can, e.g. 
step 1 ***** 
step 2 *****

---

### Post by MikeSz on 2007-11-12
if you install the latest version of Ubuntu, 7.10 - it will let you write to your windows hard disk as well as view it.  /you can however still use the CD as a "live" cd and run the OS straight from the CD to have a play round.  You should, using that, be able to see your windows hard disk and use it.

---

### Post by MikeSz on 2007-11-12
he says confidently....

---

### Post by bulldog on 2007-11-12
> **tjpearson said:**
> mmmmmmmmmmm, sorry bulldog but you've completely lost me.  It's a bit like me explaing the suspension setup of a Yamaha R6 to you, if you see what I mean.  

Slowly, slowly if you can, e.g. 
step 1 ***** 
step 2 *****

Well I ride a motorbike myself [vtr100f] so I should know something about it :)

It's all about making the right choices before you begin.
I know by now,that when a new ubuntu comes along,everybody want to upgrade,which can be more or less a pain in the ***.
Therefore we create 2 10GB partitions so you can do a clean install without loosing the existing ubuntu.
By making a separate /home,all your data and preferences are stored there,you can do a reinstall without loosing anything.

A plain install by letting ubuntu do the partitioning for you,will only create a / partition and a swap.
This will do,however,when you want to reinstall,you have to backup all your data from /home,otherwise it will be lost.

You can do all of this with the live cd or the gparted live cd,which is a small download,must be burned to a cd and the booted from.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by tjpearson on 2007-11-12
OK bulldog, I see what you mean now.  Stay safe on that bike and watch the others that arn't watching you.  What about advice on free footy on sat, I'm good at that!

So its all about partitions and keeping stuff safe, so I suppose on bootup I can choose which partition to use as well, thanks a lot.  I'm really taking the plunge, decided that ubuntu is going to be be my one and only operating system.

---

### Post by dnns123 on 2007-11-12
I not sure if I understand your thread. From what I assume, you want to copy something to/from your external HDD?

just go to add/remove and install NTFS config.
After isntalling it, go to applications --> system tools --> NTFS config

click on the box with external blah blah blah.

You should be able to write to/detect NTFS now. (not sure about detect though)

---

### Post by bulldog on 2007-11-12
> **tjpearson said:**
> OK bulldog, I see what you mean now.  Stay safe on that bike and watch the others that arn't watching you.  What about advice on free footy on sat, I'm good at that!

So its all about partitions and keeping stuff safe, so I suppose on bootup I can choose which partition to use as well, thanks a lot.  I'm really taking the plunge, decided that ubuntu is going to be be my one and only operating system.

A good partition plan is the best thing to start with.
I have 6 10GB partitions,but I like to experiment with other distro's,and they all use the sam /home and the same swap.
Works pretty well.

Good luck,and if you have questions,use the forum or just give me a PM.

Have a nice day :)

---

