---
title: "How to install kde on ubuntu system with kubuntu cd"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by skew on 2006-09-01
The subject line pretty well says it all, but i'll clarify just the same.

I have ubuntu already installed on my pc and I have a kubuntu cd. I want to install kde in tandem with gnome from the cd and not over my painfully slow dialup account.  Is that at all possible and if so how? :confused: 

Thanks

---

### Post by skew on 2006-09-01
No takers huh? :( 

  Is it because I asked a really stupid question or because it's not possible to install kde that way?  :?

---

### Post by aysiu on 2006-09-01
It's possibly only if you have the **Alternate CD**: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

If you have only the **Desktop CD**, it's not possible, and you'll need to use your dial-up connection.

---

### Post by skew on 2006-09-01
:-x  Dang!...That's what I was afraid of.

Thanks for writing back.

S

---

### Post by Marsolin on 2006-09-01
Try putting the CD in you drive and running the following from the command line.

sudo apt-cdrom add
sudo apt-get update

These two lines first add your CD as a repository and then updates the repository listing. Now you should be able to install kde.

sudo apt-get install kdebase kdm

I'm assuming you can already boot to Gnome and have the X window system running.

---

### Post by aysiu on 2006-09-01
> **skew said:**
> No takers huh? :( 

  Is it because I asked a really stupid question or because it's not possible to install kde that way?  :? It's because you waited only 45 minutes. You should generally wait at least 24 hours before bumping your thread.

> **skew said:**
> :-x  Dang!...That's what I was afraid of.

Thanks for writing back.

S If you are going to use dial-up, download the Alternate CD via BitTorrent (this is more likely to give you a non-corrupt disk image than a straight download) and then burn it. Then add it from the CD. The bonus of this is that you'll also have an Alternate CD handy in case you ever want to add KDE to another computer with dial-up only.

> **Marsolin said:**
> Try putting the CD in you drive and running the following from the command line.

sudo apt-cdrom add
sudo apt-get update

These two lines first add your CD as a repository and then updates the repository listing. Now you should be able to install kde.

sudo apt-get install kdebase kdm

I'm assuming you can already boot to Gnome and have the X window system running. As I stated earlier, this works for only the Alternate CD.

---

### Post by bozo8787 on 2006-10-16
Hi I know the question here is installing kde on ubuntu with the kubundu cd. So I ask the reverse, can one install kde on ubuntu without additional cd and instead the more 'simpler online repositories via synaptic or adept'?

---

### Post by aysiu on 2006-10-16
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) will help you do it without the CD

---

