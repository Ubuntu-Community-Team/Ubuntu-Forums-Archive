---
title: "Firefox and Konqueror works - Opera no!!!"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by simplyman2006 on 2008-03-12
Hello! I am a new user of Ubuntu 7.10 and here is my first question to resolve one problem I have. I have Internet connected via D-Link router. As I installed Ubuntu FIrefox worked alright, so, I installed Opera but it does not want to show any web page or connect to Internet either, But when I open Firefox or Konqueror (who works with Intenet alrigth too), Opera connects to very same pages all well as what FIrefox and Konqueror show at the same time, but I cant go onto any other web page in Opera at all. Please Help me to find out a solution....

---
WIth love from Russia!!!

---

### Post by gobbles414 on 2008-03-12
simplyman2006,

Welcome to Ubuntu! How did you install Opera? The best way is to install Opera is probably by going *Applications => Add/Remove*. Then, go to the drop-down menu in the window and choose "All Available Applications" and search for Opera. If you've already installed this version of Opera, uninstall it and attempt to install Opera using the official Opera website (click [here]("http://www.opera.com/")).

Did this help?

---

### Post by simplyman2006 on 2008-03-12
> **gobbles414 said:**
> simplyman2006,

Did this help?

I uninstalled Opera and downloaded a file from Opera web page and installed it after. Still no results - Opera shows me a white screen....

---

### Post by gobbles414 on 2008-03-13
simplyman2006,

Interesting... I'll have to think about this some more tomorrow. In the meantime, have you consulted[ Opera's Online Help]("http://www.opera.com/support/online/") for answers?

---

### Post by simplyman2006 on 2008-03-13
I just wonder that let me tell one thing about Ubuntu and all the Gnone distros in general. I tried all the possible Linux distros and found out one interesting thing that all Gnome-based linuxes gave me no Internet at all, for the exception all KDE - Konqueror  let me surf the Internet but all the rest browsers refused, It looked like only intergrated (built-in, as I understood it) web browsers worked but the applications I was installing were way capricious... But recently I installed Ubuntu-based distro, it is called Runtu 2.0, Russian-made one. So my Ubuntu works so wonderful on my Dell 1505, even it is a Gnone-based distro, Internet on Firefox works all wonderful.

As they say Runtu is 90 per cent is of Ubuntu, so I doubt about differences Runtu might have in comparison with Ubuntu.

---

### Post by gobbles414 on 2008-03-13
> **simplyman2006 said:**
> I just wonder that let me tell one thing about Ubuntu and all the Gnone distros in general. I tried all the possible Linux distros and found out one interesting thing that all Gnome-based linuxes gave me no Internet at all, for the exception all KDE - Konqueror  let me surf the Internet but all the rest browsers refused, It looked like only intergrated (built-in, as I understood it) web browsers worked but the applications I was installing were way capricious... But recently I installed Ubuntu-based distro, it is called Runtu 2.0, Russian-made one. So my Ubuntu works so wonderful on my Dell 1505, even it is a Gnone-based distro, Internet on Firefox works all wonderful.

As they say Runtu is 90 per cent is of Ubuntu, so I doubt about differences Runtu might have in comparison with Ubuntu.

Am I understanding you correctly that no GNOME-based Linux will allow you to access the internet? That's really strange! Have you tried installing Ubuntu using the alternate CD?

---

### Post by Daveth on 2008-03-13
you haven't got a rule set on on your router have you- it sounds like things are being filtered out that are not Firefox or Konqueror, though why Opera picks the same pages is an odd one.

---

### Post by simplyman2006 on 2008-03-13
> **gobbles414 said:**
>  Have you tried installing Ubuntu using the alternate CD?

Yes! I tried and as I say all the GNOME-based Linuxes didn't give me an access to Internet....

> you haven't got a rule set on on your router have you- it sounds like things are being filtered out that are not Firefox or Konqueror, though why Opera picks the same pages is an odd one.

Please tell me what this rule is.,, I set up my router as wan settings PPPoE and all my password and login have been wtitten on [http://192.168.1.1](http://192.168.1.1) - this is what I did when I was Windows user. I changed nothing since...

---

### Post by Daveth on 2008-03-15
sounds like you have not then set a rule. Out of ideas here!

---

### Post by simplyman2006 on 2008-03-19
So! It looks like Ubuntu is not perfect as Windows is. Sad but it is a truth...

---

### Post by igknighted on 2008-03-20
> **simplyman2006 said:**
> So! It looks like Ubuntu is not perfect as Windows is. Sad but it is a truth...

Ah, blanket statements from a single anecdote... I love them.

---

### Post by p_quarles on 2008-03-20
This is strange, but it is not a widespread problem, so is not a valid basis for generalizations about Ubuntu.

Anyway, here are some steps you can take to isolate the problem. First, install the following network monitor:
```
sudo apt-get install tcpdump
```
Now, set it to log network traffic:
```
sudo tcpdump -i eth0 -n
```
Now, attempt to browse the web using Opera. Post whatever output comes up in the terminal from tcpdump.

---

