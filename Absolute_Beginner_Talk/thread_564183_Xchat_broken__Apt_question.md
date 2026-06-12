---
title: "Xchat broken / Apt question"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-09-30
As subject states, Xchat on one particular installation won't load... logs state a "half installed" condition.   Xchat is running fine on several other systems.   Used Synaptic to uninstall, uninstall and remove, and other combinations.  Reinstallation returns the same error.  Made me think I need to get rif of the .deb files in the /var/cache/apt directory, but I can't find anything that says how to do this.  

Can I, should I just go manually delete the 5 or so files related to Xchat, or am I really asking for a problem by breaking Apt/Synaptic?  Or, is there another way to recover from this "half installed" error that I don't know about yet?

tx

---

### Post by chuckyp on 2007-09-30
Those are just backups of the debs downloaded from the repos.  You can safely delete them and apt will redownload them.  Also its a good idea to keep an eye on /var/cache/apt because it can grow rather large keeping older versions.  You can:
```

sudo apt-get autoclean

```
To delete older versions of packages that have alternatives installed or availible from the repos.

---

### Post by Dr Small on 2007-09-30
Also try
```
sudo apt-get remove xchat --purge
```

To delete configuration files.

---

### Post by drhiii on 2007-09-30
Thank you all for this helpful information.  I will employ both methods and see if this solves the Xchat problem, and also saves space!

tx a mill

---

