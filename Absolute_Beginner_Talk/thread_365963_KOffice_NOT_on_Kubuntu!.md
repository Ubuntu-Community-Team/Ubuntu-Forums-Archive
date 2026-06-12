---
title: "KOffice NOT on Kubuntu?!"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Tadpole on 2007-02-20
I just tried Kubuntu for the first time and, amazingly, was not able to find KOffice. Go to the Office section of the start menu and you'll find OpenOffice, but not KDE's own flagship office suite. I can't even find it in Adept.

Am I missing something? How could it not be there?

Thank you.

---

### Post by Maestro23 on 2007-02-20
> **Tadpole said:**
> I just tried Kubuntu for the first time and, amazingly, was not able to find KOffice. Go to the Office section of the start menu and you'll find OpenOffice, but not KDE's own flagship office suite. I can't even find it in Adept.

Am I missing something? How could it not be there?

Thank you.

Running Xubuntu myself and just did a 

[COLOR="Red"]apt-cache search Koffice[/COLOR] and found it in the repositories.

---

### Post by tdwester on 2007-02-20
You can add the repositores from here [http://kubuntu.org/announcements/koffice-161.php](http://kubuntu.org/announcements/koffice-161.php)

---

### Post by Tadpole on 2007-02-20
> **Maestro23 said:**
> Just did a 

[COLOR="Red"]apt-cache search Koffice[/COLOR] and found it in the repositories.

Okay, so it's there but it's not in Adept. I still don't understand why it doesn't just come installed, or at least come in Adept, but thank you anyway.

By the way, I'm new to the linux command line. Should I type "sudo apt-get install koffice"?

---

### Post by Tadpole on 2007-02-20
> **tdwester said:**
> You can add the repositores from here [http://kubuntu.org/announcements/koffice-161.php](http://kubuntu.org/announcements/koffice-161.php)

Wait, so it *isn't* included in Kubuntu? That would be even worse. I don't mean to sound bitter, I'm just confused why such a big and important program is so ignored.

---

### Post by Maestro23 on 2007-02-20
> **Tadpole said:**
> Okay, so it's there but it's not in Adept. I still don't understand why it doesn't just come installed, or at least come in Adept, but thank you anyway.

By the way, I'm new to the linux command line. Should I type "sudo apt-get install koffice"?

Probably have to enable extra repositories like the one guy mentioned.  After that(If you want to do command line):

> sudo aptitude update

sudo aptitude install koffice



You can use apt-get or aptitude.  The differences are explained here: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Good luck.

---

### Post by tdwester on 2007-02-20
That one I can not answer but it is easy to add.

---

### Post by rasbach on 2007-02-20
Having both office suite programs installed by default would be redundant and take up a lot of unnecessary space.  One of the things I disliked about SuSe (and I'm guessing that's where you came from) was that it installed both by default.  With every install of Suse, one of the first things I would do is remove the redundant programs that I didn't want.

Ubuntu prides itself in a faster install time, quicker load time, and small footprint on your system.  If KOffice came with the install, you would have had to burn another CD for the .iso.

Most people prefer to use OpenOffice, so Ubuntu installs this by default.  You are entitled to either switch to Koffice as you seem fit, this is the beauty of open source.

IMHO- Open Office is much better than Koffice- but that's just me.

---

### Post by Tadpole on 2007-02-20
> **rasbach said:**
> Ubuntu prides itself in a faster install time, quicker load time, and small footprint on your system.  If KOffice came with the install, you would have had to burn another CD for the .iso.Okay this makes sense - I just figured that KOffice should be preferred over OOo on KDE since it's built for it and integrated with it.

Thank you all for the responses!

---

### Post by Jucato on 2007-02-20
During the time when Kubuntu started, KOffice was not as mature as it is now. OpenOffice was a leader, specially when it comes to supporting MS Office formats. (Even until now, I'm having issues with opening MS Office documents in KOffice, but that's another issue entirely). So it was decided to put OpenOffice.org instead.

You'll be happy to know that Kubuntu has already considered slowly switching to KOffice. They will be shipping Kexi by default in Feisty as a start. They're still watching the situation, waiting for a release that they can really rely on. Most probably KOffice 2.0 (by the time KDE 4.0 arrives).

---

