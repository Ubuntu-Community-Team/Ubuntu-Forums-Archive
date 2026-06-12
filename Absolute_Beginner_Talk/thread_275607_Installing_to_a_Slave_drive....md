---
title: "Installing to a Slave drive..."
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by james.gornall on 2006-10-11
Hi,

Im very new to Linux distrobutions and I've only ever used live CDs.

The course I'm takin has made me decide that it would be worth having a permanent installation of a Linux distro.

Just wondering is it possible to Dual Boot if windows is installed on my "master" and Ubuntu on the slave.

Thanks alot.

---

### Post by taurus on 2006-10-11
Yes, you can install Ubuntu on the slave drive.  Don't forget to install GRUB on MBR so you can use it to boot either Ubuntu or Windows.

Good luck.

---

### Post by james.gornall on 2006-10-11
wow. 

Thanks for quick reply.

You got a link for them programs and how to use?

Linux a little daunting at moment so any help appreciated.

Thanks again.

---

### Post by taurus on 2006-10-11
If you already have the desktop CD (LiveCD), then just click on the install icon on the desktop and off you go.  I will walk you thru the whole process.  And when you get to the screen regarding bootloader, make sure you tell it to install GRUB on MBR and it should pick up your Windows.  Otherwise, you can add it in later with no problem at all.  But just in case, here is one of the sites you can download Ubuntu for your machine...

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by james.gornall on 2006-10-11
Ok mate thats brilliant.

thanks alot for ya help.

Give it a go when I get home then :P

---

### Post by taurus on 2006-10-11
Good luck and if you are running into problems, just post them here.  Somebody sure will get back to you as soon as he/she is able to.

---

### Post by james.gornall on 2006-10-11
yer you seem to be a friendly bunch.

was kinda expecting "why you want windows" kinda responses.

Thanks alot mate, made good first impression on community!  I shall be returning for sure :P

---

### Post by taurus on 2006-10-11
And don't forget, we don't get paid for helping others...  :mrgreen:

---

### Post by james.gornall on 2006-10-11
hopefully 6months down the line I'll be the one helping a linux noobie :P

---

### Post by taurus on 2006-10-11
I am sure other newbies will appreciate all the helps you can give them.

---

### Post by james.gornall on 2006-10-11
lol I'll help where ever I can.

Thanks alot mate, prob need to call on you again some time.  

Learning all these new Terminal commands might take a week or so to get used to.

---

### Post by gn2 on 2006-10-11
> **taurus said:**
> Yes, you can install Ubuntu on the slave drive.  Don't forget to install GRUB on MBR so you can use it to boot either Ubuntu or Windows.

Good luck.

If you are dual-booting with two hard drives absolutely do not put Grub over the MBR if you've got any sense.

Disconnect the Windows drive and put Grub on the Ubuntu drive.

Windows on master, Ubuntu & Grub on slave.

Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.

Choose OS by selecting which drive to boot from.

Select desired default OS by re-arranging boot order in BIOS.

Only need to press F8 to select non-default OS.

Always disconnect other OS's drive if re-installing.

If you take this option you will never have any issues with Grub menu lists or MBR corruption.

Grub on my MBR was worse than any virus I ever had.

To suggest having Grub on the MBR of the Windows drive is absurd, because it's hazardous and just isn't necessary.

---

### Post by STREETURCHINE on 2006-10-11
hi i have installed ubuntu on the master and windows on the slave i currantly use  f11 to choose which hard drive to load from or i can just let it boot straight to ubuntu,can i do any thing so as i dont have to keep hitting the f11 button till it loads the choice of hard drives?:)

---

### Post by james.gornall on 2006-10-11
> **gn2 said:**
> If you are dual-booting with two hard drives absolutely do not put Grub over the MBR if you've got any sense.

Disconnect the Windows drive and put Grub on the Ubuntu drive.

Windows on master, Ubuntu & Grub on slave.

Press F8 (or whatever key depending on BIOS version) at boot time to bring up the Boot Device Selection Menu.

Choose OS by selecting which drive to boot from.

Select desired default OS by re-arranging boot order in BIOS.

Only need to press F8 to select non-default OS.

Always disconnect other OS's drive if re-installing.

If you take this option you will never have any issues with Grub menu lists or MBR corruption.

Grub on my MBR was worse than any virus I ever had.

To suggest having Grub on the MBR of the Windows drive is absurd, because it's hazardous and just isn't necessary.



Ok, so I just:

1. Unplug Master
2. Install Ubuntu to slave
3. Reconnect master
4. Use function key for my BIOS to select the drive I wanna boot from.

There is no need for the Grub thing then?

Thanks for your input.

---

### Post by gn2 on 2006-10-11
> **james.gornall said:**
> Ok, so I just:

1. Unplug Master
2. Install Ubuntu to slave
3. Reconnect master
4. Use function key for my BIOS to select the drive I wanna boot from.

There is no need for the Grub thing then?



Absolutely no need at all, now or in the future, when for example you re-install Windows, or have a Linux Kernel Update.

Just unplug the other drive when re-installing.

---

