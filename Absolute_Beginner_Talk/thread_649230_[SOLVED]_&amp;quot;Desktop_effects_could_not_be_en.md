---
title: "[SOLVED] &amp;quot;Desktop effects could not be enabled&amp;quot;"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
I inserted 
```
compiz
```

and got this...

```
brandon@brandon-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


```

My lspci | grep VGA
```
brandon@brandon-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

```

Can someone tell me my desktop effects could not be enabled?

I have a ATI Radeon XPRESS 200M card

My laptop is a HP dv8000

:popcorn::popcorn::popcorn:

---

### Post by mivo on 2007-12-24
Did you install the restricted drivers for your card? Usually, they can be installed through *System -> Administration -> Restricted Drivers Manager* (in 7.10).

---

### Post by Kingsley on 2007-12-24
I have an ATI Radeon Xpress 200G card on my desktop also. Sorry, it's not supported. You could probably get Compiz to work through Xgl though. Look for a guide, but be advised that Xgl runs very slowly.

---

### Post by hilariousness16 on 2007-12-24
I enabled everything but still getting message, I;ll try to look for a guide but does anyone else have a suggestion?

---

### Post by tiachopvutru on 2007-12-24
install xgl by

```
sudo apt-get install xserver-xgl
```

But like Kingsley says, it runs pretty slowly. My other computer has an ATI Radeon Xpress 200G... using the latest driver which has AIGLX turns out to be better, but it's still far from working well enough. Beside, you have to install it manually...

---

### Post by staticvoid on 2007-12-24
...and shouldn't you run the comand compiz --replace and not just compiz?

---

### Post by hilariousness16 on 2007-12-24
tichop...u no whats wrong? :confused:

```
brandon@brandon-laptop:~$ sudo apt-get install xserver-xgl
[sudo] password for brandon:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```


:-?

---

### Post by hilariousness16 on 2007-12-24
:guitar:

---

### Post by spiderbatdad on 2007-12-24
something has update or package manger locked up. See if you can navigate to synaptic package manager and click on reload icon. then select "Broken" from the list on the left to see if anything shows up.

---

### Post by hilariousness16 on 2007-12-24
I added some new info...

spider, i reloaded, but i don't see any "broken"

---

### Post by hilariousness16 on 2007-12-24
I think XGL is already installed? maybe? idk? 
```

brandon@brandon-laptop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

