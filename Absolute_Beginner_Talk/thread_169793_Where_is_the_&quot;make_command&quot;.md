---
title: "Where is the &quot;make command&quot; ?"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by pcsbill on 2006-05-03
Can anyone tell me how to execute the make command in a terminal/console session? I am trying to install a small hardware hotkey package but when i enter the _make_ command, bash reports it as an unrecognised command. It also reports the same thing for ./configure. Can anyone please help. I am very new to this Linux thing....just hate MS windows!

---

### Post by user1397 on 2006-05-03
in a terminal (applicarions>accessories>terminal), type:
```
sudo apt-get update
```
```
sudo apt-get install build-essential
``` then you will be able to do the "make", "./configure", and "sudo make install" commands

---

### Post by rado_london on 2006-05-03
Can you tell us what package are you trying to install and what files does it contain. Sometimes there are no configure or make options.

---

### Post by Sef on 2006-05-03
You should update the repositories first before installing.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by Jeroen Vernooij on 2006-05-03
See *make* as a program you need to have to install software.
The problem is, *make* isn't included by default in ubuntu.. 
So you need to be connected to internet to get build-essential (which includes *make*, and other important software)

---

### Post by pellgarlic on 2006-05-03
ok, i feel like a human "chicken-and-egg" puzzle here - i'm having the same problem as the original poster (i.e. i am trying to install something using the "make" command, but bash does not recognise it). 

hopefully the excellent answer will help the original poster, but unfortunately, it leaves me in a tight spot - what i am having trouble trying to install is drivers for my modem! so obviously, i can't apt-get anything to help me.

it's an intel 536ep chipset-based winmodem (boo!) which i would rather get working than have to buy another modem, especially seeing as how last time i went into a computer shop and asked for a "hardware only" modem (i.e. not one of these "controllerless" jobs), they all but laughed me out of the shop.

however, information i found on this forum (which is superb by the way!) pointed me to intel's website, who indeed have "linux driver" downloads for this modem. however, back to my original problem - it needs "built".

i have downloaded the build-essential_10.1_i386.deb from [www.debian.org](www.debian.org), and have found out how to install .deb files from [www.ubuntuguide.org](www.ubuntuguide.org), but i am unsure if not being able to update the repositories first will cause me great problems, or if there is a better way of doing this?

although i'm a relative newcomer to linux, i'm used to messing around with the inner workings of windows, and have tried a couple of distros before now, (ubuntu really caught my attention - that's why i'm pursuing a working, everyday system using it, so i can finally free myself from bill gates clutches), so i'm not a PC novice, and i should be pretty easy to instruct.

---

### Post by Radon on 2006-05-03
I am in the same position as you pellgarlic.  I am a Mandriva user but downloaded Ubuntu 6.06 beta 2 and am starting to love it.

I have it installed but also need to get *build-essential* from the internet to install the internet drivers (pppoe, speedtouch 300 adsl modem).

Not including *make* into a **beta** release was very ](*,) imho.  Why does Ubuntu hate it so much?  Richard Stallman isn't such a bad guy.  

You could have at least created a script that after a set amount of time (eg. a week) uninstalls *make* from the system after installing Ubuntu to the HDD.

However, thanks to this great community there is a [HowTo: Install gcc-3.4 via apt-get without an Internet connection]("http://www.ubuntuforums.org/showthread.php?t=79896") which I will try out at school tomorrow.

---

### Post by nanotube on 2006-05-03
hmm, the contents of build-essential should also be available on the installation cd. try popping that in, make sure that the cd repository is enabled (should be by default), and then apt-get your build-essential.

---

### Post by patrick295767 on 2006-05-03
My recommanded installations in your linux machine, via script again to make it easy:
  
```

#!/bin/bash
apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 
```
  
Greetings !!

---

### Post by pellgarlic on 2006-05-04
[QUOTE=nanotube]hmm, the contents of build-essential should also be available on the installation cd. try popping that in, make sure that the cd repository is enabled (should be by default), and then apt-get your build-essential.[/QUOTE]

cool, i will check that out, thanks nanotube. after reading that, i checked on [http://packages.ubuntu.com/hoary](http://packages.ubuntu.com/hoary) what packages were included with ubuntu, and sure enough, build-essential is there: [http://packages.ubuntu.com/hoary/devel/build-essential](http://packages.ubuntu.com/hoary/devel/build-essential) (i'm not 100% sure whether that means it's on the cd, or if it's only available in the repositories though...)

however, on closer inspection of the "Other Packages Related to build-essential" section, i see that "make" is listed. so i checked the "list of files" link for "build-essential" itself, and it looks to me like the "build-essential" package is only a list of files deemed "essential" for building Debian packages, and does not appear to include "make". 

i have downloaded "make" separately, as i think it is more likely to help me. (of course, it seems that should also be on the ubuntu cd, but there's no harm in having two options). but do i need to install "build-essential" in order for "make" to work? annoyingly, i can't check these things out until i get home from work tonight, or i'd try it right now! i much prefer testing things out myself rather than asking dumb questions, but if i can gather as much info at once, it'll be easier to sort the problem when i get home.

hi radon - i looked at that link you provided, and it's making me think this is going to be a bigger job than i first thought. seems like not only do i have to build the drivers myself, i have to mess about with the kernel? is this right? i have read a lot of posts from people having problems installing this modem, mostly with the Intel536_inst and Intel536_boot scripts. could this kernel incompatibility be the problem?

---

### Post by engla on 2006-05-04
[QUOTE=pellgarlic]cool, i will check that out, thanks nanotube. after reading that, i checked on [http://packages.ubuntu.com/hoary](http://packages.ubuntu.com/hoary) what packages were included with ubuntu, and sure enough, build-essential is there: [http://packages.ubuntu.com/hoary/devel/build-essential](http://packages.ubuntu.com/hoary/devel/build-essential) (i'm not 100% sure whether that means it's on the cd, or if it's only available in the repositories though...)

however, on closer inspection of the "Other Packages Related to build-essential" section, i see that "make" is listed. so i checked the "list of files" link for "build-essential" itself, and it looks to me like the "build-essential" package is only a list of files deemed "essential" for building Debian packages, and does not appear to include "make". 

i have downloaded "make" separately, as i think it is more likely to help me. (of course, it seems that should also be on the ubuntu cd, but there's no harm in having two options). but do i need to install "build-essential" in order for "make" to work? annoyingly, i can't check these things out until i get home from work tonight, or i'd try it right now! i much prefer testing things out myself rather than asking dumb questions, but if i can gather as much info at once, it'll be easier to sort the problem when i get home.

hi radon - i looked at that link you provided, and it's making me think this is going to be a bigger job than i first thought. seems like not only do i have to build the drivers myself, i have to mess about with the kernel? is this right? i have read a lot of posts from people having problems installing this modem, mostly with the Intel536_inst and Intel536_boot scripts. could this kernel incompatibility be the problem?[/QUOTE]

Well, build-essential is just a **meta-package**, that is, just a list of things that are essential. So the first thing you downloaded was just the list (the build-essential...deb file) and make is then just one thing on the list (the make....deb file). What you need: **All** files on the list (this is called all the **dependencies**)!

What you should do: Make sure the CD is added to your repositories (For example in synaptics you can use "Add CD.."), then try installing build-essential via synaptic.

---

### Post by pellgarlic on 2006-05-04
:D joy! 

as i write this, i am using my  sparkly new installation of ubuntu, with my own "remixed" version of the modem drivers i got off intel's website!

i indeed was able to install build-essential from the ubuntu install cd (and it brought "make" and a few other things with it automatically), so thanks nanotube and engla. i didn't even have to do the "add cd-rom" step - it was already there when i opened synaptic :) 

i still had problems installing the driver though - i got "gcc-3.4: Command not found" amongst other things, so i followed the link in radon's post for installing gcc-3.4. that got me almost all the way there, but the boot scripts still wouldn't install. 

in the included readme, it says that debian is supported, but in the Intel536_inst itself, there is no section looking for debian installation, only redhat, mandrake, suse and a couple of others.

i did a bit of digging and nosing around in /etc to find out where the script should be installing the files to, and managed to figure it out, edit the install script to include a section for recognising ubuntu, and away i went! 

woohoo! 

(p.s. in case anyone else is having problems installing this modem, here is the section i added to the Intel536_inst  to make it work: (i just put it between two existing ones - look for the "elif [-a /etc/whatever_distribution ]" which marks each one)

```

elif [ -a /etc/debian_version ]; then
{
   if [ -a ./hamregistry.bin ]; then
   {
      mv -f /etc/hamregistry.bin /etc/hamregistry.bak
      cp ./hamregistry.bin /etc/hamregistry.bin
   }
   else
   {
      rm -f /etc/hamregistry.bin
   }
   fi
   echo installing hamregistry, used for persistant storage
   install -o root -g root -m 110 hamregistry /usr/sbin
   echo installing Intel536 driver
case $KERNVER in
   2.4*)
      install -o root -g root -m 664 Intel536.o ${CharModDir}/Intel536.o || exit 1
      ;;
   2.6*)
      install -o root -g root -m 664 Intel536.ko ${CharModDir}/Intel536.ko || exit 1
      ;;
esac

   echo debian hamboot rc2.d and rc3.d scripts
   install -o root -g root -m 110 Intel536_boot /etc/init.d
   ln -s -f /etc/init.d/Intel536_boot /etc/rc2.d/S99_Intel536
   ln -s -f /etc/init.d/Intel536_boot /etc/rc3.d/S99_Intel536
   ln -s -f /etc/init.d/Intel536_boot /etc/rc5.d/S99_Intel536
}

```

but bear in mind that this may not work on your setup. i think it probably should be ok if you have 5.10 installed, as i have, but i am just beginning to learn, and i took a chance by making these changes - i could have messed up the installation altogether for all i knew. maybe those more experienced users here can cast a critical eye over this?

---

