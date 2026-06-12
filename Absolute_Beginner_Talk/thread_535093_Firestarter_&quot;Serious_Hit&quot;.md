---
title: "Firestarter &quot;Serious Hit&quot;"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by tepidarium on 2007-08-26
Hi,

I wa using Ubuntu and I noticed that my hard drive light began to blink alot even though my machine was mostly idle - this usually doesn't happen. 

I turned on Firestarter - and after 10 seconds of being on it registered a "serious" hit -and then my hard drive light stopped blinking.  Was my computer compromised?  How serious is  a "serious hit"   - what, if anything should I do.

Thanks for any advice.

---

### Post by southernman on 2007-08-26
Are you behind a router?

I looked myself but don't see/know which logs to look in. At any rate, browse though /var/log and see if you have a firewall log or some other sort of log that can tell you something more.

By default Ubuntu is very secure. Unless you install a lot of 3rd party apps (even then) your probably ok.

See what you can find in the logs though.

---

### Post by keyboard_soldier on 2007-08-26
I've never gotten a "Serious Hit" from Firestarter, so I have no idea what that means...But, if your hard drive stopped acting out of line, I guess that's a good thing!

---

### Post by some_random_noob on 2007-08-26
Don't worry about it. If something was attacking you and you got a warning, then firestarter would have stopped it. Like others have said: Ubuntu is secure unless you start installing heaps of crap. Security just isn't an issue with Ubuntu. If you're really worried, install nmap  and portscan your own computer 

```

sudo apt-get install nmap
nmap -r 127.0.0.1
```

... anything open? Use "netstat -lntp" and see what programs are keeping those ports open, then kill those programs if you don't need them. Internet security is a joke - the only danger is from software you expose yourself to.

---

### Post by slymi2005 on 2007-08-26
i downloaded the nmap and i'm not sure what it did, wut is it supposed to do?

---

### Post by tepidarium on 2007-08-26
> **southernman said:**
> Are you behind a router?

I looked myself but don't see/know which logs to look in. At any rate, browse though /var/log and see if you have a firewall log or some other sort of log that can tell you something more.

By default Ubuntu is very secure. Unless you install a lot of 3rd party apps (even then) your probably ok.

See what you can find in the logs though.

Hi,

I'm accessing the internet from my laptop with WPA2. 

The only thing I downloaded which gives me pause is that I installed Beryl 2.0 without adding the gpg key. So I got a message asking that the packages could not be verified"

Could this be a problem?

---

### Post by tepidarium on 2007-08-26
> **some_random_noob said:**
> Don't worry about it. If something was attacking you and you got a warning, then firestarter would have stopped it. Like others have said: Ubuntu is secure unless you start installing heaps of crap. Security just isn't an issue with Ubuntu. If you're really worried, install nmap  and portscan your own computer 

```

sudo apt-get install nmap
nmap -r 127.0.0.1
```

... anything open? Use "netstat -lntp" and see what programs are keeping those ports open, then kill those programs if you don't need them. Internet security is a joke - the only danger is from software you expose yourself to.

I ran nmap and it gave me the following:

Not shown: 1695 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
6001/tcp open  X11:1

---

### Post by tepidarium on 2007-08-26
Firestarter indicates that the source for my "serious hit" appears to be the ip address of my linksys wireless router.  Could that mean that someone got into my network.  I'm using wpa2 security...

---

### Post by some_random_noob on 2007-08-27
> **tepidarium said:**
> I ran nmap and it gave me the following:

Not shown: 1695 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
6001/tcp open  X11:1
Cool, it worked. That "port 631" is a printer sharing thingy. I closed that on my computer, merely by googling for an answer. The less open ports the better. I don't know what port 6001 is. Try doing "netstat -lntp" and it will tell you what program is using it.

---

