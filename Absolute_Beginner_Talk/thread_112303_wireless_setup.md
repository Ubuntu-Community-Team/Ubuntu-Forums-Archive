---
title: "wireless setup"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-01-04
Hi all,
   I have been browsing around for a little while now and looked for some info on how to setup my wireless card. Although I have come across some info, I do not fully understand what has been said. If anyway one is able to help me with this problem, please do.
   I installed kubuntu yesterday. It seems that  I have to set up my wireless connection manually. I am using a minitar mnw2bpci card. The only only drivers that come with the cd target windows and redhat. I was not to sure that the redhat driver would be appropriate to use (even if it was, I would not know how to install it). 
   As I do not have any other connection to the net other than my wireless card I cannot use apt-get (which I have read, is used for installing and getting software of the net). What I have done at the moment is go to the [http://www.minitar.com/index.php?maincat=download]("http://www.minitar.com/index.php?maincat=download")
and downloaded the rt2400 linux 1.1.0 source. I have burnt this onto a cd. This is where I am stuck. Could someone please advise on the next steps/steps.

thaks for you time and help

---

### Post by bluefrog on 2006-01-04
you could use ndiswrapper (on the cd) to use the windows driver and see if it works.

sudo ndiswrapper -i /path/to/driver.inf  (driver.sys should be in the same folder to avoid possible problems)

sudo ndiswrapper -m  (to load the driver on boot)

sudo modprobe ndiswrapper (to load the driver now)

go to system>administratio0n>networking, your card should be there now, you need to configure it and activate it.

james

---

### Post by psylvester on 2006-01-04
sylvester@ubuntu:~$ sudo ndiswrapper -i /path/to/driver.inf
Password:
sudo: ndiswrapper: command not found
sylvester@ubuntu:~$

I have installed ubuntu, im using Xp as well. When i logged in, the OS (ubuntu) doesnt dectect Wireless. What I need to do ? can you please explain ?

Thanks.
p sylvester

---

### Post by Titus A Duxass on 2006-01-04
@psylvester
You need to install ndiswrapper through apt and then repeat what you have done.

---

### Post by mwanafunzi on 2006-01-04
thanks for that.. will try that out..then get back to you. Curiously, is there anything that I can do with the source code that I found on the minitar site.

---

### Post by AlexDeGruven on 2006-01-04
[QUOTE=mwanafunzi]is there anything that I can do with the source code that I found on the minitar site.[/QUOTE]


A lot of it depends on the quality of the code they provided.

Most of the companies will cludge together a perfunctory driver for an old version of redhat so that they can say they provide a linux driver. 99% of these drivers are crap and you end up much better off using the ndiswrapper solution.

---

### Post by nandasunu on 2006-01-07
I am also trying to set up wireless to work with kubuntu. I used gnome before and had it all working. ndiswrapper doesn't seem to work for me in kubuntu (did a complete reinstall) and I can seem to apt-get it:

```
nanda@ubuntu:~$ sudo apt-get install ndiswrapper
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ndiswrapper
```

any clues?

---

### Post by psylvester on 2006-01-16
Hi friends,
I've been trying to install Wireless for pretty long time, If some one can help me, I will really appreciate it.
This is my MSN ID: [email]prasanthsylvester@hotmail.com[/email]
yahoo Id : [email]framedrelay@yahoo.com[/email]
(if anyone is free can talk to me, I will be online most of the time)

ok this is what Im doing ...............

root@ubuntu:~ # sudo apt-get install ndiswrapper
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:~ #

System has dectected my wireless card. I can see it in device manager.
its INPROCOMM IPN 2220 Wireless Lan Adapter.

root@ubuntu:~ # uname -r
2.6.10-5-386
(my kernel)

If some one can help me, I will really appreciate.
Thanks
P Sylvester.
Bangalore, India.
+91-988-660-0666

---

### Post by psylvester on 2006-01-16
I Downloaded, ndiswrapper 1.1, untard it.. But need help in installing it..

sylvester@ubuntu:~/Desktop/ndiswrapper-0.11$ ls

AUTHORS  ChangeLog  debian  driver  INSTALL  Makefile  ndiswrapper.8  ndiswrapper.spec.in  README  utils  version

can some one tell me what to do next ?

Thanks,
Sylvester.

---

