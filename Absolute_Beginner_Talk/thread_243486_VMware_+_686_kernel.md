---
title: "VMware + 686 kernel"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-08-25
Hello, 
I've been playing around with VMware some time ago, and now I decided to do it again. However, when I was trying to t run it, I got > vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl

Hmm, that's strange, it worked before. Oh well, so I'm reconfiguring it.
It's all nice untill it comes to a question > What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

I press enter, but uh oh - > The path "/usr/src/linux/include" is not an existing directory.

Well, I've searches some google, and found that it shoud be /usr/src/linux-headers-`uname-r`. So I go to /usr/src, but there are only these directories: > klaidas@klaidas-desktop:/usr/src$ ls
linux-headers-2.6.15-25  linux-headers-2.6.15-25-386  rpm


I try both linux-headers but they give an error.
Then it comes to my head that I have installed a 686 kernel, maybe that's why it doesn't work?

Should I install the old kernel again or is there a way to do it with 686? Or am I in a totally wrong direction? :-k

---

### Post by Iarwain ben-adar on 2006-08-25
Hi,
did you try to install the headers?

```
sudo apt-get install kernel-headers-2.6.15-25-686
```

IF your kernel version is 2.6.15-25-686 ;)


Iarwain

---

### Post by Klaidas on 2006-08-25
I thought I had to install headers, but didn't really know what to looks for ](*,) 
the package name was not found, but I'm now dowsnloading linux-headers-2.6.15-26-686, I'll post if ti works 

Thanks

---

### Post by Klaidas on 2006-08-25
yup, it now works. Thanks for help :)

---

### Post by Iarwain ben-adar on 2006-08-25
No problem :D

Glad to 've helped you 


Iarwain

---

### Post by XPuntu on 2006-09-05
Hmm. For some reason my terminal is telling me that it can't find the package. I did a sudo aptitude update and then cut and paste the command you gave. What did I miss?

Thanks.

---

### Post by Iarwain ben-adar on 2006-09-06
Hi,

What kernel are you running? 
```
uname -r
```


Iarwain

---

### Post by XPuntu on 2006-09-06
Oops. 

2.6.15-26-686

But still, why doesn't the apt-get command work? It should still find the package no?

I tried sudo apt-get install kernel-headers-2.6.15-26-686 but it couldn't find that package either. ](*,) 

thx

Ahh. Just saw that I should install linux-headers.....

---

### Post by Iarwain ben-adar on 2006-09-07
Hi,
so you sorted the problem out? :D


Iarwain

---

### Post by XPuntu on 2006-09-07
You betcha. XP back up now. Thanks!

---

