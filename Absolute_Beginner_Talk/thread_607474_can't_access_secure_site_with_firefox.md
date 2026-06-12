---
title: "can't access secure site with firefox"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by jantanjo on 2007-11-09
Just installed Ubuntu 7.10 on a Plll and firefox can't access https sites. 

I'm on a network with IPCop as a firewall, all other computers can access secure sites.

all help is appreciated.

---

### Post by jfinkels on 2007-11-09
Are you sure it's not just a specific site? What kind of error message are you getting?

Open firefox from the terminal:```
firefox
``` and see if you get any error message when you access a secure site.

---

### Post by jantanjo on 2007-11-09
hi jfinkels

I've tried a number of sites and the response is usually "Server not found". I even tried your "Restricted Formats " link with the same results. (Who could resist clicking on something that warns of a restricted format?)

As far as error messages, where would I find them, there's nothing in terminal.

How can I tell if firefox has 128 bit abilities?

---

### Post by jfinkels on 2007-11-11
Firefox should be able to access https sites just fine, I don't know how to help you beyond this, especially if you don't have any error output in the terminal. Make sure you have the site name typed in correctly, first. Second, there are loads of web browsers available for Linux, try epiphany, the default GNOME browser. Install it by typing```
sudo aptitude install epiphany-browser
```or try kazehakase```
sudo aptitude install kazehakase
```

---

### Post by jantanjo on 2007-11-12
Sorry jfinkels for wasting your time, 

I feel like such a retard. I checked "Use this proxy server for all protocols" and everything worked as I am used to. Now if only I could walk and chew gum at the same time.

jan

---

### Post by jfinkels on 2007-11-12
No worries, everyone makes mistakes. That's why we like working together, here, we can get through problems more quickly.

---

### Post by Bobrm2 on 2008-01-21
I have tried to log in to [https://www.telepc.net/homebankofar/;](https://www.telepc.net/homebankofar/;) using Ubuntu 7.10, then Foxfire/Epiphany, and just this morning Kamakazse. With no success. Have not made adjustment to, the security settings within the last two browsers. 
    Java is common, of course, to these three browsers, but possibly dissimilar to the Windows machine(?).  New install with regard to  java, but I wonder if that is set up correctly.  

 I can log on to the site, via Windows XP pro. 

Has anyone a notion of how to proceed, or where to look for advice? 

Thanks

---

