---
title: "Webmin installation in Ubuntu server"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by sikandarnoori on 2007-01-28
hi all,
i need your help about the how to install the **webmin** in Ubuntu server via command prompt. tnx by advanced

Noori

---

### Post by taurus on 2007-01-28
I don't think webmin is in the repos.  However, you can download a .deb from here.

```

wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.320_all.deb

```
Then, you can install it with

```
sudo dpkg -i webmin_1.320_all.deb
```

---

### Post by sikandarnoori on 2007-01-28
dear Taurus,

many tnx from your replay,

Noori

---

### Post by marvelchip on 2008-01-10
> **taurus said:**
> I don't think webmin is in the repos.  However, you can download a .deb from here.

```

wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.320_all.deb

```
Then, you can install it with

```
sudo dpkg -i webmin_1.320_all.deb
```


Say I have downloaded the webmin on flash, how does the system know that its on flash, or does this command (sudo dpkg -i webmin_1.320_all.deb) automatically assume the file is on CDrom???

---

### Post by taurus on 2008-01-10
> **marvelchip said:**
> Say I have downloaded the webmin on flash, how does the system know that its on flash, or does this command (sudo dpkg -i webmin_1.320_all.deb) automatically assume the file is on CDrom???

If you saved it to a CDROM, then you need to change directory to where the CDROM is mounted first before you run that command to install it.  Otherwise, you can include the whole path if you wish.

---

### Post by marvelchip on 2008-01-11
Just to get a clearer picture (as i`m new to the Linux world), by default where does the command (sudo dpkg -i webmin_1.320_all.deb) tell the system to get the webmin from???
If its on cd/flash what command do i need to run it??

---

### Post by dir3wolf on 2008-01-11
sudo dpkg -i webmin_1.320_all.deb

This command tells the system to install package **webmin_1.320_all.deb** from the folder you're running it from.
When you open terminal you're located in your home folder. If there is no webmin_1.320_all.deb package in your home folder you'll get this:
```
d3vetka@lapi:~$ [COLOR="Red"]sudo dpkg -i webmin_1.320_all.deb[/COLOR]
[COLOR="Blue"]dpkg: error processing webmin_1.320_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 webmin_1.320_all.deb[/COLOR]
```
So, if you have webmin_1.320_all.deb on your flash memory you should navigate to it in the terminal and then run that command.
In may case that looks like this:

```
d3vetka@lapi:~$ [COLOR="Red"]cd /media[/COLOR]
```This is where ubuntu mounts external memory

```
d3vetka@lapi:/media$ [COLOR="Red"]ls[/COLOR]
cdrom  cdrom0  [COLOR="blue"]**N95 GIGA**[/COLOR]
```In my case external memory is my phone. Here you'll see what is the system name of your memory. Here it is N95 GIGA.

```
d3vetka@lapi:/media$ [COLOR="Red"]cd N95\ GIGA/[/COLOR]
d3vetka@lapi:/media/N95 GIGA$ [COLOR="Red"]sudo dpkg -i webmin_1.320_all.deb[/COLOR]
```
Navigate to the folder named after your flash memory and run the command.

---

