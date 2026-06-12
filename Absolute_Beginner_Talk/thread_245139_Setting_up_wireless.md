---
title: "Setting up wireless"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by fluoridw on 2006-08-27
I am currently installing ubuntu onto my dell inspiron 6400. It uses the wireless intel chipset 

Intel® PRO/Wireless 3945 802.11 a/b/g wireless LAN card

I have yet to figure out how to install the drivers, i have found the intel drivers for linux but dont know how to install them becuase I am totally new to linux.

[http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=2259&dwnldid=10315&agr=y&lang=eng&prdmap=2259](http://downloadfinder.intel.com/scripts-df-external/detail_desc.aspx?strstate=live&productid=2259&dwnldid=10315&agr=y&lang=eng&prdmap=2259)
I hope you can help me. and thanks in advance!

---

### Post by Bachstelze on 2006-08-27
Hi and welcome to Ubuntu :)

Extract the archives, you fill find a petty throughout README.

---

### Post by fluoridw on 2006-08-27
Like I said I am totally new to linux. I read the read-me and no luck.

A form of a step by step guide would be much easier because it would get me started and maybe even help me learn how to use terminal and so on.

Please do not just tell me to read the read-me. I did before I posted this with no luck whatsoever.

---

### Post by Bachstelze on 2006-08-27
```

First, we build and install the ieee80211 subsystem.  You can obtain
the latest ieee80211 subsystem from http://ieee80211.sf.net.  We
recommend version 1.1.12 or newer:

        % tar xzvf ieee80211-1.1.12.tgz
        % cd ieee80211-1.1.12
        % make
        # make install   <--- You may need to be root
        % cd ..

```

Did you go and download the mentioned module ?

---

### Post by fluoridw on 2006-08-27
Yes I have it downloaded and I am running ubuntu right now. But I really don't know what to do and don't understand the install document because I don't now command line terminal yet.

---

### Post by Bachstelze on 2006-08-27
All right so go to the directory you downloaded the archive in, then run those commands :

```

tar xzvf ieee80211-*.tgz
cd ieee80211-*
make
sudo make install
```

Replace * with thz correct version number, you can use the Tab key to complete filenames automagically. Also, if you get "make : command not found", run

```
sudo apt-get install build-essential
```

---

### Post by fluoridw on 2006-08-27
You mention going to the directory I downloaded the archive in but how do I do that?

---

### Post by Bachstelze on 2006-08-27
with the cd command in a terminal :)

---

### Post by fluoridw on 2006-08-27
I got make: command not found and I ran 

sudo apt-get install build-essential

but then when I try

sudo make install

I get: make: *** no rule to make target 'install'. stop.

---

### Post by Bachstelze on 2006-08-27
Did you run make after installing the b-e ?

---

### Post by fluoridw on 2006-08-27
yeah that was my mistake but now I get this:

fluoride@fluoride-laptop:~/Desktop/ieee80211-1.2.15$ sudo make install
make -C /lib/modules/2.6.15-26-386/build M=/home/fluoride/Desktop/ieee80211-1.2.15 modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2
fluoride@fluoride-laptop:~/Desktop/ieee80211-1.2.15$


plus what applicaton should I get to manage my wireless and whats the proper command? apt-get "program name" ?

---

### Post by Bachstelze on 2006-08-27
It will be a little more complicated than that ;) Well anyway, you need the headers for your kernel, run

```
sudo apt-get install linux-headers-2.6.15-26-386
```

---

### Post by fluoridw on 2006-08-27
I get this:

fluoride@fluoride-laptop:~/Desktop/ieee80211-1.2.15$ sudo apt-get install linux headers-2.6-26-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package headers-2.6-26-386


whats next?

---

### Post by Bachstelze on 2006-08-27
linux[size=7]-[/size]headers-2.6**.15**-26-386 ;)

You can use copy/paste to avoid such mistakes.

---

### Post by fluoridw on 2006-08-27
Alright I have done that and what am I supposed to do now? How do I know if everything is working or is there more?

---

### Post by Bachstelze on 2006-08-27
```

Once the ieee80211 subsystem is installed, we build the ipw3945.ko module:

        % tar xzvf ipw3945-1.0.0.tgz
        % cd ipw3945-1.0.0
        % make

```

so you browse to the directory where you extracted your drivers' archive (the first one and run those :)

You will not need to run the first one if you already extracted the archive in the archive.

---

### Post by fluoridw on 2006-08-27
right im confused this is where I am right now:

fluoride@fluoride-laptop:~/Desktop/ieee80211-1.2.15$


but dont know what to do next.

---

### Post by Bachstelze on 2006-08-27
where did you download the first archive ?

---

### Post by fluoridw on 2006-08-27
on my Desktop

---

### Post by Bachstelze on 2006-08-27
All right so here you go :

cd ~/Desktop/intel-ipw3945-1.0.0/ipw3945-1.0.0
make
wget [http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz](http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz)
DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" /etc/hotplug/firmware.agent)
tar xzvf ipw3945-ucode-1.13.tgz
cp ipw3945-ucode-1.13/ipw3945.ucode $DIR

no, it's not over yet :p but tell me if you get a problem here

---

### Post by fluoridw on 2006-08-28
Alright well I actually was able to install the package and all today due to a friends help, but what is a program that allows me to search for wireless networks/acces points and so on.

---

