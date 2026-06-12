---
title: "Troubles with Skype"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-05-27
I just don't seem to be able to reinstall skype...
Due to a problem with libc6, which I had changed to the unstable version and that I couldn't downgrade without having to reinstall my whole system... Well I reinstalled everything from scratch
Everything is working, except that I don't succeed to reinstall skype.
I've tried the version that is on [www.skype.com]("www.skype.com") and I've tried the skype in the universe by adding 
> deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

to my sources.list and then doing
```
sudo apt-get update
sudo apt-get install skype
```
But whatever I try, each time I get the message that there are unresolved dependencies.
> De volgende pakketten hebben niet-voldane vereisten:
  skype: Vereisten: libqt3-mt maar het is niet installeerbaar of
                    libqt3c102-mt (>= 3:3.3.3.2) maar het is niet installeerbaarE: Niet-werkende pakketten:


So I tried to install those dependencies
```
sudo apt-get install libqt3-mt
```

And I get:
> Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Pakket libqt3-mt is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
Echter, de volgende pakketten vervangen dit:
  libqt3c102-mt


Which basically says that I have to install libqt3c102-mt
So...
```
sudo apt-get install libqt3c102-mt
```
And then:
> Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Pakket libqt3c102-mt is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket libqt3c102-mt heeft geen installeerbare kandidaat


... and this says that even if some other package refers to is, libqt3c102-mt has no package that I can install.

So now I don't know what to do...
I guess that I don't have the right repository... but I'm not sure...
This is my sources.list:
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


##deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
##deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

##SKYPE

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free




As you can see I've enabled all the standard repos and added one for skype.

Anyone that has any idea of how I can fix this dependency problem or how I can install Skype without all this junk?

---

### Post by Kimm on 2006-05-27
libqt3-mt and libqt3c102-mt is basicly the same package, the problem your having is that these two packages can not coexist.

libqt3c102-mt is the name used by debian (and up untill Breezy, Ubuntu aswell), that is why the Skype package is asking for it. There is however a way to solve the problem.

Download the Skype package from skype.com and extract it in a temporary directory (lets call that directory: temp), in the temporary directory you should now have two files, data.tar.gz and control.tar.gz.
Extract data.tar.gz in the temporary directory like this:

tar xvzf data.tar.gz

Then create a new directory named DEBIAN (Must be capital letters!), then move control.tar.gz to that folder and extract it in the same maner as we extracted data.tar.gz (tar xvzj control.tar.gz)

You should now be facing a file named "control" (along with some others), open this file in a text editor and find the replace option, set the first value as "libqt3c102-mt" and the secund value (the one to replace with) as "libqt3-mt" and press OK.

Now, make sure you deleated all the archives (data.tar.gz, control.tar.gz and skype*.deb) and cd to you home directory (cd ~), then type this in your terminal (might might need to install dpkg-dev):

dpkg-deb -b temp
sudo dpkg -i temp.deb

that should set you up with a working skype setup.

---

### Post by Ecthelion on 2006-05-27
First of all thanks for your help.

I've tried what you adviced, but it didn't worked...

[QUOTE=Kimm]libqt3-mt and libqt3c102-mt is basicly the same package, the problem your having is that these two packages can not coexist.[/QUOTE]

Problem isn't that they cannot coexist...
The problem is that none CAN exist... I mean, I can't install them.
Not libqt3-mt nor libqt3c102-mt.

When I try to install libqt3-mt it says that it cannot be installed and that I should install libqt3c102-mt.:-k 
When I try to install libqt3c102-mt it says that even if some other package refers to it (obviously the libqt3-mt package), that there is no version of it that I can install.   ](*,) ](*,)  

I've tried to install the libqt4 instead but that doesn't seem to help... [-( 

Any advice is welcome...

---

### Post by Kimm on 2006-05-27
[http://packages.ubuntu.com/breezy/libs/libqt3-mt](http://packages.ubuntu.com/breezy/libs/libqt3-mt)

That should help you out, every package ubuntu has can be found on that website.

It might help you out :)

---

### Post by patrick295767 on 2006-05-27
TO install skype : you can use this script: 
  
```

#!/bin/bash
###############" installing skype
mkdir /root/miniram
cd /root/miniram
wget http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2
echo "size of skype should be = 10678284  " >> "/root/miniram/log_sizeskype.txt"
echo "Here it is : $(ls -la sky*)" >> "/root/miniram/log_sizeskype.txt"
mkdir /opt
cp /root/miniram/skype_staticQT-1.2.0.18.tar.bz2 /opt/skype_staticQT-1.2.0.18.tar.bz2 
cd /opt
tar -xjf skype_staticQT-1.2.0.18.tar.bz2
cd skype-1.2.0.18
chmod +x skype
cd /opt/skype-1.2.0.18
ln -s /opt/skype-1.2.0.18/skype /usr/bin/skype
rm -rf /opt/skype_staticQT-1.2.0.18.tar.bz2
echo "=> Skype staticQT-1.2.0.18 Installed !!"
#################" end skype ###

```
  
That's one easy way too !!  :KS :KS

---

### Post by Ecthelion on 2006-05-27
[QUOTE=patrick295767]TO install skype : you can use this script: 
  
```

#!/bin/bash
###############" installing skype
mkdir /root/miniram
cd /root/miniram
wget http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2
echo "size of skype should be = 10678284  " >> "/root/miniram/log_sizeskype.txt"
echo "Here it is : $(ls -la sky*)" >> "/root/miniram/log_sizeskype.txt"
mkdir /opt
cp /root/miniram/skype_staticQT-1.2.0.18.tar.bz2 /opt/skype_staticQT-1.2.0.18.tar.bz2 
cd /opt
tar -xjf skype_staticQT-1.2.0.18.tar.bz2
cd skype-1.2.0.18
chmod +x skype
cd /opt/skype-1.2.0.18
ln -s /opt/skype-1.2.0.18/skype /usr/bin/skype
rm -rf /opt/skype_staticQT-1.2.0.18.tar.bz2
echo "=> Skype staticQT-1.2.0.18 Installed !!"
#################" end skype ###

```
  
That's one easy way too !!  :KS :KS[/QUOTE]


Looks like the easy way doesn't work for me.
I've put your script in a file and tried to execute itin commandline but i get this error:
> chmod 755 skypeinstall
ecthelion@ElvenLounge:~/Desktop$ ./skypeinstall
mkdir: kan map `/root/miniram' niet aanmaken: Toegang geweigerd
./skypeinstall: line 4: cd: /root/miniram: Onbekend bestand of map
wget: ontbrekende URL
Aanroep: wget [OPTIE]... [URL]...

Probeer `wget --help' voor meer opties.
./skypeinstall: line 6: http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2: Onbekend bestand of map
./skypeinstall: line 7: syntax error near unexpected token `newline'
./skypeinstall: line 7: `echo "size of skype should be = 10678284  " >> '
ecthelion@ElvenLounge:~/Desktop$ sudo ./skypeinstall
wget: ontbrekende URL
Aanroep: wget [OPTIE]... [URL]...

Probeer `wget --help' voor meer opties.
./skypeinstall: line 6: http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2: Onbekend bestand of map
./skypeinstall: line 7: syntax error near unexpected token `newline'
./skypeinstall: line 7: `echo "size of skype should be = 10678284  " >> '
ecthelion@ElvenLounge:~/Desktop$ nano skypeinstall
ecthelion@ElvenLounge:~/Desktop$ sudo ./skypeinstall
mkdir: kan map `/root/miniram' niet aanmaken: Bestand bestaat
wget: ontbrekende URL
Aanroep: wget [OPTIE]... [URL]...

Probeer `wget --help' voor meer opties.
./skypeinstall: line 6: http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2: Onbekend bestand of map
./skypeinstall: line 7: syntax error near unexpected token `newline'
./skypeinstall: line 7: `echo "size of skype should be = 10678284  " >> '
ecthelion@ElvenLounge:~/Desktop$ nano skypeinstall
ecthelion@ElvenLounge:~/Desktop$ sudo ./skypeinstall
./skypeinstall: line 1: !/bin/bash: Onbekend bestand of map
mkdir: kan map `/root/miniram' niet aanmaken: Bestand bestaat
./skypeinstall: line 5: syntax error near unexpected token `newline'
./skypeinstall: line 5: `echo "size of skype should be = 10678284  " >> '


So I tried it by copying in command line every essential line
 >  sudo wget http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2
Password:
--15:56:19--  http://patrick295767.sitesled.com/miniram/skype_staticQT-1.2.0.18.tar.bz2
           => `skype_staticQT-1.2.0.18.tar.bz2'
Resolving patrick295767.sitesled.com... failed: Tijdelijke mislukking bij naamoplossing.


I'm starting to think this is really some repos that is missed out or something since I get more and more the message that I cannot install some packages.

[QUOTE=Kimm]http://packages.ubuntu.com/breezy/libs/libqt3-mt

That should help you out, every package ubuntu has can be found on that website.

It might help you out [/QUOTE]

I've been thinking to do that too but I prefer not too... Since it's because I started installing packages that synaptic couldn't install that I got my system not working anymore.
And that I had to reinstall from scratch.
Still I'll give it a try... As long as it's not in the unstable... I've learned my lesson.

---

### Post by Ecthelion on 2006-05-27
[QUOTE=Ecthelion]
Quote:
Originally Posted by Kimm
[http://packages.ubuntu.com/breezy/libs/libqt3-mt](http://packages.ubuntu.com/breezy/libs/libqt3-mt)

That should help you out, every package ubuntu has can be found on that website.

It might help you out

I've been thinking to do that too but I prefer not too... Since it's because I started installing packages that synaptic couldn't install that I got my system not working anymore.
And that I had to reinstall from scratch.
Still I'll give it a try... As long as it's not in the unstable... I've learned my lesson.[/QUOTE]

Alright, it's working again...
Thank all of you!

Still i'm wondering how come that while it IS in the synaptic list, that synaptic won't install it...
> libqt3c102-mt:

Pakket libqt3c102-mt is niet beschikbaar, maar bestaat wel in de database.
Dit betekent meestal dat het pakket genoemd is als afhankelijkheid en niet beschikbaar is gemaakt, verouderd is of niet beschikbaar is vanwege de huidige bronnenlijst


Basically telling that it is in the list for i it was called for as dependencie but that it is made unusable because it is too old or because of my current repository list.

So does that mean that it is only in the list because if someone wants to install it it would say to install another package?...
But why couldn't I install that other package using synaptic then?

:confused: CONFUSED:confused:

---

### Post by patrick295767 on 2006-05-27
[QUOTE=Ecthelion]Looks like the easy way doesn't work for me.
I've put your script in a file and tried to execute itin commandline but i get this error:


So I tried it by copying in command line every essential line
 

I'm starting to think this is really some repos that is missed out or something since I get more and more the message that I cannot install some packages.



I've been thinking to do that too but I prefer not too... Since it's because I started installing packages that synaptic couldn't install that I got my system not working anymore.
And that I had to reinstall from scratch.
Still I'll give it a try... As long as it's not in the unstable... I've learned my lesson.[/QUOTE]

  
you need to be root ! :KS :  

```
sudo bash
chmod +x myskypescript.sh
sh myskypescript.sh
```

---

