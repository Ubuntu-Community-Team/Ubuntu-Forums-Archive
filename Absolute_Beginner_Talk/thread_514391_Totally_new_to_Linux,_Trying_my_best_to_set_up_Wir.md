---
title: "Totally new to Linux, Trying my best to set up Wireless card"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by MonsterCC on 2007-07-31
Ok dudes I am totally new to Linux, but know my way around a computer somewhat. 
So I have currently found out what wireless card I have in my Dell Latitude D600 and have transfered their drivers onto my Ubuntu desktop.
I also have downloaded NDISwrapper in some sort of archive file (tar I believe?) 
And now I am stuck.
I tired my best to get NDISwrapper to work after extracting it but without success.

So can you guys help me out?
If it involves the terminal I pretty much need step by step instructions.
Thanks guys!

---

### Post by Ek0nomik on 2007-07-31
So, what kind of wireless card do you have?

```
lspci
```

should reveal which one if you have if you are second guessing yourself.

---

### Post by MonsterCC on 2007-07-31
A Dell Truemobile 1300 Mini PCI Card
and what I got as the driver was BCMLW5.
I have both the inf and the sys files.

---

### Post by Ek0nomik on 2007-07-31
Here are some pages you may want to look at;

[http://ubuntuforums.org/showthread.php?t=443646](http://ubuntuforums.org/showthread.php?t=443646)

[http://ubuntuforums.org/showthread.php?t=164863](http://ubuntuforums.org/showthread.php?t=164863)

Hopefully these will assist you.

---

### Post by MonsterCC on 2007-07-31
ok but first I need to know how to install ndiswrapper.
I have already got in on my desktop but need to install it.

---

### Post by Ek0nomik on 2007-07-31
> **MonsterCC said:**
> ok but first I need to know how to install ndiswrapper.
I have already got in on my desktop but need to install it.

If you don't have the compiling software, you need to install:

```
sudo apt-get install build-essential
```

Then proceed to untar your ndiswrapper tarball, naviagate into the directory, and build the installation by doing:

```
tar -xzvf ndiswrapper-yourversion.tar.gz
cd ndiswrapper-yourversion
make
make install
```

---

### Post by MonsterCC on 2007-07-31
After "sudo apt-get install build-essential" it is all good until it says "E: Couldn't find package build-essential"

---

### Post by Ek0nomik on 2007-07-31
> **MonsterCC said:**
> After "sudo apt-get install build-essential" it is all good until it says "E: Couldn't find package build-essential"

Try;

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by MonsterCC on 2007-07-31
It didn't work cause I don't have internet without the wireless card.

---

### Post by ugm6hr on 2007-07-31
> **MonsterCC said:**
> It didn't work cause I don't have internet without the wireless card.

This should allow you to locate all the necessary files for download on a different computer, and transfer to Ubuntu with a USB stick:

Just go to Synaptic Package Manager (in System menu) and search for build-essential, and mark it for installation.  Then (in Synaptic) go to File-> Generate Package download script.  This creates a text file with a list of all the files necessary to install the "build-essential" package.  

Open the text file, and manually download all the packages onto a USB stick (or CD-R etc) from a different (internet-connected) computer; they will be at the various URL's listed in the text file.

Back in Ubuntu, open the File Browser (nautilus) and open the USB-stick location.
Press Alt+F2 and type: **gksudo nautilus /var/cache/apt/archives/**
Copy the files from the USB-stick, and paste to /var/cache/apt/archives
Close both nautilus windows.

Then try again:
```
sudo apt-get install build-essential
```

Hopefully, that should now work.

References:
[http://ubuntuforums.org/showpost.php?p=3101014&postcount=5](http://ubuntuforums.org/showpost.php?p=3101014&postcount=5)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jw5801 on 2007-07-31
You can either put in the install CD and add that as a repository (System > Admin > Sources List), or you can get the .deb files from another computer and copy them across to your linux box and then install (don't forget that you'll need to get all the other packages listed there as build-essential is dependant on them.
The .deb files can be found here: [http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)
Then you'll need to either use the graphical package installer or the command line to install the packages:
```
sudo dpkg -i *package-name*.deb
```
where *package-name* is the name of the package you want to install.

---

### Post by MonsterCC on 2007-07-31
Ok So I went into the package manager and did a search but it did not find it.
So then I downloaded the build-essentials as a .deb file on my windows desktop then transfered to my ubuntu laptop. It opened but had a red error message which said:

"Error: Dependency is not satifiable: libc6-dev|libc-dev"

---

### Post by MonsterCC on 2007-07-31
I tired another .deb file automatix (I know you guys disapprove of it but i am getting kinda desperate) and it also had a dependency problem.

---

### Post by aninaiian on 2007-08-01
Out of curiosity, why aren't you using the ndiswrapper packages in the official repos?

---

### Post by anewguy on 2007-08-01
I assume you installed from a LIveCD?  With Ubuntu booted, just put that CD back in the drive.  When Ubuntu recognizes it it will say something to the effect that a media containing software packages has been detected and do you want to run package manager?  - just answer yes or OK (I don't have the CD in right now so I'm not sure of the exact wording).  Then just use search and enter in ndiswrapper.  Select ndiswrapper-common and the ndiswrapper-utils-xxxxx  (mine say 1.9) packages for installation, click apply, and it should be installed.  No compiling, etc., needed - the package will take care of everything.  Please post back if you have further problems or questions.:)

---

### Post by MonsterCC on 2007-08-01
Ok I managaed to et a connetion on my Ubuntu laptop by ripping out the ethernet cable out of my router and putting it into my laptop. I then:

sudo apt-get update

after words i:

sudo apt-get build-essential
but it said i already had it.

so then i installed automatix then Ndiswrapper 
and then 
ndiswrapper -i bcmwl5.inf
then tested it by 
ndiswrapper -l
which said:
bcmwl5: Invalid driver

so THEN I found another possible driver, installed that, and then ndiswrapper -l which yielded:

bcmwl5a:driver installed
              device (14E4:4320) present (alternate driver: bcm43xx)

and now what do i do?

---

### Post by jw5801 on 2007-08-01
You'll need to blacklist the alternate driver!
```
sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit
```
then add ndiswrapper to the kernel modules (as well as to the list of modules that load on startup):
```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo -s
echo ndiswrapper >> /etc/modules
exit
```
and that should get you close. Otherwise look at [this thread](http://ubuntuforums.org/showthread.php?t=297092) and read the issues there as you're almost guaranteed that someone will have encountered whatever problem you come across.

Also, for the record, in my first post I did say that you'd need all the dependancies listed on the page I linked you to if you wanted build-essential to work! :p

---

### Post by MonsterCC on 2007-08-01
Hey Guys!
I fiqured it out without ndiswrapper or anything complicated!
All thanks to this man's blog [http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)
and this pakage: bcm43xx-fwcutter

Thanks For all your guy's help though It was apperciated!
Hopefully with the internet now working I can fully tweak out and enjoy Ubuntu.

Thanks Again!

---

