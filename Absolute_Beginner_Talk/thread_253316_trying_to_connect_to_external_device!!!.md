---
title: "trying to connect to external device!!!"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-09-08
Hi I only recently installed Ubuntu and I dont know much about linux so if u have any suggestions please go through it step by step. 


I have manually installed minicom becuase I want to connect my fingerprint board (which is called SM01) to the PC and the manual for the fingerprint board needs me to set up the terminal first.

This is what the manual says:

[COLOR="Red"]Start by setting up a terminal (using Minicom, for example) with the following characteristics.:

1) Connection speed :115,200 bps
2) 8 data bits
3) No parity
4) 1 stop bit
5) No hardware control
6) No software control

When the Sm01 is switched ON, the boot sequence can be visualised and the following prompt appears at the end:

**SM01 login:**
You can login as "root" without a password

**[root@SM01 /root]$**

At this stage you control a shell under the SM01.[/COLOR]


However when I switched the board ON the boot sequence does not appear and I do not see any prompt. The manual does not say that I should type any commands to get this boot sequence. If u think I need to use a command please let me know. 

Anyway I also think that it might be a minicom related problem:
This is how I configured the serial port.


A - Serial Device : /dev/ttyS1 &#9474;
B - Lockfile Location : /var/lock &#9474;
C - Callin Program : &#9474;
D - Callout Program : &#9474;
E - Bps/Par/Bits : 115200 8N1 &#9474;
F - Hardware Flow Control : No &#9474;
G - Software Flow Control : No


What does "8N1" mean???? because I am not sure that my settings for the number of parity bits, stop bits and data bits were saved.


Also Im sure how to test if this port is being recognised and how to save my settings for the serial port....

Also do I need to leave "B" empty ?????

please help me!!

---

### Post by monktbd on 2006-09-08
> **cinderella said:**
> 
E - Bps/Par/Bits : 115200 8N1 &#9474;


Seems to me like **8** bits, **n**o parity and **1** stop like you need it.

i am not sure about the lock file location but i would guess it is fine like it is.

---

### Post by cinderella on 2006-09-08
> **monktbd said:**
> Seems to me like **8** bits, **n**o parity and **1** stop like you need it.

i am not sure about the lock file location but i would guess it is fine like it is.

I thought so too but the boot sequence and the prompt for the "SM01" still does not appear.

---

### Post by monktbd on 2006-09-08
not much i can do i think.

the device is properly connected to the correct serial port?
is there a setting in minicom that needs to be set for incoming connections since you shouldnt do anything?

---

### Post by cinderella on 2006-09-08
> **monktbd said:**
> not much i can do i think.

the device is properly connected to the correct serial port?
is there a setting in minicom that needs to be set for incoming connections since you shouldnt do anything?

not sure! but i will read the manual based on mnicom more thoroughly!! thanks

---

