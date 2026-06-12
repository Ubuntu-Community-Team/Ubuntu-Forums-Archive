---
title: "Exceptionally unimpressed with Ubuntu today"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by StueyB on 2006-02-24
Hi !

I *thought* everything was going ok, but in the last 24 hours I have had some exceptionally nasty bugs rear their heads. On both occasions I had to do a hard power down and when I rebooted my desktop was corrupted. 

Is it coincidental that the last 24 hours is when I began doing some serious hardcore work on it?  I dont know, but suffice to say I thought it was going ok, but it seems to crash a lot more frequently thank windows and nautilus cant make its mind up if its coming or going.

I have had to reboot into Windows to get the work done as it seems Ubuntu cant take the strain.

The thing is, im running a bog standard Dell Dimension with 1 GB RAM. As for tweaking the machine the only things I have done are:

install the 686 kernal
Change the wallpaper and colours
Use Automatix
Install a new standard type thing (no tweaking required)

So at the moment im very unimpressed. :(

---

### Post by skirkpatrick on 2006-02-24
I've been running Hoary since last spring and upgraded to Breezy when it came out and I've never had a problem.  Other than a couple of applications, I've not really installed anything that wasn't in the repositories.  I did use Automatix on my daughter's machine and promptly removed it as well as whatever it had done and gone with Easy Ubuntu instead as it had fewer problems.

---

### Post by Stealth on 2006-02-24
So...do you want us to help you impress you? Or are you just letting us know and not planning on giving any information to help you out...:rolleyes:

---

### Post by angkor on 2006-02-24
[QUOTE=StueyB]
Is it coincidental that the last 24 hours is when I began doing some serious hardcore work on it?  I dont know, but suffice to say I thought it was going ok, but it seems to crash a lot more frequently thank windows and nautilus cant make its mind up if its coming or going.
[/QUOTE]

Don't know if it's coincidental. What do you consider 'serious hardcore work'? Did you try and go back to the original kernel and see if it does the same? What causes the crashes...error messages?

Anyhow it's hard to tell what's causing it when you don't give any extra info.

---

### Post by Cousindaddy on 2006-02-24
Exactly what kind of a response were you hoping to solicit with your thread?

I'm sure there are people here who can help.

---

### Post by StueyB on 2006-02-24
Well I did consider filling a bug report but thing is, im not sure how many people use it the way I do. Basically whats been happening is that I have a remote ftp session mounted so I can copy and paste stuff over as im working on it. For the most part it is fine but when I try and copy some stuff across (no specific difference in files etc it locks up hard. The most still moves, but the keyboard stops responding completely, the apps in the background (Rythembox) still works, but not even CTRL + ALT + DEL will respond. My only way to get the box working again is to reboot it.

Upon rebooting it tells me my desktop rights are being ignored as they are not right.

---

### Post by Stormy Eyes on 2006-02-24
So, basically, it's a bug in Nautilus? File a bug report complaining about nautilus then. Also, you may want to try pressing CTRL+ALT+F1 to get to a console, logging in, and then using the following command:

```
killall -9 nautilus
```

---

