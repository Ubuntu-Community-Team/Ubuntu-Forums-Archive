---
title: "Cant lock list directory."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-04-08
I'm trying to install Gnome from Kubuntu and when I give the install Ubuntu Desktop code in terminal and tell it yes I want to install all the stuff it tells me ```
Couldn't lock list directory..are you root?

```. So I type ```
Sudo -i
``` to become root and try it again, and I get the same message. Whats wrong?

---

### Post by taurus on 2007-04-08
What command did you run from a terminal?  Did you remember to put sudo in front of it?

---

### Post by Hieronymus on 2007-04-08
```

sudo apt-get install ubuntu-desktop

```

This should work, is this what you used yourself?

Jeroen

---

### Post by Narcoleptic_Insomniac on 2007-04-08
I ran ```
Sude aptitude install ubuntu-desktop gdm
``` because thats what someone else told me to use in order to install Gnome.

Sorry for slow responses. I'm not used to getting quick replies on this board.

---

### Post by Hieronymus on 2007-04-08
> **Narcoleptic_Insomniac said:**
> I ran ```
Sude aptitude install ubuntu-desktop gdm
``` because thats what someone else told me to use in order to install Gnome.

Sorry for slow responses. I'm not used to getting quick replies on this board.

assuming that sude is an error in typing this should work normally. But what happens when you use the code I typed, with gdm also added in your case?
And if that doesn't work try to do 
```

su
apt-get install ubuntu-desktop gdm

```

Jeroen

---

### Post by taurus on 2007-04-08
> **Narcoleptic_Insomniac said:**
> I ran ```
Sude aptitude install ubuntu-desktop gdm
``` because thats what someone else told me to use in order to install Gnome.

Sorry for slow responses. I'm not used to getting quick replies on this board.

[http://ubuntuforums.org/showthread.php?t=404436](http://ubuntuforums.org/showthread.php?t=404436)

:confused:

---

### Post by Narcoleptic_Insomniac on 2007-04-08
> **Hieronymus said:**
> assuming that sude is an error in typing this should work normally. But what happens when you use the code I typed, with gdm also added in your case?
And if that doesn't work try to do 
```

su
apt-get install ubuntu-desktop gdm

```

Jeroen

Yes Sude was a typing error. 
I tryed typing what you said and its telling me to enter the Kubuntu 6.10 disc into my drive and I don't have that disc. I installed Edgy via the internet. So what do I do now.

---

### Post by Hieronymus on 2007-04-08
First check if you have the package available somewhere, check your /etc/apt/sources.list if you have unchecked all sources (remove the # in front of the lines starting with deb and put a # in front of the line which mentions the cd)

Then save and do an update, and try again.

```


sudo nano /etc/apt/sources/list
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop gdm


```

Jeroen

---

### Post by Narcoleptic_Insomniac on 2007-04-08
Screw this I'll just burn the CD. But that brings me to another question, I burnt the alternate Feisty Beta CD and it won't load from computer start up, any reason why?

---

