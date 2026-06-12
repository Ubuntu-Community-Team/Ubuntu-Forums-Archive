---
title: "need Ksnapshot handbook"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Robshaus on 2007-07-01
Having played with various distros since 1999, I have converted my one workstation office to Ubuntu Fiesty. Screen shots of data is a daily practice for which I use Ksnapshot with some success.  "help" returns "could not launch the KDE help center: could not find service'khelpcenter'. Add-remove programs does not offer  Ksnapshot handbook. How do I obtain or install it ?

---

### Post by steveneddy on 2007-07-01
In terminal type

```
man ksnapshot
```

"man" means **manual**

Do this for any application that you need some extra help with.

What is your problem? Ksnapshot seems pretty easy to use to me.

---

### Post by Robshaus on 2007-07-01
Tnx for your reply. Ksnapshot program window has no minimize button and and imposes itself in snapshots which include most of desktop. How do I initiate a new snapshot without including the ksnapshot window ? I often can move the ksnapshot window partly off the desktop and get by, but this is not a good solution.

---

### Post by steveneddy on 2007-07-01
Try

```
sudo apt-get install khelpcenter
```

#-o

---

### Post by Robshaus on 2007-07-01
Tnx Steveneddy. I am off to  "try sudo apt-get install khelpcenter"

---

### Post by jrev on 2007-07-01
You got a quicker snapshot practice here :

Just put your mouse cursor on the window you want to record and clic ALT + Printscreen

You'll get your picture and register it where you want...:p

That's the full handbook to me

[[img]http://www.enregistrersous.com/images/vignettes_images/145037539920070701182806.png[/img]](http://www.enregistrersous.com/images/3/145037539920070701182806.html)

---

### Post by steveneddy on 2007-07-01
In retrospect, I use kscreenshot and I don't have the problem of the GUI for ksnapshot showing up in any screenshots.

---

### Post by Robshaus on 2007-07-01
sudo apt-get install khelpcenter  worked magnifico. Exactly what I wanted.  Ksnapshot/region which allows me to select a specific portion of an htm or html frame provides me with a better solution than printscreen which has to be then cropped. 
Tnx again. I am off and running.

---

### Post by steveneddy on 2007-07-01
I'm glad I could help. I guess i helped.

Anyway - glad you got what you wanted.

---

