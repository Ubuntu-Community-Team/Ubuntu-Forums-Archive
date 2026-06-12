---
title: "Help, close to giving up on vmware"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-15
I've installed vmware server - downloaded from vmware. I had it working. But under xgl it wouldn't do fullscreen (complaint: not suitable screen setting from host).
I then installed vmware player it could do the fullscreen but after a restart of the player none (plyer or server) would start. 
When I start from console I get:```
$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```Running **/usr/bin/vmware-config.pl.** does not solve the problem.
I think a complete uninstall would help the problem - but it will never install. No matter how I try to uninstall I end up with that same answer. That is, even after a **remove completely** in synaptics I still get that answer when I run the **vmware** command.
I tried something suggested here:
[http://www.ubuntuforums.org/showthread.php?t=180624&highlight=vmware+share](http://www.ubuntuforums.org/showthread.php?t=180624&highlight=vmware+share)
But got this:
```
$ sudo apt-get remove vmware*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vmware

```So I how do I uninstall completely or how do get vmware working?

---

### Post by jd65pl on 2007-01-15
To uninstall vmware server to the following command

```
/usr/bin/vmware-uninstall.pl
```

---

### Post by fsando on 2007-01-15
Thanks - I tried that too with same result.
I just reinstalled from the untarred folder - it works now. So I will have to live with it the way it is right now- until I learn more about how it works (hope it continues to work).
Next hurdle is getting access to files across ubuntu/windows without breaking anything.

---

### Post by fsando on 2007-01-15
Update: 
vmware (sticking to its plan) stopped working after ubuntu reboot. Same result as above. ](*,) ](*,) 
Is there any way to completely remove vmware?

---

### Post by m4xr8d on 2007-01-15
did you start the vmware service after reboot?

```
sudo /etc/init.d/vmware start
```

---

### Post by fsando on 2007-01-15
> **m4xr8d said:**
> did you start the vmware service after reboot?

```
sudo /etc/init.d/vmware start
```

Actually not I didn't know that

I did a file-search for 'vmware' (including hidden files) and changed the name of everything that seemed safe - and sure enough now when I installed again it believed it was a clean install - but now there is no network connection. 

```
$ sudo /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed

```
I feel I'm met with one hard problem after, the other, the learning curve is a bit steep. Reminds me, though, of win 3.1 back then, much of the same experience and frustration.  I'm not sure I understand those errors except they are about network.
Anyway I've downloaded parallels trial version. I'm going to see if it's worth 50$
Btw some issues installing parallels are solved here:
[[COLOR="Blue"]_http://http://www.ubuntuforums.org/showthread.php?t=319498&highlight=parallels_[/COLOR]]("http://http://www.ubuntuforums.org/showthread.php?t=319498&highlight=parallels")

EDIT: just read on digg ([http://digg.com](http://digg.com)) about virtualbox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) - an open source virtualizer - they have an ubuntu package - installed like a a charm - going to try it out in the next days. Well - the packages are not open source but they have an open source version - as I far as I understand it

---

### Post by ghandi69_ on 2007-02-10
Definitely.. I'm a total noob, and I was able to get Virtual Box running vista (the copy school gave me... NO i didn't spend money on it...) in just one all nighters attempt!!!

Virtual Box gets my recommendation.

---

