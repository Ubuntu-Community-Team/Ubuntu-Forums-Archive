---
title: "Python woes"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-03
I keep getting this error while trying to install packages in Synaptic:

E: python2.3-4suite: subprocess post-installation script returned error exit status 2

It pops up unexpectedly during install as a dialog box and asks if I want to skip it.  How can I fix this (and why is it happening?):confused:

---

### Post by amohanty on 2006-10-03
Open a terminal Applications->Accessories->Terminal

In there type:
**sudo apt-get install python2.3-4suite | tee install.log**
Enter _your_ password. 

If there is a problem post the contents of install.log.
NOTE: if you are unable to open install.log, in the terminal type:
**sudo chown your_username:your_username install.log**

HTH
AM

---

### Post by saintj0n on 2006-10-03
Ok...Here is the install.log

Reading package lists...
Building dependency tree...
python2.3-4suite is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.

Does this mean I have a bad install?

---

### Post by amohanty on 2006-10-03
> python2.3-4suite is already the newest version.

dude you are good to go... its already installed.

AM

---

### Post by saintj0n on 2006-10-06
Well..You are right. I guess I'm a little new to this stuff. It just seemed like it was errored out because of the cryptic message about it returning some code or something.

---

### Post by jordanmthomas on 2006-10-06
> 1 not fully installed or removed.

That is the problem
Try
```
sudo dpkg --configure -a
```
It's not python that is broken, it is something else.  This command will tell the package manager to configure what didn't get finished earlier.

---

### Post by saintj0n on 2006-10-07
Ok..I don't know a lot about dpkg except that it installs debs right? So if I was trying to get javacc up and running and it was throwing out errors aboout python2-3.4-suite and java-2sre, What would the usage be?

Maybe from any directory I can type sudo -su dpkg --configure -a java-2sre..

Is that right? It will only work on a debian package right?

---

### Post by jordanmthomas on 2006-10-07
It reconfigures debs that you have already tried to install, but that failed for some reason.  You don't need anything after the -a because that stands for 'all'  If you really wanted, I suppose you could switch the -a with the offending package, but it's not neccessary.

And yes, it will only work for debs, but if you are getting the errors above, that's what you're dealing with.

---

### Post by saintj0n on 2006-10-07
Ok I'm really confused... I was tryin to play a streamed video off of abc.com and it redirected me to the java upload page. I installed the java j2re deb package and I can now use Jbird netbeans and my python compiler works too. However, the streamed video still redirects me to the java page. So I tried to reinstall and I get a python error. No matter how many packages I use I get the same error. If it works, why the error?:confused:

---

### Post by amohanty on 2006-10-08
Fire up synaptic (System->Administration->Synaptic package manager), on the bottom left, click on custom, then on the panel on the left (just above it) click 'Broken' and post the list of packages that show up on the right.

HTH
AM

---

