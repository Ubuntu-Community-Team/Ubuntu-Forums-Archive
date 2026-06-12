---
title: "Is the repository not there, or ..."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by Steff_DK on 2006-01-07
Running:
```
sudo /etc/init.d/hpoj setup
```

I get: "Command not found" :o 

I'm pretty certain the repository is already added in synaptic... :rolleyes: 

I have only tried sudo apt-get xxxxxxxx install before so i can't see whats wrong with this command ... 

Got the command off this:
[https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters?highlight=%28printer%29)

---

### Post by Mustard on 2006-01-07
I would say you  might have missed the first line, just before that line where it says to install hpoj.  You could do this command to install it...

```
sudo apt-get install hpoj
```

Then proceed to that command and continue with the HOW TO instructions.

---

### Post by aysiu on 2006-01-07
hpoj is in the Universe repository (see the first link of my sig).
You can use the command given above or install it via Synaptic--for more details, read the second link of my sig.

---

### Post by Steff_DK on 2006-01-07
Okay - read the wiki a wee bit more thorough and found out that I was supposed to install the hplip packages instead. Did this from the synaptic ... uh -thingy, and then followed the wiki guidelines.

Now my HP printer-cum-scanner works!!!

Never got it working in XP, and after having downloaded all sorts of sh*te from the internet, including HP's own drivers, I gave up ...

Now it works again!!!

In your face XP :p

---

