---
title: "Wicd problem"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2007-07-30
Hi everyone,

I'm having a bit of a peculiar problem with wicd on a wireless connection at home. I need wicd so I can easily get a static ip from my router, and it worked fine yesterday. I was able to browse the internet, ssh anywhere, etc. Then I went to work and connected to the wireless network there, where it also worked (albeit with a dynamically assigned address). This was all as planned, since I downloaded wicd so I could have different preferences for different networks--static ip at home, dynamic ip at work. When I connected up at home tonight, I was able to access some websites like google and Caltech's main page (but not department-specific pages, such as pma.caltech.edu), but I wasn't able to go to myriad other pages, among them farmers.com and harvard.edu. When I reconnected to my network with a dynamically assigned address, I was able to use the internet normally. That's how I'm making this post. Any ideas would be appreciated--I'm stumped!

---

### Post by hnaamyilkemku on 2007-07-30
Some notes which might be helpful: between last night and tonight I've installed the openssh server and a few windows games (SC and BW). I don't think I've made any other large-scale changes.

---

### Post by ugm6hr on 2007-07-30
> Any ideas would be appreciated--I'm stumped!

How unusual... Must be some kind of firewall issue with static IP.  Perhaps worth running Firestarter to see if it is blocking anything when you try and connect with a static IP.  Maybe you need to manually open the http port for Firefox?  Although I can't see why a static IP would change that.  :-k

---

