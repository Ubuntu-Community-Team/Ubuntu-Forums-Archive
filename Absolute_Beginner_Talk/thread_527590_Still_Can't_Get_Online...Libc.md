---
title: "Still Can't Get Online...Libc"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by metsfan47 on 2007-08-16
I posted on here 5-6 days ago because I had just installed Ubuntu and couldn't get online.  Unfortunately I still haven't found a solution to the issue.  I did a little research on my own, and found that the drivers that came with my motherboard had a folder called "linux drivers"  I started playing around with that, and actually found something called network drivers!  I'm hoping this is the issue, but I can't seem to install them.  When I try I get the following errors:

"No precompiled kernel interface was found to match your kernel; this mean sthat the installer will need to compile a new kernel interface."

I press "OK"

"Error: You do not appear to have libc header files installed on your system.  Please install your distributions libc development package."

"Error: Installation of network driver has failed.  Please see the [log] for details" 

What is libc development package?  Does anyone have any advice?  Thank you in advance, its been so long without the internet!  :)  

-Aaron

---

### Post by overdrank on 2007-08-16
> **metsfan47 said:**
> I posted on here 5-6 days ago because I had just installed Ubuntu and couldn't get online.  Unfortunately I still haven't found a solution to the issue.  I did a little research on my own, and found that the drivers that came with my motherboard had a folder called "linux drivers"  I started playing around with that, and actually found something called network drivers!  I'm hoping this is the issue, but I can't seem to install them.  When I try I get the following errors:

"No precompiled kernel interface was found to match your kernel; this mean sthat the installer will need to compile a new kernel interface."

I press "OK"

"Error: You do not appear to have libc header files installed on your system.  Please install your distributions libc development package."

"Error: Installation of network driver has failed.  Please see the [log] for details" 

What is libc development package?  Does anyone have any advice?  Thank you in advance, its been so long without the internet!  :)  

-Aaron

HI in you last thread you had a internet connection. May I ask why you are trying to install the drivers now? And what model is you nic card. You can find this by lspci command in the terminal.

---

### Post by metsfan47 on 2007-08-16
I'm sorry, but I was never able to get online.  It said I was connected to a wired connection, but it wasn't.  Pings went unreturned and my IP, Subnet, etc. were all 0.0.0.0 

I'm trying to install drivers to fix the problem.  I really want to get online with Ubuntu.  

Unfortunately I am at work right know and can't tell you my exact nic card.  Its intergrated into the motherboard, which is Asus A8N-VM.  I'll post when I get home though. (I can hook up an old Windows machine to post at home)

-Aaron

---

### Post by overdrank on 2007-08-16
> **metsfan47 said:**
> I'm sorry, but I was never able to get online.  It said I was connected to a wired connection, but it wasn't.  Pings went unreturned and my IP, Subnet, etc. were all 0.0.0.0 

I'm trying to install drivers to fix the problem.  I really want to get online with Ubuntu.  

Unfortunately I am at work right know and can't tell you my exact nic card.  Its intergrated into the motherboard, which is Asus A8N-VM.  I'll post when I get home though. (I can hook up an old Windows machine to post at home)

-Aaron

Ok if it as Asus states it is Realtek RTL8201CL then there seems to be some trouble with that nic card. As for the linux drivers you will have to compile them and hope they will be compatible. I know you don't have room for expansions but you may look a  different networking card. Good luck!

---

### Post by metsfan47 on 2007-08-16
I was thinking of trying a new NIC regardless, they seem to only run $7-$10 on tigerdirect or newegg.  

I'm afraid I don't understand what you mean by "compile" the drivers.  Sorry, I'm a n00b.  Could someone explain in a little more detail?  Thanks!

-Aaron

---

### Post by RomeReactor on 2007-08-16
Hi. I think installing **build-essential** installs the libc development package, so search for it in Synaptic (System->Administration-.Synaptic Package Manager); also search for **libc6-dev** and install it, just in case. Or to install from the terminal:
```
sudo apt-get install build-essential libc6-dev
```
Afterwards, try installing the drivers again.

---

### Post by Shazaam on 2007-08-16
metsfan...
Do you have an old dialup modem laying around? You could install that and sign up for some usually time limited FREE dialup with companies like juno.com or peoplepc (10 hours free per month). That way you could download what you need to get your nic card running.
If your company will let you, go to one of those sites to get your user login information, write it all down and take the info home with you. You do NOT need to download their software to use dialup with Linux.
Here is a good page that might help. Print it out...
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

