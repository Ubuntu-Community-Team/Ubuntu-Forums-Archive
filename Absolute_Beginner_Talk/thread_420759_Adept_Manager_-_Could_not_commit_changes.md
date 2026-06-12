---
title: "Adept Manager - Could not commit changes"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Blade1384 on 2007-04-23
Whenever I try to install programs through adept i get this error:

There was an error commiting changes.  Possibly there was a problem downloading some packages or the commit would break packages.

Also, whenever I try to install with apt-get I receive this error:

E: Sub-process /usr/bin/dpkg returned an error code (2)

Help!

**Update**

I get the same message when I try to update.  So I cannot download any updates for Kubuntu.

---

### Post by falm on 2007-04-27
Hello,
i had the same problem, after

sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
  -> read the output, you will have to answer a few questions
sudo dpkg --configure --pending

everything is working again

---

### Post by venik212 on 2007-04-27
Pretty upsetting to get it fouled up after less than 12 hours after installation of Kubuntu... ;-(

---

### Post by Blade1384 on 2007-04-30
Hey it's working now.  Thanks for the help, and yes, it is pretty upsetting to have adept stop working less than 12 hours after the installation.

---

### Post by pseudo_nz on 2007-08-08
> **falm said:**
> Hello,
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
  -> read the output, you will have to answer a few questions
sudo dpkg --configure --pending



I tried installing the cupswrapper from brothers website and got the same result - I've run the coding that was listed above, but instead of questions, this is the output:

dpkg: error processing dcp130ccupswrapper (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 dcp130ccupswrapper


I've deleted the original deb file, as it's obviously no good, but I'm pretty sure nothing was actually installed, so I'm not sure where to go to fix this.  I've got a few hundred mb of updates to run after reinstalling dapper, so will leave it until the system is up to date before trying again (on dialup, worse luck), only now I can't get *any* updates!

Anyone with some wisdom to share?

---

### Post by robinbillings on 2007-11-15
While installing a random application (3dchess) I clicked on the Details button to see what the error was and noticed that the libqt3-mt, which apparently calls kdesudo, appeared to be the hangup.  I ran sudo apt-get install libqt3-mt and prompted it to Install /I/ over the configuration file already there.  Solved the problem.

Robin Billings

---

### Post by lemming552 on 2007-11-17
falm's commands solved it for me. Thanks!

---

### Post by wolfger on 2007-11-20
> **falm said:**
> sudo dpkg --configure -a
  -> read the output, you will have to answer a few questions

No questions, just errors:
```
Setting up xcwcp (2.3-6) ...
dpkg: error processing xcwcp (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 xcwcp
```

---

### Post by garich on 2007-11-23
Same error here, BUT right after fresh installing Kubuntu 7.10. Other errors are - found an update of the system (Gutsy Gibbon), however i thought i already installed 7.10 :)

p.p. anyway - the programs looks they've installed normally, just don't want to see the errors.

p.p.p The advice of falm looks like solved the problem.

---

### Post by ddrake on 2007-12-11
Hello

 I have installed kubuntu gutsy on an acer aspire 4710N (core2duo) laptop and did
face a number of problems (wireless, webcam, headphones, builtin microphone etc)
and including this! 

I have tried FALM's suggestions and the last two gave the following
> dpkg --configure -a
Setting up tomcat5.5 (5.5.25-1ubuntu1) ...
 * no JDK found - please set JAVA_HOME
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomcat5.5-admin:
 tomcat5.5-admin depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-admin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-webapps
 tomcat5.5-admin
root@ananda:/var/lib/dpkg# dpkg --configure --pending
Setting up tomcat5.5 (5.5.25-1ubuntu1) ...
 * no JDK found - please set JAVA_HOME
invoke-rc.d: initscript tomcat5.5, action "start" failed.
dpkg: error processing tomcat5.5 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat5.5-webapps:
 tomcat5.5-webapps depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-webapps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomcat5.5-admin:
 tomcat5.5-admin depends on tomcat5.5 (>= 5.5.25-1ubuntu1); however:
  Package tomcat5.5 is not configured yet.
dpkg: error processing tomcat5.5-admin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tomcat5.5
 tomcat5.5-webapps
 tomcat5.5-admin


The reason I am putting it here is that there seems to be some (KDE?) bug
that created this in the first place. What did I do?
a) casually browsing the services table (K->system settings ->advanced(tab)->system services, I found that TOMCAT has been started and is running. I was not using anything related to it so I stopped it and ticked off the button to start at boot time.
b) I wanted to reinstall knetworkmanager since the icon on the panel, when clicked on gave no data (all empty). And why did I touch this utility? My ipw3945 wireless DOES NOT work....  I used adept manager to remove and then reinstall this KNetworkManager.
c) The trouble started then - adept manager - would refuse to commit with the error message reported by others here.
d) when I tried restarting the TOMCAT in 'system services' of system settings, I got the  error message : first set the JAVA_HOME for TOMCAT ...

I could not do anything further!

Since then I always had the adept error message persist for whatever I installed
and worst - I was not sure I installed fully or correctly . This reallyPUTS off people.

Hope the advanced gutsy users can file an appropriate bug report
if they find the above repeatable.  

Thanks falm
DD

PS: latest info:  I thought Falm's suggestions would make a difference! No --- it did not help me. The adept manager's error message remains.

PPS :  SOLVED my problem.

 I fixed the tomcat JAVA_HOME by editing the file /etc/default/tomcat5.5   and adding a line pointing to where I had installed the jdlk.
And then adept manager started working without the above problems. Thanks

---

