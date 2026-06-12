---
title: "Recomend a good Firewall"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2006-09-03
This is my first post to Ubuntu forum. My best regards to the moderators and seniors present here. I am a linux lover, from India...fully frustrated using Windows with its lot of problems mainly caused due to virus and also many other ways, and using linux for 2 years without any problem. I am neither from computer industry or have any formal education with computer. That is why I am not particular in terminology and also very much dependent on your help. Hope to enjoy your company.

Anyway, may anybody please recomend a good firewall for my newly installed ubuntu 6.06 LTS, which will give me flexibility to allow or deny individual IP addresses?

---

### Post by Klaidas on 2006-09-03
The firewall is installe dby default, it's iptables.
If you're asking for a GUI of iptables...> sudo apt-get install firestarter

---

### Post by Linux Lover on 2006-09-03
Installed firestarter but it is giving some problem. While I am launching the application it is showing an error, "Failed to start Firewall. The device eth0 is not ready. Please check your network device settings and make sure your internet connection is active."

My internet connectin is presently active but still it is giving the error. Even if I manually press the start button too. What is the problem?

I am using ADSL connection through my only network card (eth0). It is purely a desktop system.

---

### Post by David Corrales on 2006-09-03
You could also try guarddog.

---

### Post by OffHand on 2006-09-03
Try reinstalling it with:

```
sudo apt-get remove firestarter && sudo apt-get install firestarter
```

---

### Post by John.Michael.Kane on 2006-09-03
Provided you have a lowend spare machine. You could always build a linux firewall router using one of the many firewall distro's.

---

### Post by Linux Lover on 2006-09-03
Hello everybody,

The problem gone with the reinstallation of firestarter. Thank you for your help.

My best regards to all of you for your attention to my thread.

---

### Post by Linux Lover on 2006-09-03
> **SD-Plissken said:**
> Provided you have a lowend spare machine. You could always build a linux firewall router using one of the many firewall distro's.

Hey friend,
Though I have a spare low end machine, in spite of that my machine is purely a desktop machine which contains no valuable data.
So, your suggestion is no doubt of a great suggestion but it is of no need indeed for a machine like mine. Anyway, you remind me the smoothwall software once again with your post.
Anyway, I appreciate your advice as I wish to test such a firewall in future.

---

### Post by Linux Lover on 2006-09-03
> **Klaidas said:**
> The firewall is installe dby default, it's iptables.
If you're asking for a GUI of iptables...

[OFF TOPIC] : I visited your photo gallary. It is very nice. You should really proud of your own eye.
:-)

---

