---
title: "Uninstalling crossover to install full version"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by painejake on 2008-01-30
Right well i installed this ([http://www.codeweavers.com/products/download_trial_linux/](http://www.codeweavers.com/products/download_trial_linux/)) version of crossover a while back and i liked it so i removed it and have only just got round to purchasing the full version anyway, i try to install the full version and it says that the crossover demo clashes with the full version how do i uninstall the demo completly?

---

### Post by zvacet on 2008-01-31
If I remember correctly you can do it from programs>system tools or from synaptic.If that doesn´t work try with 

```
sudo apt-get --purge remove** packagename**
```

or 

```
sudo dpkg --remove --force-remove-reinstreq **packagename**
```

---

