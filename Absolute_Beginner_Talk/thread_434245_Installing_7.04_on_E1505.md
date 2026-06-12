---
title: "Installing 7.04 on E1505"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by jhranicky on 2007-05-05
I am just completely lost at the moment.  I'm trying to install 7.04 on my E1505 and I am having some problems.  I have an ATI X1400 card.  I read the sticky about installing Ubuntu for the X**** cards.  But I still don't understand.  I also have a Core 2 Duo processor.  I heard I should download a different version because I have 64-bit.  Can anyone help me?

---

### Post by Oki on 2007-05-05
Hi

The difference between 32 and 64 are not much, and there are more programs for 32 – so my suggestion is to not take the 64. 

Am not sure if I understand you correctly; have you installed Ubuntu and are now wondering how to install the driver for the GPU?

---

### Post by starcraft.man on 2007-05-05
> **jhranicky said:**
> I am just completely lost at the moment.  I'm trying to install 7.04 on my E1505 and I am having some problems.  I have an ATI X1400 card.  I read the sticky about installing Ubuntu for the X**** cards.  But I still don't understand.  I also have a Core 2 Duo processor.  I heard I should download a different version because I have 64-bit.  Can anyone help me?

The simple answer to your second question is that you really don't need the 64 bit version of Ubuntu. It has limited benefits for the average day user, and it does have some problems with software support (often some programs are only coded for 32 bit, its the one with the largest base if the coders must make a choice). So I would tell you to get the 32 bit version of the Feisty Fawn live installer from [here.]("http://www.ubuntu.com/getubuntu/download") Just pick Feisty Fawn, standard personal computer and then the location nearest to you and make sure to check the alternate installer (since I read the sticky, seems you can't use live CD at all. Then download away, burn and boot into it.

So I will just try to make this brief and walk you through this. 

1) Once you downloaded the iso for alternate installer of Feisty, your gonna burn it (with any program you have, use 4 or 8X to prevent any errors on the CD. Then pop it into the drive and make sure your computer boots into it (ensure your BIOS is set to boot from CD first).

2) When the menu pops up select the first option, it will say "Text install".

3) Go through and read each screen clearly, they are more or less straightforward (make sure your ethernet internet is plugged in so that feisty autoconfigures your internet). 

4) Eventually you will get to a partitioner, here is the slightly advanced part now pay attention carefully. You will have to make 3 partitions. Firstly, if you have windows already installed and want it gone, you will select it (with arrow keys and enter of course) and enter it, then select the option to delete it. Then, you will want to select the free space left and push enter, set it to 8 GB and is primary type. Then make sure it has the following options:

Ext3
Format partition (if this line is blank, thats ok)
mounted to: /

When all that is set, push done with this partition. Now we will set two more up the same way, I'll just list the settings since its the same way to make the new ones.

Make a 2 GB partition, make it logical. Select the format and choose swap file. Push done.

Now, make a new partition with the remainder of your drive. It should be logical type (size is whatever is left). The format should be ext3, and it should Mounted to: **/home**.

Thats it, then write the changes to disk and the rest should be installed on its own.

**** NOTE: If you want to dual boot, leave your windows parition, select it and resize it so you have at least 10 GB for the install of / and swap, then X amount for your home folder (depending how much you want to install.

5) Log in and open up the terminal (Applications > Accessories > Terminal), then type in this, run each line seperate:

```
sudo aptitude update
sudo aptitude upgrade
```

6) When upgrades are done, reboot. Log back in, open the terminal again and put in this command:

```
sudo apt-get install xorg-driver-fglrx
```

7) When the install finished, run this command in the same terminal:

```
sudo depmod -a
```

8 ) FInally run these two lines of code in the terminal as well:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

9) Reboot and your done. 

I hope this helps, please reply if you have any problems. and yes, this did take a while to type out clearly :D

---

