---
title: "Limewire installation problems"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-11-30
During the installation of Limewire for Ubuntu, the installer froze while installing the Java application. I tried and tried again,however, a dialog box comes up and tells me "Only one software management tool is allowed to run at the same time". I only have one running. I attempted this 4 times at least only to see the same thing happen again. The package installer that I used was the default one, (Gdebi package installer). Any suggestions as to what I should do now to start the installation over?

---

### Post by kamitsukai on 2007-11-30
restart your pc

---

### Post by fmbugdadi on 2007-11-30
I already tried restarting several times, still get the same message...

---

### Post by kamitsukai on 2007-11-30
o right well that sorted it out for me last time....y not try frostwire? lol im sure somone else will be able o help

---

### Post by SunnyRabbiera on 2007-11-30
hmm...
well give another reboot a shot and see what happens, but I have a feeling I know what your problem is...
if you have this issue after rebooting then I will know for sure.

---

### Post by fmbugdadi on 2007-11-30
Yes, I rebooted again, and the same thing happens...
also, when I run synaptic package manager, i get an error now that says, "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

---

### Post by Duck2006 on 2007-11-30
In the terminal run

sudo dpkg- --configure -a

---

### Post by SunnyRabbiera on 2007-11-30
ah ha, just as I thought!
I had this issue once but I have to remember the fix I had for it...
give me a minute...
Duck2006 might have beat me to it though...
its been ages but I did have this issue once and I was able to get it fixed
edit: try apt-get update if the suggestion Duck2006 didnt work, that is what fixed my issue
if you open the system monitor and see if there is "apt" stuff running this also might be an issue, if apt is hanging then i definately know your problem

---

### Post by Duck2006 on 2007-11-30
Sorry this is what it should been.

sudo dpkg --configure -a

---

### Post by SunnyRabbiera on 2007-11-30
Yeh one of them works.
Like i said I had an issue like this myself, sometimes apt hangs when you install things and sometimes the apt sources file is locked :shock:

---

### Post by fmbugdadi on 2007-11-30
ok, after running that command, I can run synaptic now, however, after synaptic loads, a dialog box appers that says, "You have 1 broken package on your system!

Use the "Broken" filter to locate it."

any suggestions, as to how to fix this before I try installing limewire again? Is there a better way to install limewire?

---

### Post by SunnyRabbiera on 2007-11-30
Okay this is no big issue
In synaptic you click on "custom filters" and then click on "broken"
now there will be a red box next to the broken package, just click it and select "remove package"
Now here is hoping the broken package is just limewire, sometimes installing limewire from the limewire page can cause a issue like this.
what you might need instead is frostwire, frostwire is just like limewire... in fact it is almost exact.

by what means did you install limewire with might I ask?

---

### Post by fmbugdadi on 2007-11-30
when I clicked to download limewire, I had the option to "save to disk", or to "open with Gdebi package install", I chose to open with Gdebi package install, and it started installing the package, then it froze when installing java

---

### Post by fmbugdadi on 2007-11-30
Ok, now i went into synaptec, clicked on custom filter, then broken, then proceeded to remove java5 bin, then while removing i got this error "java5 bin in very inconsistent state, and i clicked on details, and received this error in terminal"dpkg: error while removing Java5 bin (purge) package is in very bad inconsistent state, you should reinstall it before attempting a removal. errors were encountered while processing. sun java 5 bin 
E: subprocess usr/bin/dpkg returned an error code (1)
a package failed to install, trying to recover...

---

### Post by SunnyRabbiera on 2007-11-30
ahh
well yes limewire needs a version that is not in the ubuntu repositories by default.
this is an easy fix though (sorta), after fixing your broken package I want you to do the following:
first you go to the java website:
[here]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com")

after that download the self extracting file (dont bother with the RPM, its not worth your time)
after that is done downloading go to where you downloaded your file (if all your files download to the desktop though, please take the file to your home folder or something, just open up your home directory and drag and drop.)
after this you will need to open up synaptic again
now what you will need is something called nautilus-open-terminal, as this will allow you to open a terminal inside your desired directory (for some odd reason this is not enabled in ubuntu, it honestly should be)
now after installing it you will have to restart your session... there is no real easy way to do this bit I am afraid.
now after restart go to whatever directory you put the java installer in and under "file" in the menu go to "open in terminal"
after this type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks 
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)
then go to [this site]("http://www.frostwire.com/")

and download frostwire
frostwire is less temperamental then limewire sometimes so installing it with gedebi should be smoother.
the hardest bit of this is installing java, as there is no real decent installer for it under linux and the ones that are out there really dont work in cases like this.
I have had this issue and even though it is a bit complicated when installing java its all smooth sailing from there

---

### Post by SunnyRabbiera on 2007-11-30
> **fmbugdadi said:**
> Ok, now i went into synaptec, clicked on custom filter, then broken, then proceeded to remove java5 bin, then while removing i got this error "java5 bin in very inconsistent state, and i clicked on details, and received this error in terminal"dpkg: error while removing Java5 bin (purge) package is in very bad inconsistent state, you should reinstall it before attempting a removal. errors were encountered while processing. sun java 5 bin 
E: subprocess usr/bin/dpkg returned an error code (1)
a package failed to install, trying to recover...

ah so it is java that is the issue...
maybe you can try to install it the way i suggested above, like i said installing java can be testy.

---

### Post by fmbugdadi on 2007-11-30
BY golly it worked!!! thanks for all of your help.. I am just trying to get frostwire to connect now....

---

### Post by fmbugdadi on 2007-11-30
O.k, now that I got that accomplished, is there anything that i need to change on my router, to get frostwire to connect?

---

### Post by SunnyRabbiera on 2007-11-30
well connection can be a testy issue on frostwire, and there is little you can do if you are using a router...
do you have any firewalls installed or enabled in linux? this can be a factor

---

### Post by fmbugdadi on 2007-11-30
ok, I have it all working now... thanks a million!!!

---

### Post by SunnyRabbiera on 2007-11-30
no problem, we aim to please.
just keep in mind that sometimes packages you download from the net can have issues with your system, but otherwise ubuntu is good at what it does.

---

### Post by Parvo on 2007-12-01
Actually I think the problem is this. When I install things I always hit the “terminal'' so I can see what's happening. When my installation froze I looked at the terminal and saw that it wanted me to accept the license terms. when I did that it installed the rest of the way without problems. Hope this helps.

---

