---
title: "Unable to create new X config backup file"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-17
Nvidia setup program says:

Unable to delete X config backup file '/etc/X11/xorg.conf.backup'.

Then I deleted the backup file myself, now it claims:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Thoughts?

---

### Post by brennydoogles on 2007-08-17
> **mikex said:**
> Nvidia setup program says:

Unable to delete X config backup file '/etc/X11/xorg.conf.backup'.

Then I deleted the backup file myself, now it claims:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Thoughts?

are you running the program as root??? If not, simply append "sudo" to the beginning of the command, and you will be running as root. When it asks for your password, it is the same password you use to login.

---

### Post by loserboy on 2007-08-17
i dunno... permissions error?

edit:  beat me to it

---

### Post by mikex on 2007-08-17
When I installed Envy, the Nvidia program was added to my applications menu, and when I click on it there, it just comes up and runs. Are you saying it should ask me for a password? Why did Envy add it to my menu in such a way?

---

### Post by cheshirekow on 2008-05-09
This seems to be an old thread but in case someone stumbles upon it... you can launch the nvidia settings through the following:

```
sudo nvidia-settings
```

then put in your password and you'll be running it as "root". There shouldn't be any problem saving to the configuration file after that.

---

