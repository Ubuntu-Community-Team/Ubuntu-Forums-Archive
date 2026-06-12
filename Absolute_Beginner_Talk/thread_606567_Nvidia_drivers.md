---
title: "Nvidia drivers??"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by poision_heart on 2007-11-08
I install gutsy n everything working well.I ve enabled restricted drivers of nvidia for my laptop.But here i ve one doubt,there is on splash screen of nvidia or there is no nvidia config manager i found in ubuntu.Is anything wrong with my installation?Last time i used envy i got splash as well as nvidia config manager.I also heard that envy using best new nvidia drivers than the one available at restricted manager drivers.Pls guide

---

### Post by PartisanEntity on 2007-11-08
Look in your /etc/X11/xorg.conf file and see which drivers are being used by your graphics card. Does it say nv or nvidia?

---

### Post by khurrum1990 on 2007-11-08
Hi, in the default Nvidia driver configuration in 7.10 there is an option Nologo, something like that which removes the splash screen from coming cause many people don't like it. Also in 7.10 everything is automated and u don't need nvidia config manager because there is already a graphical interface for x server in 7.10. 7.10 provides u with latest drivers so they don't need nvidia-xconfig either. I hope I helped. Good Luck!

---

### Post by poision_heart on 2007-11-08
Hi yes you ve solve my problem.Its alright but i am missing nvidia config editor speciall for special effects like gamma correction and cursor shadow etc etc.How can i do that in gutsy now?Thanks for help.

---

### Post by PartisanEntity on 2007-11-08
Launch a terminal and type:

```
sudo nvidia-settings
```

Be careful, if you launch the Nvidia settings in 'sudo' mode you will be able to save changes, so make sure you know what you are doing.

---

### Post by poision_heart on 2007-11-08
Thanks buddy it worked for me.

---

