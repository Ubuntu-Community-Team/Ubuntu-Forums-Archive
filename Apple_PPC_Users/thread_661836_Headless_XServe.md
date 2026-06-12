---
title: "Headless XServe"
date: 2008-01-08
forum: Apple PPC Users
---

### Post by breaking on 2008-01-08
Hey All!

I have a headless XServe that I am trying to install Ubuntu on. I currently have the XServe in target disk mode and the install seems to be going well. I am curious does Ubuntu by default have SSH installed? If not I might have to get that squared away... 

My question is if anyone has ever gotten this type of setup working. I am kind of skeptical about it.

Thanks! 

Joe

---

### Post by stalker145 on 2008-01-08
> **breaking said:**
> Hey All!

I have a headless XServe that I am trying to install Ubuntu on. I currently have the XServe in target disk mode and the install seems to be going well. I am curious does Ubuntu by default have SSH installed? If not I might have to get that squared away... 

My question is if anyone has ever gotten this type of setup working. I am kind of skeptical about it.

Thanks! 

Joe

I can't say anything about your intended setup, but to answer your initial question: no, Ubuntu does not come with SSH installed. It's an easy fix, though ```
sudo aptitude install openssh-server
```

---

### Post by breaking on 2008-01-08
Sure it is easy if you have a Terminal to the machine.... Since mine is headless then I need almost everything installed prior to rebooting..

I am considering installing 7.10 on my G5 desktop.. creating a ISO of that and installing that ISO onto my XServe.

---

### Post by stalker145 on 2008-01-08
> **breaking said:**
> Sure it is easy if you have a Terminal to the machine.... Since mine is headless then I need almost everything installed prior to rebooting..

I am considering installing 7.10 on my G5 desktop.. creating a ISO of that and installing that ISO onto my XServe.

That would probably work. I heard recently of [Remastersys]("http://www.remastersys.klikit.org/"), though I haven't tried it yet. That might be the answer for you.

---

