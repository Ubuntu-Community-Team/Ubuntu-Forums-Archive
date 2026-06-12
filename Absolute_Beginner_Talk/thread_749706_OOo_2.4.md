---
title: "OOo 2.4"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by hikujk123 on 2008-04-08
Is there any safe way to install OpenOffice.org 2.4 in ubuntu gutsy gibbon?

---

### Post by Origin415 on 2008-04-08
Best bet, imo, is to hold off until Hardy releases.

---

### Post by stchman on 2008-04-08
> **hikujk123 said:**
> Is there any safe way to install OpenOffice.org 2.4 in ubuntu gutsy gibbon?

Yes, I have it running on my Feisty installs.  I have a tutorial to install 2.3.1 but it will work for 2.4.  Just sub 2.4 for 2.3.1 as I need to update my procedure.

You must have a JRE installed for all OO functions to work properly.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

You can download the DEB version of OO 2.4 via this link.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0)

---

### Post by fourscore on 2008-04-09
> **stchman said:**
> Yes, I have it running on my Feisty installs.  I have a tutorial to install 2.3.1 but it will work for 2.4.  Just sub 2.4 for 2.3.1 as I need to update my procedure.

You must have a JRE installed for all OO functions to work properly.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

You can download the DEB version of OO 2.4 via this link.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0)

If I install 2.4 using the above procedure  and later if i have to install 2.4.1 ( assuming it is released ) do I have to uninstall 2.4 or  will 2.4.1 install over the prev version.

---

### Post by stchman on 2008-04-09
> **fourscore said:**
> If I install 2.4 using the above procedure  and later if i have to install 2.4.1 ( assuming it is released ) do I have to uninstall 2.4 or  will 2.4.1 install over the prev version.

Uninstall 2.4, it will be easy as all the packages will be listed in Synaptic under

Installed (local or obsolete)

---

### Post by fourscore on 2008-04-09
Few more queries :
- For uninstalling the inbuilt version of OpenOffice can we also go thru the Add/Remove programs by unchecking the  OO package  ? Wouldn't this be easier.
- Will it make any difference in performance, in Hardy(8.04),   if  we install  OO2.4 afresh  after uninstalling the   inbuilt   OO2.4 version.

---

### Post by stchman on 2008-04-09
> **fourscore said:**
> Few more queries :
- For uninstalling the inbuilt version of OpenOffice can we also go thru the Add/Remove programs by unchecking the  OO package  ? Wouldn't this be easier.
- Will it make any difference in performance, in Hardy(8.04),   if  we install  OO2.4 afresh  after uninstalling the   inbuilt   OO2.4 version.

If I did not supply a one line statement to uninstall the stock OO software then the answer is yes.  I have eliminated the searching you will need to do.

I cannot comment of the OO included with Hardy as I have never used Hardy.  I don't plan on using Hardy until a month after it's release.

---

### Post by boombox1387 on 2008-04-12
Okay, so I've successfully installed 2.4 in Gutsy after following a couple tutorials, and it's fast and awesome.  There are just two things, though:

The Ubuntu Update Manager thinks that 2.3 is newer than 2.4 and prompts me to update all the time.

I miss the Human theme from 2.3.  I liked the old icons and splash screen a lot better.  Any way to change this?

---

### Post by hikujk123 on 2008-04-12
The link you provided has a download for linuxintel.  Is there a linux install for amd64?

---

### Post by Oldsoldier2003 on 2008-04-12
> **boombox1387 said:**
> :

The Ubuntu Update Manager thinks that 2.3 is newer than 2.4 and prompts me to update all the time.



Go into synaptic and lock the versions then in order to lock them in apt :
```
sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences
```
Its a known issue that apt-get doesn't respect the package locks in synaptic, so creating a link prevents you from having to relock the packages from the command line.

Actually you can lock the packages from the command line and synaptic will respect the locks, but it is easier for the average user (includes myself in this one ) to do it in synaptic.

---

### Post by boombox1387 on 2008-04-12
> **hikujk123 said:**
> The link you provided has a download for linuxintel.  Is there a linux install for amd64?

I'm running amd64 and the Intel install worked fine for me.  I didn't see a separate installer for amd64 anywhere.

---

### Post by boombox1387 on 2008-04-12
Thanks for this Oldsoldier, I'll give it a shot as soon as I'm back at my own computer.

---

### Post by hikujk123 on 2008-04-12
> **Oldsoldier2003 said:**
> Go into synaptic and lock the versions then in order to lock them in apt :
```
sudo ln -fs /var/lib/synaptic/preferences /etc/apt/preferences
```
Its a known issue that apt-get doesn't respect the package locks in synaptic, so creating a link prevents you from having to relock the packages from the command line.

Actually you can lock the packages from the command line and synaptic will respect the locks, but it is easier for the average user (includes myself in this one ) to do it in synaptic.


How do you do this in kubuntu?

---

### Post by Oldsoldier2003 on 2008-04-12
> **hikujk123 said:**
> How do you do this in kubuntu?

I dont use Kubuntu anymore but you should be able to change the command to point to adept instead of synaptic.

```
sudo ln -fs /var/lib/adept/preferences /etc/apt/preferences
```

---

### Post by hikujk123 on 2008-04-13
I get this error for all .deb packages:

dpkg: error processing openoffice.org-base_2.4.0-12_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


Does anyone know how to fix this?

---

### Post by hikujk123 on 2008-04-14
bump

---

### Post by stchman on 2008-04-14
> **hikujk123 said:**
> I get this error for all .deb packages:

dpkg: error processing openoffice.org-base_2.4.0-12_i386.deb (--install):
 package architecture (i386) does not match system (amd64)


Does anyone know how to fix this?

Pretty self explanatory.  You are attempting to install 32bit debs onto a 64bit machine.  Since you are running 64bit Ubuntu you will either need to wait until OO2.4 hits the repos or build it from source.

You can Google to see if anyone has made 64 bit debs.

---

### Post by fourscore on 2008-04-14
> **stchman said:**
> Yes, I have it running on my Feisty installs.  I have a tutorial to install 2.3.1 but it will work for 2.4.  Just sub 2.4 for 2.3.1 as I need to update my procedure.

You must have a JRE installed for all OO functions to work properly.

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

You can download the DEB version of OO 2.4 via this link.

[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.4.0)
Have managed to successfully install  OO2.4 in Gutsy based on the instructions above.   Few observations -  In the  earlier 2.3 ver which came with gutsy  there was an option to enable Loading of quickstarter at startup.   In  OO2.4 (directly downloaded from OO.org)   it is missing but in the windows version it is available. Any ideas ?
Overall response times of  OO2.4 is quite good.

---

