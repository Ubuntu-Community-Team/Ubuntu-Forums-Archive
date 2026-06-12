---
title: "I broke Apt - Please Help!"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by AnthonyRoberson on 2007-05-16
I just installed Kubuntu Feisty Fawn and I seem to have broken Add/Remove Programs.  When I try to open it, I get the following message:

The APT Database could not be opened!  This may be caused by incorrect APT configuration...

When I go to the Konsole and type apt-get upgrade, I get the following errors:

E: Unable to open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (var/lib/package/) are you root?

This all started when I tried to install Automatix2.  I am a MAJOR LINUX NEWB.  Please, please help me.  Thanks so much!

---

### Post by Martin on 2007-05-16
If Automatix is still running it will have locked the repository lists, this is normal and is a good thing.
Make sure all of your package management software is off. Then try again

---

### Post by taurus on 2007-05-16
Can you post your /etc/apt/sources.list?  You probably screwed up your repos when you added Automatix2.

```
cat /etc/apt/sources.list
```
Otherwise, run

```
**sudo** apt-get update
**sudo** apt-get upgrade
```

---

### Post by ThePolemistis on 2007-05-16
> **AnthonyRoberson said:**
> I just installed Kubuntu Feisty Fawn and I seem to have broken Add/Remove Programs.  When I try to open it, I get the following message:

The APT Database could not be opened!  This may be caused by incorrect APT configuration...

When I go to the Konsole and type apt-get upgrade, I get the following errors:

E: Unable to open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (var/lib/package/) are you root?

This all started when I tried to install Automatix2.  I am a MAJOR LINUX NEWB.  Please, please help me.  Thanks so much!

are you riunning as root?
u need to do:

```
sudo apt-get upgrade
```

---

### Post by AnthonyRoberson on 2007-05-16
[QUOTE=taurus;2668645]Can you post your /etc/apt/sources.list?  You probably screwed up your repos when you added Automatix2.

```
cat /etc/apt/sources.list
```
Otherwise, run

....

When I do cat, I get a message that says "No such file or directory".  Also, how do I tell if I am running as root?

Thanks...

---

### Post by taurus on 2007-05-16
What's the output of this command from a terminal?

```
ls -la /etc/apt
```

---

### Post by mstlyevil on 2007-05-17
> **AnthonyRoberson said:**
> I just installed Kubuntu Feisty Fawn and I seem to have broken Add/Remove Programs.  When I try to open it, I get the following message:

The APT Database could not be opened!  This may be caused by incorrect APT configuration...

When I go to the Konsole and type apt-get upgrade, I get the following errors:

E: Unable to open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory (var/lib/package/) are you root?

This all started when I tried to install Automatix2.  I am a MAJOR LINUX NEWB.  Please, please help me.  Thanks so much!

I suspect adept may not have added a dependencie during the installation of AX. Try this command first and see if it works first.

```
sudo apt-get -f install
``` 

If that does not work then please come to the [Automatix forums]("http://www.getautomatix.com/forum/") and we will get this fixed for you.

---

