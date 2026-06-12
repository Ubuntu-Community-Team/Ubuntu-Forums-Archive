---
title: "Is ndiswrapper installed with ubuntu?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by joshbax on 2006-05-17
Hey all, is ndiswrapper installed with ubuntu?

I have a pc with it running on, and a belkin pci wif card, which i cant get online.

If it is installed with it, how do i open it?

Thanks

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=joshbax]Hey all, is ndiswrapper installed with ubuntu?

I have a pc with it running on, and a belkin pci wif card, which i cant get online.

If it is installed with it, how do i open it?

Thanks[/QUOTE]
I believe that ndiswrapper comes with Breezy but as I recall, it is broken. Do the following to completly remove ndiswrapper and reinstall it.

> sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Now, follow [ this tutorial](http://ubuntuforums.org/showthread.php?t=112526&highlight=ndiswrapper) Please note that you will need the windows drivers for your wireless card. The files are often avaible from your laptop/desktop distributor's website. They may be in .exe format but you can use wine to extract the files.

---

### Post by joshbax on 2006-05-17
ok thanks.

is wine installed with ubuntu then?

and another problem, on the guide it says i need to topen the synaptic package manager. but when i click on it, nothing happens.

i just tried that 1st command you told me, and i got

```

josh@HAL-9000:~$ sudo rmmod ndiswrapper
sudo: unable to lookup HAL-9000 via getbyhostname()

```

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=joshbax]ok thanks.

is wine installed with ubuntu then?[/QUOTE]
No, wine is avaible in the repositories though. There is a link in my signature entitled, "Extra Repositories for Breezy/Dapper." You may need to add these to gain acess to the repository with wine. If you think that you already have the repositories enabled, in terminal type:

> sudo apt-get install wine

If you extract the files from an .exe file, the files will be extracted to /home/Username/.wine/drive_c/ and then it should be in one of the folders. If you are using nautilus to browse that directory, make sure you have "Show Hidden Files" checked. (It should be under View)

---

### Post by joshbax on 2006-05-17
i don't have an internet connection on it though, so apt-get won't work. should i move the pc downstaris so i can get a hard-wire connection, and download all the stuff i need and then try the steps here?

PS i added this above

i just tried the 1st command  you told me and i got

```
josh@HAL-9000:~$ sudo rmmod ndiswrapper
sudo: unable to lookup HAL-9000 via getbyhostname()
```

---

### Post by Jagot on 2006-05-17
[QUOTE=joshbax]is ndiswrapper installed with ubuntu?[/QUOTE]

The ndiswrapper modules are installed with Ubuntu but you must have the ndiswrapper-utils package to get it working.  Ndiswrapper in the form it is supplied with in a default Breezy installation is not functional.

You can download the .deb on another computer and transfer it over to your Ubuntu computer from here:

[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils)

Download the dependencies listed there also.  Then you can follow any tutorial for ndiswrapper to get it working.

---

### Post by joshbax on 2006-05-17
ok i will do all of that and let you know my outcome! thanks.

---

### Post by az on 2006-05-17
Ndiswrapper is most deffinitely functional in Breezy!  The ndiswrapper module is in the kernel and the userspace utility IS ON THE CD!

Install ndiswrapper-utils (Use synaptic - you do not have to be on the net) and you are good to go.  If you check the changelogs in the upstream ndiswrapper, there is very little change between the current bleeding-edge ndiswrapper and the one that comes with breezy.  There is no reason to remove the one that ships and recompile ndiswrapper from source.


Just make sure you are using the latest .inf file for your card.  The one that came in the box may be too old.

---

### Post by joshbax on 2006-05-17
ok sounds great.

but when i click on the synaptic manager, it doesn't open. nothing happens.

---

### Post by az on 2006-05-17
[QUOTE=joshbax]ok sounds great.

but when i click on the synaptic manager, it doesn't open. nothing happens.[/QUOTE]
Open up a terminal and run

sudo apt-get -f install

sudo apt-get install ubuntu-desktop

sudo synaptic


and post the results, please....

---

### Post by Bpa on 2006-05-22
I don't understand what package we need to get from that page you give. At the bottom there aren't any .deb files and when you click on any of the top links it just goes to another page with information on that file.  I don't have my original CD or I would just use synaptic or apt-get to get the ndiswrapper-utils. I need to know exactly what to dload and what to install in order to get ndiswrapper to work.(moving all files with a flash drive)  

Thanks,
Barret

---

### Post by Bpa on 2006-05-22
[QUOTE=Jagot]You can download the .deb on another computer and transfer it over to your Ubuntu computer from here:

[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils)

Download the dependencies listed there also.  Then you can follow any tutorial for ndiswrapper to get it working.[/QUOTE]

Sorry, this was the quote I was replying to.

---

### Post by Bpa on 2006-05-22
[QUOTE=Bpa]I don't understand what package we need to get from that page you give. At the bottom there aren't any .deb files and when you click on any of the top links it just goes to another page with information on that file.  I don't have my original CD or I would just use synaptic or apt-get to get the ndiswrapper-utils. I need to know exactly what to dload and what to install in order to get ndiswrapper to work.(moving all files with a flash drive)  

Thanks,
Barret[/QUOTE]

Sorry, lol I figured it out. You must go to the part where it says Download ndiswrapper-utils and then click on the architechture you want (x386 or AMD64). Then click on the mirror for your location. I was clicking on the part where it said "list of files" every time, and it would just bring me into an infinite loop of going back to the same page.  Just figured I'd post this in case anyone else is as retarded as I am.  

Good day!

---

### Post by joshbax on 2006-05-22
Hey all! 

Ok I got my ubuntu working fine.

I was using a dodgy hard disk on that install it turns out, so I used a new SATA one and it's all good.

I used the below guide
[http://www.mozmarks.com/james/node/4?PHPSESSID=fd17d18b4ffbdf75e716ab540d740b31](http://www.mozmarks.com/james/node/4?PHPSESSID=fd17d18b4ffbdf75e716ab540d740b31)
and it saved my ***. it was my exact wifi card, and exact linunx distro. So lucky! lol

synaptic now works. But for some reason it wont let me connect to the WINE repositories... It says bad connection or somehting like that. Just trouble downloading in general.

---

