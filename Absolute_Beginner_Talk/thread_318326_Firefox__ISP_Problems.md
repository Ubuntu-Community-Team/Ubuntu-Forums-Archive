---
title: "Firefox / ISP Problems"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Kevin Funnell on 2006-12-13
Good Day & Thanks in advance,

I had a small problem & had to re-install Ubuntu, I reformated The swap file area and Ubuntu main HD.

Then I configured the Internet connection via PPPConfig, all seemed OK able to log-in to my Mail Program and  ISP  my Home Page but unable to go anywhere else.  Pop-Up Message "Server not Found".

Also have problems in updating Synaptic Package Manager - Al  Icon Legens show green (box) - Installed and unable to update, probable inked to fault above.

Any HELP in correcting these problems would be appreciated.

Thanks,
Old Kevin] (*,)

Thanks for the replies so far followed the suggested correction still having problems with the ISP connection 

Modem: Dial-Up Hayes External Accura 56K + FAX

Computer P4, Ubunto install fro Live Cd.

will off the net for about 3 hours,

Thanks,
Old kevin](*,)

---

### Post by ardvark71 on 2006-12-13
> **Kevin Funnell said:**
> 
I had a small problem & had to re-install Ubuntu

Nice play on words:mrgreen: 

For your internet connection, are you connecting via Dial-up or DSL, Cable, etc.?

With Synaptic, when you get your connection fully up and running you will need to:

1. Bring up the main program.
2. On the upper part of the Synaptic window, click "Settings."
3. Click Repositories.
4. Click "Add" on the upper right corner.
5. Make sure all four boxes are checked, including "Universe" and "Multiverse."
6. Click "ok"
7. Click "ok" again.

Best Regards...

:KS

---

### Post by furiousV on 2006-12-13
To sort out Firefox:

Launch it, and go to **about:config** in the address bar.

Filter out **ipv6** and set **network.dns.disableIPv6** to **True**

That should get websites loading

---

### Post by Kevin Funnell on 2006-12-13
I am on Dial-Up (old copper wire), usually reliable.
Old Kevin

---

### Post by ardvark71 on 2006-12-13
> **Kevin Funnell said:**
> I am on Dial-Up (old copper wire), usually reliable.
Old Kevin

Will your system ping out to various sites? What is the brand and model of the modem you're using?

Best Regards...

---

### Post by Kevin Funnell on 2006-12-14
#1.  System Ping - not sure about that as I don't know how to do that.

#2 Modem External Accura 56K  FAX.

Will not be able to answer any more question for anothe couple of Hours - Thunderstorms are in the area.   Hopefully will be back on the net (windows) later on (abot 3 hours)

Old Kevin:-k

---

### Post by ardvark71 on 2006-12-15
> **Kevin Funnell said:**
> #1.  System Ping - not sure about that as I don't know how to do that.

Just open a terminal and type in:

ping (whatever) .com

The (whatever) can be your choice of any given web site.

Best regards...

---

### Post by Kevin Funnell on 2006-12-15
Thanks for the Info.

From where it never rains but when it does it pours

---

### Post by Kevin Funnell on 2006-12-15
Another question or two,

In "[COLOR="Blue"]furiousV[/COLOR]" Post #3 it was stated to: "Filter out IPv6" - How Do I do this?  I have set the "Network.dns.disableIPv6" to **True**

Thanks,
Old Kevin

---

### Post by Kevin Funnell on 2006-12-17
Good Day All,  

[COLOR="Red"]I NEED HELP IN SETTING-UP MY EXTERNAL MODEM SO I CAN CONNECT TO THE WEB AND UPDATED PACKAGES.[/COLOR]

I still having problems with my connection to the Internet and therfore are unable to use eith of the update managers or Download Package Information.

I am able to log-in to my Mail program where I can Receive & send mail I can also log-into my ISP /Home page but can not connect to any other Web page/Site. Which makes it impossible to use Ubuntu 

I used PPPconfig to configure the modem and that is wher I probable have made some minor errors in my selection of options available.

My System P4 Intel computer
Modem: External -  Hayes Accura 56K + FAX

I Can ping my ISP/Home page but no othe valid WEB sites.

If any one has a working copy of PPPconfig could you send it to me via this Forum or e-mail.

I want to use Ubuntu/Linux but without a working Internet connection in is impossible and I have to go back to Windows to connect to theis Forum or other sites.

Old Kevin

---

### Post by chrisfay on 2006-12-17
Whats in your resolv.conf file?

```
sudo vi /etc/resolv.conf
```

---

### Post by Kevin Funnell on 2006-12-20
Good Day Chrisfay,
In anothe one of my post I got some help, I tried the suggestions  and got it working, then found had a small problem when trying to use Update Manager so I re-installed Ubunto from Live Cd.  This time have no problems in setting-up the Internet connection with pppconfig and now merrly updating by selective updates all well that ends well.
Thanks, Old Kevin

---

### Post by LookTJ on 2006-12-20
are there any nameservers(Of course DNS) set in /etc/resolv.conf

here's an example of mine(resolv.conf)

```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

to look at yours

do:

```
gksudo gedit /etc/resolv.conf
```

then set the DNS servers provided by your ISP.

take a look at disabling [IPv6 tutorial](http://ubuntuforums.org/showthread.php?t=202838) for the whole system

Hope that helps. :D

EDIT: Sorry I didn't see above post. Is it resolved yet?

---

