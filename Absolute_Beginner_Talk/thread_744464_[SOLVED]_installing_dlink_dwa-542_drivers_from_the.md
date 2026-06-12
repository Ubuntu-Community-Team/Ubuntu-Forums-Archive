---
title: "[SOLVED] installing dlink dwa-542 drivers from the windows install disk with ndiswrap"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by chris82543 on 2008-04-03
I just installed ndiswrapper and now I want to install the dwa-542 drivers using the windows install disk that came with it but the directions were not very clear to me.
does anyone know how to do it?

---

### Post by bodhi.zazen on 2008-04-03
Mount the Windows CD, 

then use this command :

```
sudo ndiswrapper -i /media/cdrom//path/to/driver.inf
```

To see if it is installed use :

```
sudo ndiswrapper -l
```

---

### Post by chris82543 on 2008-04-03
i get command not found

---

### Post by annda on 2008-04-03
please copy&paste the exact command and its output.

p.s. how did you install ndiswrapper?

---

### Post by bodhi.zazen on 2008-04-03
> **chris82543 said:**
> i get command not found

Looks like you need to install some packages.

```
sudo apt-get install ndiswrapper ndiswrapper-utils-1.9
```

---

### Post by chris82543 on 2008-04-03
chris@chris-desktop:~$ sudo ndsiwrapper -i /media/cdrom//path/to/driver.inf
[sudo] password for chris:
sudo: ndsiwrapper: command not found

with lots of time and effort:)

---

### Post by chris82543 on 2008-04-03
tried to install and got this

chris@chris-desktop:~$ sudo apt-get install ndiswrapper ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper

---

### Post by bodhi.zazen on 2008-04-03
/me looks

/me bad

it is ndiswrapper-common

---

### Post by chris82543 on 2008-04-03
what do you mean?

---

### Post by bodhi.zazen on 2008-04-03
LOL

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

Then re-run the first commands I gave you

---

### Post by chris82543 on 2008-04-03
same thing happens
chris@chris-desktop:~$ sudo apt-get install ndiswrapper-common ndiswraper-utils-1.9
[sudo] password for chris:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswraper-utils-1.9
chris@chris-desktop:~$

---

### Post by annda on 2008-04-03
it is ndiswra**pp**er-utils-1.9, not ndiswra**p**er-utils-1.9

it's just a typo, go ahead.

btw, i recommend using the search function in Synaptics to find relevant packages, just my 2 cents...

---

### Post by chris82543 on 2008-04-03
it worked but now it says i have an invalid driver when i enter  sudo ndiswrapper -l
chris@chris-desktop:~$ sudo ndiswrapper -l
driver : invalid driver!
chris@chris-desktop:~$

---

### Post by bodhi.zazen on 2008-04-03
That is a common problem.

You can start by seeing if you can locate an alternate driver on your Windows CD. Try a XP, win 2000, or alternate driver if possible.

Otherwise, you will need to google your wireless card and see if you can locate an alterante driver.

In my limited experience, if the linux kernel does not recognize the card, and you get that error with ndiswrapper, you will likely have great difficulty getting you card to work.

Perhaps there is someone here with more experience with your card.

---

### Post by chris82543 on 2008-04-03
ok thanks I will keep working on it

---

### Post by bodhi.zazen on 2008-04-03
oh, and to remove the driver, again use ndiswrapper

```
sudo ndiswrapper -e name_of_driver
```

The name of the driver is the same as the .inf file, all lower case, and without the .INF

DRIVER.INF = driver

go ahead an remove it as it is not working.

Once you get a working driver, the next steps are :

```
sudo modprobe ndiswrapper
sudo depmod -a
```

You can then see if the card is recognized by network manager. Again, it does not always work.

---

### Post by chris82543 on 2008-04-03
problem after problem 

chris@chris-desktop:~$ sudo ndiswrapper -e driver
couldn't delete /etc/ndiswrapper/driver: No such file or directory
chris@chris-desktop:~$

---

### Post by bodhi.zazen on 2008-04-03
LOL

You need to change "driver" to the actual name of the driver you installed, the name of the .INF file you used on your windows CD (without the .INF)

---

### Post by chris82543 on 2008-04-03
it still said 

chris@chris-desktop:~$ sudo ndiswrapper -e net5416
couldn't delete /etc/ndiswrapper/net5416: No such file or directory
chris@chris-desktop:~$ 
then i went to the location /etc/ndiswrapper and it was empty

---

### Post by bodhi.zazen on 2008-04-03
looks like the attempt to install the driver was a total failure then, no need to "remove" something that is not there.

Sorry for the confusion, good luck in your search ....

---

### Post by chris82543 on 2008-04-03
how would i install a driver thats not on the disk

---

### Post by chris82543 on 2008-04-03
i got the new driver tried to install it and got this!!

chris@chris-desktop:~$ sudo ndiswrapper -i /home/chris/driver//path/to/net5416.inf
installing net5416 ...
couldn't open /home/chris/driver//path/to/net5416.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
chris@chris-desktop:~$

---

### Post by bodhi.zazen on 2008-04-03
Where is the driver ? Your desktop ? If so the path is /home/chris/Desktop/net5416.inf

So, assuming it is on the desktop,

```
sudo ndiswrapper -i /home/chris/Desktop/net5416.inf
```

Also, FYI, to save on typing you can use "tab completion". Type part of the path and hit the Tab key.

---

### Post by chris82543 on 2008-04-03
I finaly got it working IM WIRELESS!!!!

net5416 : driver installed
        device (168C:0023) present

thanks for the help:guitar:

---

