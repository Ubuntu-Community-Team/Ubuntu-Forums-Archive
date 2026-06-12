---
title: "maximum number of o.s??"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-03-09
I installed ubuntu gutsy gibbon 7.10 on my laptop..i also have vista as second o.s. .My lap config 2gb ram,120 gb harddisk,1.6 ghz processor.Now I wanna install open suse ..Is it safe to install 3 os  on a lap???:)

I have an inbulit webcam  on my lap 2mega pixels..but i have a problem with it  on ubuntu..When i opened camorama webcam viewer it is saying 
"error:cannot connect to video device /dev/video0 .plz check connection"..
but when i opened through kopette messenger it is working fine....plz tell how to start a webcam....:confused:

One more doubt,I downloaded many packages through synaptic package manager..Now my friend has just installed ubuntu on his lap due to its extraordinary advantages over windows..Should he download all the packages  from synaptic??Or is there a way for him to get them from my lap(some sort of synchronising)..We do have lan connection(in our college)...Is there any software that can make this possible???plz help us!!!:(

---

### Post by munkyeetr on 2008-03-09
> **RAJESHKSV said:**
> I installed ubuntu gutsy gibbon 7.10 on my laptop..i also have vista as second o.s. .My lap config 2gb ram,120 gb harddisk,1.6 ghz processor.Now I wanna install open suse ..Is it safe to install 3 os  on a lap???:)


Yes.

---

### Post by kelean on 2008-03-09
Here is a link from another Linux site.  .  I know a bit extreme, but very interesting read.  I hope it helps.  Kelean.

[http://www.justlinux.com/forum/showthread.php?t=147959&highlight=dual+boot]("http://www.justlinux.com/forum/showthread.php?t=147959&highlight=dual+boot")

---

### Post by szymon_g on 2008-03-09
> **RAJESHKSV said:**
> I installed ubuntu gutsy gibbon 7.10 on my laptop..i also have vista as second o.s. .My lap config 2gb ram,120 gb harddisk,1.6 ghz processor.Now I wanna install open suse ..Is it safe to install 3 os  on a lap???:)

I have an inbulit webcam  on my lap 2mega pixels..but i have a problem with it  on ubuntu..When i opened camorama webcam viewer it is saying 
"error:cannot connect to video device /dev/video0 .plz check connection"..
but when i opened through kopette messenger it is working fine....plz tell how to start a webcam....:confused:

One more doubt,I downloaded many packages through synaptic package manager..Now my friend has just installed ubuntu on his lap due to its extraordinary advantages over windows..Should he download all the packages  from synaptic??Or is there a way for him to get them from my lap(some sort of synchronising)..We do have lan connection(in our college)...Is there any software that can make this possible???plz help us!!!:(

1. if you wont delete any previous partitions (windows' and ubuntu's)- it will be safe.
if you have (on ubuntu) /home on seperated partition - you can use it on other distro (but there may be some problems due to various configuration of programs, of their different versions etc)


2. hm... its hard to say a solution... but does file /dev/video0 exist? maybe kopette uses other device... (like /dev/video)? if yes, you can do a symbolic link to it (man ln ;p)

3. i'm not sure about synaptic's behaviour (i run aptitude by hand), but, by default, before installation of program and its dependencies, it stores them in

/var/cache/apt 

directory. if you never cleaned it (e.g. by sudo apt-get clean) - there should be a possiblility to do a local repo which can be transported (on dvd, for example) to yours friends computer.

/////////// 
btw, there is a programm called apt-cd. check it out :P

---

