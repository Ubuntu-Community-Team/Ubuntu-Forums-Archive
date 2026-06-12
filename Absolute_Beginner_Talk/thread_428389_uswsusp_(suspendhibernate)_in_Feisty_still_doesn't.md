---
title: "uswsusp (suspend/hibernate) in Feisty: still doesn't work"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-04-30
Hi,

on my laptop (MSI S260) suspend was working out of the Box in Feisty but not hibernation. After looking around a little bit I found this article that was supposed to fix everything using the package uswsusp:

[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

I used the method proposed in the 4th comment by Robin Battey which is:

[B]sudo aptitude install uswsusp
sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi[/B]

...and then suspend/hibernation was supposed to work  and it did for most poeple.......except me :( The install of uswsusp went without a hitch and I could succesfully test a hibernation using sudo s2disk. I also correctly diverted /usr/sbin/pmi to /usr/sbin/pmi-disabled but when I try to suspend/hibernate using the logoff button screen, the screen dims out and a dialog ask me to ente my password and then bring me back to the desktop and the Gnome Power Manager Applet (in taskbar) pops up a balloon with "Your computer failed to suspend. Check the help filefor common problems". I check the help but couldn't find anything related to that.

If I remove the diversion to pmi-disabled with sudo dpkg-divert –rename –remove /usr/sbin/pmi, this restore the default suspend/hibernation behaviour of Feisty (not using uswsusp) and I can suspend but not hibernate.

On the link above someone mentionned that he had this problem after installing splashy package and that suspend/hibernation could work once he removed the splashy package. I have not installed splashy or anything related but although experience the same problem: uswsusp doesn't work with pmi diverted to pmi-disabled. I don't want to run scripts for suspend/hibernation because as Robin Battey explained these scripts would be overwritten each time an update to the HAL package is done. His solution appears much better and it seems to work for most people.....but I don't know why it's not working for me.

Any help?

Thanks

---

### Post by kilou on 2007-04-30
A little update: I found that Feisty did change the UUID of my swap partition and this was probably causing some problems. I changed the UUID of my swap partition in etc/fstab to reflect the uuid corresponding to that swap partition in /dev/disk/by-uuid/. I also made sure the diversion to pmi-disabled was on and I uninstalled/reinstalled uswsusp package from the terminal. After that I rebooted the computer and upon restart I could successfully hibernate the computer and resume it. However I still have the same problem for suspend: it goes out, ask for password and goes back to desktop displaying an error message about suspend :(

Any idea why now hibernate would work with the diversion to pmi-disabled but not suspend?????

Thanks

---

### Post by kilou on 2007-05-02
Solved here [http://ubuntuforums.org/showthread.php?t=429949](http://ubuntuforums.org/showthread.php?t=429949) ......but I need to make sure that erasing everything in the suspend and hibernate scripts is OK :confused:

---

### Post by kilou on 2007-05-02
Do you think it is OK to erase everything in the sleep.sh and hibernate.sh scripts (in /etc/acpi/) and just add s2ram -f and s2disk respectively? Do I need anything from these scripts or will s2ram and s2disk care of everything??

---

### Post by H.E. Pennypacker on 2007-05-23
> A little update: I found that Feisty did change the UUID of my swap partition and this was probably causing some problems. I changed the UUID of my swap partition in etc/fstab to reflect the uuid corresponding to that swap partition in /dev/disk/by-uuid/. 

As far as I can tell, Feisty has the correct UUID for swap, but hibernation still doesn't work for me.

> **kilou said:**
> Do you think it is OK to erase everything in the sleep.sh and hibernate.sh scripts (in /etc/acpi/) and just add s2ram -f and s2disk respectively? Do I need anything from these scripts or will s2ram and s2disk care of everything??

I would not make any changes if everything is currently working.

---

### Post by Cruncher on 2007-05-23
> **kilou said:**
> A little update: I found that Feisty did change the UUID of my swap partition and this was probably causing some problems.
Just FYI: They are working on that problem.
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526)

---

### Post by Inxsible on 2007-05-25
Hey Kilou,

I see that you have used Paul Betts blog to get the hibernate and suspend work for you. 

Can you please tell me whether you downloaded the hal files ?

I followed Robin Battey's advice and only ran
```

sudo apt-get install uswsusp
sudo dpkg-divert &#8211;rename &#8211;divert /usr/sbin/pmi-disabled /usr/sbin/pmi

```

NOTHING ELSE.

Do I still need to download the hal files and cp them to usr/lib/hal/scripts/linux  ?

When i executed those 2 commands up there.. and then tried sudo s2disk, my media button lights and all LED's on the machine DO NOT turn off and my CPU fan also keeps running -- meaning it did not hibernate !!

suspend doesn't work either

---

### Post by kilou on 2007-05-26
Inxsible, there is an updated method to make suspend and hibernate work. Look at post #19 here: [http://ubuntuforums.org/showthread.php?t=194426&page=2](http://ubuntuforums.org/showthread.php?t=194426&page=2)

I also had to remove drive references to UUID in fstab and replace them with the "old way" (use dev/sdaX instead of UUID for drive X).

Hope this helps ;)

---

### Post by Inxsible on 2007-05-27
thanks kilou,

Using the link that you provided,  i changed the hibernate.sh and sleep.sh

Now, my machines do go into hibernate and sleep, but they DO NOT resume. After hibernating or sleeping, if i hit the power button again, this is what happens :

1) Hit the power button
2) shows me the grub menu
3) i select Ubuntu 
4) Shows the Ubuntu loading bar
5) Before the bar completes, i get a flickering of the screen and then a lock symbol / icon on the screen


After this, I cannot do anything. I have to perform a hard reset and then log in to Ubunut again.
This leads me to believe that even though my machine sleeps and hibernates correctly, it is not able to resume from them.

Do I need/have to make changes to the resume script too ?

Any other solutions?

Thanks

---

### Post by Inxsible on 2007-05-27
Bump

---

