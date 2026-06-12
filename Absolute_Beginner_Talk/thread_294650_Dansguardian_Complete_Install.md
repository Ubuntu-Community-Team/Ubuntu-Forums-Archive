---
title: "Dansguardian Complete Install"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by folta on 2006-11-06
Hi. I'm completely new to Ubuntu and I just finished installing the latest version. I have been trying for the past hour to install Dansguardian to use the pc as a content filter between our router and modem. I have 2 Ethernet cards plugged in but I don't know where to go. Can anybody give me a step by step guide on how to install Dansguardian (including what file to download) and configure it so it filters the content between my router and modem?

Thank You,
Tom

---

### Post by adamkane on 2006-11-06
Fortunately Google is a good resource for this particular software. Here are some howtos:

[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

Let us know how it goes.

---

### Post by Najand on 2006-11-06
First Edit your repositories:
   1. Click "System"
   2. Click "Administration"
   3. Click "Software Sources"
   4. Enter your Password
   5. Check all options in the page with "Ubuntu 6.10" tab.
   6. After reloading the packages list, Click Close

Now for install there are a few different ways:
A. Easier GUI Synaptic 
Then install it using Synaptic. Find the Dansguardian Package, right click on it and mark it for install, then click "apply". It will install automatically for you. (If you cannot find it there, just click reload and then look for it again.)

B. Using terminal
Terminal can be found at Application -> Accessories
Run the following:
```

sudo apt-get update && sudo apt-get install dansguardian

```
It will download and install it for you automatically.

---

### Post by folta on 2006-11-06
i tried that and a bunch of other tutorials but when i run the 
```

sudo apt-get install dansguardian tinyproxy firehol

```
it returns with an error.

---

### Post by Najand on 2006-11-06
Well, that is because you don't have UNIVERSE repository. Just add it by  ediiting them as I wrote above.

---

### Post by folta on 2006-11-06
> **Najand said:**
> First Edit your repositories:
   1. Click "System"
   2. Click "Administration"
   3. Click "Software Sources"
   4. Enter your Password
   5. Check all options in the page with "Ubuntu 6.10" tab.
   6. After reloading the packages list, Click Close

Now for install there are a few different ways:
A. Easier GUI Synaptic 
Then install it using Synaptic. Find the Dansguardian Package, right click on it and mark it for install, then click "apply". It will install automatically for you. (If you cannot find it there, just click reload and then look for it again.)

B. Using terminal
Terminal can be found at Application -> Accessories
Run the following:
```

sudo apt-get update && sudo apt-get install dansguardian

```
It will download and install it for you automatically.

i'll try this.

---

