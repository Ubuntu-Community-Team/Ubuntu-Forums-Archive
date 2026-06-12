---
title: "Possible to get one of my modems connected?"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by fruitsofherwomb on 2007-04-20
ok this is very simple. I want to know if its possible to get either of these modems connected. I'll give you as much possible information. 

First: 

is a winmodem i guess, it says Lucent Win Modem. after seeing for more info on the 'pc' i got it from (old HP Pavilion 521c) 

and the other one is: 

Creative Modem Blaster V.92 PCI Model D15633. 

Any, suggestions to get my linux connection up and connected would be greatly appreciated. 

:grin:

---

### Post by Bachstelze on 2007-04-20
Please do a scanModem scan on each of those and post the results (the ModemData.txt file, most importantly).

[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

---

### Post by fruitsofherwomb on 2007-04-20
ok, I did it for one modem and was going to post it. Problem is How do I access my Linux Portion through windows?

---

### Post by Bachstelze on 2007-04-20
Google for "ext2ifs".

---

### Post by fruitsofherwomb on 2007-04-20
modemdata.txt: 
> Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:09.0	11c1:044e	1235:044e	Communication controller: Agere Systems LT WinModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:09.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  00:09.0
   Class 0780: 11c1:044e Communication controller: Agere Systems LT WinModem
      Primary PCI_id  11c1:044e
 Support type needed or chipset:	Agere.DSP
 


 The modem has a supported Lucent/Agere  Mars or Apollo DSP (digital signal 
 processing) chipset. Support packages for 2.6.n kernels are at: 
 [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)
 For a temporary fix for 2.6.18 kernels see 

 See AgereDSP.txt for Details.
  DSP=1

 Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
 code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

 0x044e -- Mars 3 Mercury data fax only
-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 12:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)


 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------


Thought this is the one you wanted, theres like10 other txts .

---

### Post by Bachstelze on 2007-04-20
OK, drivers for your modem exist. I'm at school right now so I can't help you much about compiling them but when I'll be back home, I'll look into it. Meanwhile, see what you can do by yourself, all you need id there :

[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

---

### Post by fruitsofherwomb on 2007-04-20
Thanks you have been very helpful :)

---

### Post by fruitsofherwomb on 2007-04-20
Ok, I looked at all the files, I'm a linux n00b and don't know what i'm doing 8-[ 

So, I know there is someone out there that can help besides HymnToLife to install these drivers. 

:(

---

### Post by fruitsofherwomb on 2007-04-20
BUMP, So close I can almost taste it :(

---

### Post by Bachstelze on 2007-04-20
All right, so here's what to do :

```

sudo apt-get install linux-headers-$(uname -r) build-essential wvdial
mkdir ~/modem
mkdir ~/modem/tmp
cd ~/modem
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-20061203.tar.bz2
wget http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz
tar xjvf martian-20061203.tar.bz2
tar xzvf martian-full-20061203.tar.gz -C tmp
cd martian
cp ../tmp/martian/modem/ltmdmobj.o modem
make clean
make
sudo make install
sudo depmod -a
sudo modprobe martian_dev
sudo martian_modem
sudo wvdialconf /etc/wvdial.conf

```

if all went well, wvdial should detect your modem. You can then remove all this with

```

cd
rm -rf modem
```

as you shouldn't need it again.

---

### Post by fruitsofherwomb on 2007-04-20
wouldn't you need to go online to run this:
wget [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/martian-full-20061203.tar.gz)

???:confused:

---

### Post by Bachstelze on 2007-04-20
Yes. How are you getting online right now ?

---

### Post by fruitsofherwomb on 2007-04-20
well, yes I was going to do it how I did the scan I thought since I can't go online in Linux (I have to boot into linux to  do those commands, sure you know) and you put it in the middle of the code so I thought wget :link: was a command for the system to go online and get a certain file. If it is I can't do that. 

anyway this is the error it gives me in terminal to start with, might be me mistyping or something... I haven't slept in a while..

---

### Post by Bachstelze on 2007-04-20
You just need to get the files. wget is the easiest way but you can also download them in Windows and copy them to the correct place. Also, you need to be more careful when typing comands ;)

---

### Post by fruitsofherwomb on 2007-04-20
where is the 'correct place' last time i did scan modem i just put it in my desktop.... :KS

---

### Post by Bachstelze on 2007-04-20
Copy them to your desktop then do :

```

cd
mv Desktop/martian* modem
cd modem

```

you can then go on with the rest, you won't need to get online anymore.

---

### Post by fruitsofherwomb on 2007-04-20
lol, i tried it for the past 40 mins over and over again :mad: 

```
sudo apt-get install linux-headers-$(uname -r) build-essential wvdial
cd ~/modem
tar xjvf martian-20061203.tar.bz2
tar xzvf martian-full-20061203.tar.gz -C tmp
cd martian
cp ../tmp/martian/modem/ltmdmobj.o modem
make clean
make
sudo make install
sudo depmod -a
sudo modprobe martian_dev
sudo martian_modem
sudo wvdialconf /etc/wvdial.conf

```
is that how I should input it cuz, well. I 'm not going to directly download. 

I get a error right after first line E: cannot get linux-headers-silverslug (my username) or something like that. 

It still lets me cgo on.... after that I get to cp ../tmp/martian/modem/ltmdmobj.o modem is where everything comes to a grinding halt. It says it doesn't exist. Even if i take off the tmp.

---

### Post by Bachstelze on 2007-04-20
Why do you put your username there ?

---

### Post by fruitsofherwomb on 2007-04-20
I thought you were suppose to................ 

my bad. SO i just type it like that?

---

### Post by Bachstelze on 2007-04-20
Yep, just type it like that :)

Also, to be sure it will work, when you do

```
cd ~/modem
```

ls should output this :

```
mfb@ana ~/modem $ ls
martian-20061203.tar.bz2  martian-full-20061203.tar.gz

```

---

### Post by fruitsofherwomb on 2007-04-20
here are the errors that I get ... 

```
sudo apt-get install linux-headers-$(uname -r) build-essential wvdial
```
that gives me a error. Not found or something

```
cp ../tmp/martian/modem/ltmdmobj.o modem
```
that gives me a error as well, i guess there is no ltmdmobj.o modem :confused:

---

### Post by Bachstelze on 2007-04-20
There is one, if you follow exactly what I told you... Let's do it one step at a time, shall we ? First, how did you install Ubuntu ? You'll need some packages and they can be fetched only with an Alternate CD so you'll have to get one if you installed from a Live CD.

---

### Post by fruitsofherwomb on 2007-04-20
I installed it by live cd :(

---

### Post by Bachstelze on 2007-04-20
Maybe it changed with Edgy, I'm not sure... Do this :

```

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add
** insert your CD and press Enter, when you're back to the prompt, do :
sudo apt-get install build-essential
```

If that doesn't work, you'll need to get your hands on an Alternate CD.

---

