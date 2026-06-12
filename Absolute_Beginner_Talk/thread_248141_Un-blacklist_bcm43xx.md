---
title: "Un-blacklist bcm43xx"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by tilai on 2006-08-31
I lost the thread where I was told to blacklist bcm43xx then do ndiswrapper. Now my laptop won't detect the wifi card and there's no more eth1. how do i undo the bcm43xx blacklist step?

---

### Post by TFX360 on 2006-08-31
> **tilai said:**
> I lost the thread where I was told to blacklist bcm43xx then do ndiswrapper. Now my laptop won't detect the wifi card and there's no more eth1. how do i undo the bcm43xx blacklist step?

Open a terminal


```
sudo nano /etc/modprobe.d/blacklist
```


remove the line you want. Probably at the bottom.

```
crtl-x
```
```
Enter
```
```
Enter
```

To save the file...


But wouldn't you like to try to look if ndiswrapper is installed propperly?


```
sudo ndiswrapper -l
```


Should say **driver present, hardware present**

---

### Post by Metacarpal on 2006-08-31
[This might prove useful to you.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")

---

### Post by friedokra on 2006-08-31
this same thing just happened to me. blacklisting it used to work, but then it started making my eth1 card disappear!!!

---

### Post by TFX360 on 2006-08-31
> **friedokra said:**
> this same thing just happened to me. blacklisting it used to work, but then it started making my eth1 card disappear!!!

The same counts for you in my previous post. What does ndiswrapper -l tell you?

---

### Post by tilai on 2006-08-31
Thanks TFX, I removed it from the blacklist after following the steps. I did the sudo ndiswrapper -l command and got 
> Installed ndis drivers:
bcmwl5  invalid driver!


Does it mean there is something wrong with the ndiswrapper installation?

---

### Post by TFX360 on 2006-08-31
> **tilai said:**
> Thanks TFX, I removed it from the blacklist after following the steps. I did the sudo ndiswrapper -l command and got 


Does it mean there is something wrong with the ndiswrapper installation?

Yep, wrong driver in the inf/sys. What card do you have and more important what version does it say on the card...

---

### Post by tilai on 2006-08-31
Card? I guess you mean the Wifi card. It's a Broadcom 4306. Can't rememer the version. Let me check it on the other OS then come back again

---

### Post by TFX360 on 2006-08-31
See ya in a bit then.

---

### Post by tilai on 2006-08-31
> What card do you have and more important what version does it say on the card.

It is a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03). After rebooting back onto Drapper I was extremely surprised to see that not only the Wifi card is detected, but I also somehow have  wifi connection.:D (You can't see it but I just danced around the table.. Hehe)

Hope it keeps working next time I switch the laptop on.

For the Ndiswrapper should I be doing something?

---

### Post by TFX360 on 2006-08-31
> **tilai said:**
> It is a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03). After rebooting back onto Drapper I was extremely surprised to see that not only the Wifi card is detected, but I also somehow have  wifi connection.:D (You can't see it but I just danced around the table.. Hehe)

Hope it keeps working next time I switch the laptop on.

For the Ndiswrapper should I be doing something?

Is it still running?

```
sudo ndiswrapper -l
```

---

### Post by tilai on 2006-08-31
> **TFX360 said:**
> Is it still running?

```
sudo ndiswrapper -l
```

Yes, the wifi is fine now.\\:D/

Re sudo ndiswrapper still having the error message
> Installed ndis drivers:
bcmwl5 invalid driver!

It's 8.25am here, I am going to hit the sack and check up your next step recommendations. Thanks TFX.

---

### Post by TFX360 on 2006-08-31
> **tilai said:**
> Yes, the wifi is fine now.\\:D/

Re sudo ndiswrapper still having the error message


It's 8.25am here, I am going to hit the sack and check up your next step recommendations. Thanks TFX.

Woooo, it's 2.34 AM here. I'm going to

```
sudo shutdown -h now
```

here too. 


Kewl, you from China?


Diggit!

---

### Post by tilai on 2006-09-01
> Kewl, you from China?
I am foreigner there looking for a job. In my free, boring time I am exploring Ubuntu. ;)

So if anyone needs a half-decent employee who is fluent in English and French, just pm me. (Yes, completely out of subject and unashamed to advertise myself:tongue: )

---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> I am foreigner there looking for a job. In my free, boring time I am exploring Ubuntu. ;)

So if anyone needs a half-decent employee who is fluent in English and French, just pm me. (Yes, completely out of subject and unashamed to advertise myself:tongue: )

Lol, advertise yourself! :D

---

### Post by tilai on 2006-09-01
Re the 
> Installed ndis drivers:
bcmwl5 invalid driver!
What should I do, if anything, about it?

---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> Re the 

What should I do, if anything, about it?

Well, apparantly the native Ubuntu bmc43xx driver works for you. So you can remove the ndiswrapper driver by doing:


```
ndiswrapper -e drivername.inf
```

Do a -l agian to get the drivername if you can't remember.


Remove the module

```
sudo rmmod ndiswrapper
```


Remove the module from startup

```
sudo nano /etc/modules
```

Remove ndiswrapper

```
crtl+x
```
```
Enter
```
```
Enter
```

To save the file.

That should do it.

---

### Post by TFX360 on 2006-09-01
Is it a laptop you are working on? Does the connecton come back after you suspended/hiberbnated?

---

### Post by tilai on 2006-09-01
> **TFX360 said:**
> 

```
ndiswrapper -e drivername.inf
```

Do a -l agian to get the drivername if you can't remember.

Ok, I am still on the first part.
I thought the drivername would be bcmwl5.inf since the only detail I got from the command #ndiswrapper -l is the error msg bcmwl5  invalid driver!

However, typing #ndiswrapper -e bcmwl5.inf resulted in
> rl@Laptop:~$ ndiswrapper -e bcmwl5.inf
Driver bcmwl5.inf is not installed.Use -l to list installed drivers

---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> Ok, I am still on the first part.
I thought the drivername would be bcmwl5.inf since the only detail I got from the command #ndiswrapper -l is the error msg bcmwl5  invalid driver!

However, typing #ndiswrapper -e bcmwl5.inf resulted in

Maybe my error, maybe the .inf should not be included!

---

### Post by tilai on 2006-09-01
Without the .inf the message changes to
> rl@Laptop:~$ ndiswrapper -e bcmwl5
Can't remove directory /etc/ndiswrapper/bcmwl5 (Permission denied) at /usr/sbin/ndiswrapper line 166


---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> Without the .inf the message changes to

Did you sudo the command? That's probably it!

---

### Post by tilai on 2006-09-01
> **TFX360 said:**
> Did you sudo the command? That's probably it!

I'm bad. Right now I'm just blindly following instructions. Yes, after adding the sudo command, it was ok. But the next stop gave
> rl@Laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules:confused:

---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> I'm bad. Right now I'm just blindly following instructions. Yes, after adding the sudo command, it was ok. But the next stop gave
:confused:

Then you never installed ndiswrapper properly. Doesn't matter it doesn't exist so we don't need to remove it.

---

### Post by tilai on 2006-09-01
> **TFX360 said:**
> Then you never installed ndiswrapper properly. Doesn't matter it doesn't exist so we don't need to remove it.

Thanks for your help over the last couple of days TFX360.:D

---

### Post by TFX360 on 2006-09-01
> **tilai said:**
> Thanks for your help over the last couple of days TFX360.:D

Your welcome. Good luck there in China. I hope you find a suiting job soon.

---

