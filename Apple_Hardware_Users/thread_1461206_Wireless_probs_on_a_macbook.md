---
title: "Wireless probs on a macbook"
date: 2010-04-23
forum: Apple Hardware Users
---

### Post by thedoctor81877 on 2010-04-23
I am helping a friend, who has just switched over to ubuntu on a Mac. I do not currently know what type of macbook he has, but currently the wireless chip is not working. I am able to get connected through the ethernet port though. I do not know enough about macbooks to figure out how to find out which wireless chip he has. Any help would be appreciated.

-the Doctor

---

### Post by mmalone21 on 2010-04-23
I am not 100% sure this is the only issue or if it will fix it since I have not installed ubuntu on a mac in a year or so, and have owned an Apple product in 13 years. Well anyway in the synaptic package manage their is an airport package that has helped me to get others Apple wireless working in the past.

---

### Post by thedoctor81877 on 2010-04-23
I am not seeing an airport package in synaptic...

---

### Post by jaco223 on 2010-04-23
> **thedoctor81877 said:**
> I am not seeing an airport package in synaptic...

Have you checked to see if the wireless driver is installed?
System>Administration>Hardware Drivers

You probably need to activate the wireless driver.
After activating the driver, restart the computer
log back in, click on network manger in the panel,
you should see wireless networks there.
Jaco

---

### Post by thedoctor81877 on 2010-04-23
That fixed the prob. Thanks a bunch.

---

### Post by jaco223 on 2010-04-23
> **thedoctor81877 said:**
> That fixed the prob. Thanks a bunch.

No problem, glad you got it working!

Jaco

---

### Post by pmhauge on 2010-05-01
I'm having a similar problem, but the solution that worked for the OP does not work for me. I'm able to activate the driver from the Live CD, but after installing 10.04 on my Macbook, wireless does not work at all. System > Administration > Hardware Drivers simply tells me that no proprietary drivers are in use by this system. I'm also given an error that "downloading package indexes failed. Please check your network status. Most drivers will not be available." 

Hard wiring to ethernet also does not work. 

Any additional fixes?

---

### Post by linuxopjemac on 2010-05-02
cannot you hook it up to a cable connection and update the repository and try again?

```
sudo apt-get update
sudo apt-get upgrade
```

then do your hardware driver trick in administration..

---

