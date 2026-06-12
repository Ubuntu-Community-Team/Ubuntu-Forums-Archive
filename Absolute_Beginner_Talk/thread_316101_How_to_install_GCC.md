---
title: "How to install GCC"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by cyberbuff on 2006-12-10
Dear Frendz,
I am new to ubuntu. I tried to configure ADSL using rp-pppoe-3.5. But it sed that c compiler doesnt work. Now I downloaded GCC 4.0. Someone please tell me how to install them. It has a deb extension. 
Help much appreciated
Regards.

---

### Post by Perfect Storm on 2006-12-10
Put your Ubuntu CD in the CD-drive

```
sudo aptitude install build-essential
```
(if you're on edgy).

Otherwise on Dapper and up , doubleclick.

By command
```
cd /where/the/packa/is
sudo dpkg -i XXXXXXXXXX.deb
```

---

### Post by dancro on 2006-12-10
How about using Synaptic Package Manager?  

Click System/Administration/Synaptic Package Manager to get started.  
Then select "All" on the left side and click the Search button; enter "gcc" to search for the package, select "gcc-4.0" it and mark for installation.  Then Apply to install it.  Any dependencies are identified and included.  

Hope this helps.
Dan

---

### Post by cyberbuff on 2006-12-10
> **dancro said:**
> How about using Synaptic Package Manager?  

Click System/Administration/Synaptic Package Manager to get started.  
Then select "All" on the left side and click the Search button; enter "gcc" to search for the package, select "gcc-4.0" it and mark for installation.  Then Apply to install it.  Any dependencies are identified and included.  

Hope this helps.
Dan
Thnks for your help. but it sed dependencies not satisfied.
Any clue?:confused:

---

### Post by sas on 2006-12-10
You need to install the build-essential package rather than the gcc-4.0 package.

---

### Post by cyberbuff on 2006-12-10
well I installed gcc-4.1_4.1.1-13ubuntu5_i386.deb. But when I tried to configure the rp-pppoe-3.5 package, it gave me the following error message: 
```
loading cache ./config.cache
checking for gcc...gcc
**checking whether the c compiler (gcc) works...no**
configure: error: installation or configuration problem: C compiler cannot create executables. 
```
Seems like the C compiler still not working. What shuold I do?

---

### Post by sas on 2006-12-10
Install the build-essential package, that will install various gcc related packages.

---

### Post by cyberbuff on 2006-12-10
> **sas said:**
> Install the build-essential package, that will install various gcc related packages.
is the stuff in the ubuntu cd?

---

### Post by Ozitraveller on 2006-12-10
No

Try this :

How to install Basic Compilers (build-essential)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29)

---

### Post by cyberbuff on 2006-12-10
well I'll try that. Thank you so much for your time. As a matter of fact, I am typing this in Xp. It's really very tiresome job to go to Ubuntu and check it. I'll post further advances (or retreats :mrgreen: )
Regards

---

### Post by cyberbuff on 2006-12-11
I installed Build Essential according to Artificial Intllgence.

Now this is a bit off-topic. When I am trying to setup adsl connection using rp-pppoe-3.5, it goes on well. when run adsl start, it says link is up. But i cant access the net. running "adsl status" gives me this:
```
can't read pppoe PID file /var/run/pppoe.conf-adsl.pppoe.pid.pppoe
```As a matter of fact there is no such file there. 
i should mention one thing: tried the command "pppoeconf" before. Is it why it's not working now? 
Regards:-k

---

### Post by Perfect Storm on 2006-12-11
I think you'll be better off if you start a new thread with a title that reflect your new problem, so the members who knows this stuff can spot it.

---

### Post by cyberbuff on 2006-12-11
ok please check [http://www.ubuntuforums.org/showthread.php?p=1871650#post1871650](http://www.ubuntuforums.org/showthread.php?p=1871650#post1871650). thanks to friends for helping me.

---

