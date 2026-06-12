---
title: "install KDE over GNOME"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-08-25
Hey, im tryin to install KDE over GNOME but when i use
sudo apt-get install Kubuntu-desktop

i get errors saying that it couldnt install. Has anyone had this problem... and how'd you get buy it?

~Lance

---

### Post by aysiu on 2005-08-25
Can you post the exact command you typed in and the exact error you got?

---

### Post by noob_Lance on 2005-08-25
ryder18@x1-6-00-11-e3-0a-d0-4d:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed
E: Broken packages
ryder18@x1-6-00-11-e3-0a-d0-4d:~$

---

### Post by aysiu on 2005-08-25
Whoa! I've never seen that.
Maybe you should take the error message's advice.

[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

What happens when you try to install just KDE, instead of the full Kubuntu-desktop?

---

### Post by noob_Lance on 2005-08-25
how can i install jsut kde?

---

### Post by aysiu on 2005-08-25
[QUOTE=noob_Lance]how can i install jsut kde?[/QUOTE]

[i]sudo apt-get update
sudo apt-get install kde[/i]

You can also use Synaptic Package Manager to browse packages if you don't know the exact name of the package you're trying to install:

System > Administration > Synaptic Package Manager.

---

### Post by Koba on 2005-08-25
[QUOTE=noob_Lance]ryder18@x1-6-00-11-e3-0a-d0-4d:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: amarok but it is not going to be installed
E: Broken packages
ryder18@x1-6-00-11-e3-0a-d0-4d:~$[/QUOTE]
 oh...my...gawd... i get the EXACT same message, right down to the last letter... i wonder why our Ubuntu's are condemmed :( i also need help on this exact same problem. i already have kde, but i want kubuntu-desktop...

---

### Post by Koba on 2005-08-25
I DID IT! i fixed our problem. this is how its done, go into console and do type this:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb
sudo dpkg -i amarok_1.3-beta2-1_i386.deb
```
then, after thats done, type:
```
sudo apt-get install kubuntu-desktop
```
and voila! fixed and done!

---

### Post by noob_Lance on 2005-08-26
koba i tried it... didnt work...

aysiu- it worked on the last install... now it wont work this time... wtf:@ lol

---

### Post by Viziri on 2005-08-26
I followed aysiu's advice i get the following error.



Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdesdk but it is not going to be installed
E: Broken packages

 ](*,)

---

### Post by sophtpaw on 2005-08-26
[QUOTE=Koba]I DID IT! i fixed our problem. this is how its done, go into console and do type this:
```
wget http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb
sudo dpkg -i amarok_1.3-beta2-1_i386.deb
```
then, after thats done, type:
```
sudo apt-get install kubuntu-desktop
```
and voila! fixed and done![/QUOTE

Thank you Koba,

Worked for me too. I also had Amarok needed while  installing it another dependency issue arose which was libtag1 ( if i remember right) Anyways, i installed that (i was right there in Synaptic waiting to be clicked for installation and  i was all set. 
Nothing else in the way and then Amarok installed using your clever wget:

wget [http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb](http://www.lsr.ph.ic.ac.uk/~ho1/linux/deb/amarok_1.3-beta2-1_i386.deb)

then:

sudo dpkg -i amarok_1.3-beta2-1_i386.deb installed it

Then all that remained was going back to 

sudo agt-get install kubuntu-desktop

Funny how sometimes it really is as easy as 1,2,3. And the same problem can be a nightmare for someone else. Sr, Nooblance that it hasn't worked out for you yet. As a n00b myself i couldn't say more than make sure you have resolved dependency issues (if it wants amarok give it amarok; if it wants libtag1 as it did in my case, kobo must have had it already, then give it libtag1) then i can't see why kubuntu is not installiing for you.

Good luck mein lieber,

--
sophtpaw

---

### Post by Lord Illidan on 2005-08-26
Try installing via synaptic.. maybe you need to force amarok to a lower version number...

---

### Post by noob_Lance on 2005-08-26
ok i got it to work thru synaptic, but now i cant install the JRE :| and i need my music :| help!!

---

