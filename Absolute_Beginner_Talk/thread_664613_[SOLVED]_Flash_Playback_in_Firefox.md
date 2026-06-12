---
title: "[SOLVED] Flash Playback in Firefox"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by fraser_m on 2008-01-11
I am having trouble getting the Flash plugin to work with Firefox. Gnash is installed but doesn't seem to work, and Firefox defaults to Gnash. Is there any way to change this?

Fraser

---

### Post by nikoPSK on 2008-01-11
just install the mozilla flash plugin. :KS

---

### Post by nikoPSK on 2008-01-11
I can remeber I have flash non-free but I am at school on windows right now.
 
Hope that helps,
nikoPSK

---

### Post by fraser_m on 2008-01-11
My Solution:
```
sudo apt-get install alien
```
Download Flash Installer .rpm from website.
```
sudo alien flashinstaller.rpm
```
Then install the .deb!

---

### Post by nikoPSK on 2008-01-11
> **fraser_m said:**
> My Solution:
```
sudo apt-get install alien
```
Download Flash Installer .rpm from website.
```
sudo alien flashinstaller.rpm
```
Then install the .deb!
 
not really a solution... alien can break things. I suggested getting the one supported.. .I'll come back to when I'm on ubuntu. It's best not to use alien when there is something already in deb.

---

### Post by stchman on 2008-01-11
> **fraser_m said:**
> I am having trouble getting the Flash plugin to work with Firefox. Gnash is installed but doesn't seem to work, and Firefox defaults to Gnash. Is there any way to change this?

Fraser

Install the flash plugin via synaptic.

```
sudo apt-get -y install flashplugin-nonfree
```

---

### Post by nikoPSK on 2008-01-11
> **stchman said:**
> Install the flash plugin via synaptic.
 
```
sudo apt-get -y install flashplugin-nonfree
```
 
thank you, I couldn't quite rmember the package name. :)

---

