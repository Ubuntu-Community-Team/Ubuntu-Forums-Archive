---
title: "Ubuntu Studio And VirtualBox"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by oceansize on 2007-08-31
Installed VirtualBox onto my Vista Home Premium PC today (2gb RAM 1TB HDD space, ATI X1300 Graphics card, dual core AMD processor) with the intention of loading Ubuntu Studio onto a 'virtual' drive. I found a great walk through here
[http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/#comment-52456](http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/#comment-52456)
Which I followed through just fine.

All goes well until the point where I've selected to install from the main menu - the screen just goes black with a cursor marker in the top right, 

I've left for ages (over an hour) to see if it was doing something 'in the background' but it wasn't.  Anyone any ideas what I'm doing wrong or how I can got past this stage?

---

### Post by ts51 on 2007-08-31
Set up virtual box correctly, but set the CD rom to be the ubuntustudio iso. from there it is just like using another computer once you start the virtual machine.

---

### Post by oceansize on 2007-09-01
OK, tried that and still the same thing, after the opening splash screen where you can select to install..etc.., I choose to install- screen goes black with a curssor top left

---

### Post by Orbital75 on 2007-09-01
Here is how to fix this.... 
Open Virtual Box and go into Settings.
Under the General Tab Choose Advanced.
Now, Put a Check in the **Enable IO APIC** box.

This will fix it, I had the same issue with Virtual Box.
Hope this helps...  :KS

---

### Post by lammergeir on 2007-09-02
I've tried twice to install VirtualBox into Ubntu Studio 7.04, and each time the installer hangs -last time, ran for nearly three hours, on ADSL. I closed apps and now get following fault:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Grateful for help for this newbie.

---

### Post by oceansize on 2007-09-02
> **Orbital75 said:**
> Here is how to fix this.... 
Open Virtual Box and go into Settings.
Under the General Tab Choose Advanced.
Now, Put a Check in the **Enable IO APIC** box.

This will fix it, I had the same issue with Virtual Box.
Hope this helps...  :KS


Thanks mate..installed like a dream after doing that!!

---

### Post by n3tfury on 2007-09-02
your nick a reference to janes addiction? :)

---

### Post by Seisen on 2007-09-02
> **lammergeir said:**
> I've tried twice to install VirtualBox into Ubntu Studio 7.04, and each time the installer hangs -last time, ran for nearly three hours, on ADSL. I closed apps and now get following fault:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
Grateful for help for this newbie.

You need to run ```
sudo dpkg --configure -a
``` in the terminal. Did you download the VirtualBox .deb file if so you can add the VirtualBox repository by following the directions here. I ended up having to do that because I was having problems with the .deb file.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by lammergeir on 2007-09-02
Thanks. Ran the code and it helped, now get Update manager error: 'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'
I moved to Ubuntu to make life easier....  (It's also more fun!)

---

### Post by Seisen on 2007-09-02
Try reinstalling it again for some reason that problem pops up once in a while.

---

### Post by lammergeir on 2007-09-12
Thanks for all the kind assistance.  I found Lonnie Lee Best's instructions helpful. [http://www.howtoadvice.com/UbuntuVirtualBox/](http://www.howtoadvice.com/UbuntuVirtualBox/) , and tried to follow Arun's Blog about installing Virtualbox in Ubuntu Feisty.  I'm using 1.5 and on start up in get: FATAL: NO BOOTABLE MEDIUM FOUND! SYSTEM HALTED.
Grateful for pointers.  Under advanced boot order. cd/dvd then hard drive and I've checked all three extended features.  Won't boot up with either win98 or 2000.

---

### Post by dgaf on 2007-09-16
i use this and it works great   Wubi-7.04.04:)  gives you choice of os i put in ubuntu  studio
but it give you a choice of all ubuntu systems so close to a real install.  gives you a dual boot up
add this and you dont  lose anything like a live cd i tried all  ubuntu os each one took 35-40 min 
and and u can add and remove this software from windows side...i think this really help out a lot 
i put linux on a old dell cpx..but it not the same as putting it on my my pc  ..i can almost due 90% of all
linux stuff i love the system package you just pick what you want click to install...wubi 7.04.04 should be on this site next to  live cd it only a 10mb  then it downloads the os u want  ..there is not anyway to screw this up if screw something up just restart and pick
windows to boot and unstall and the restall the program....ps it will let you pick out how much disk space
you want..

---

