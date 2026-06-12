---
title: "Installing NVidia Beta driver"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2006-12-31
As a first step to install Beryl on my desktop (NVidia Geforce 5200 AGP card), I have to install Nvidia Beta drivers, I have already installed regular drivers of Nvidia (using ubuntu guide wiki). After updating repo's and all, when I try to update the drivers apt-get says that Nvidia-glx is already the latest driver. Does that mean that I need to unistall the NVidia driver first.
 
Thanks

---

### Post by spockrock on 2006-12-31
what repo are you using, and what does apt-cache policy nvidia-glx give you when you enter that in terminal.

you don't need the latest and greatest driver from nvidia to get beryl working.

---

### Post by mahiyar on 2006-12-31
Currently I'am not at the place where linux is installed, however if I remember corectly I have added restricted, and edgy free/non free repositories, I have also installed automatix2 (though I have unchecked the repositories of automatix to avoid conflict in the Synaptic manager preferrence) and also just before installing the beta version there was an added line of repos in apt-get list. Can I force check synaptic to look just in the repo line for beta drivers by disabling other repo lines.
Regards apt-cache policy, i cannoot tell exactly but i remember my settings in synaptic being the option of latest drivers.
The current version of NVidia drivers is some 8600 or there abouts.
   Ok this is the output of apt-cache policy
nvidia-glx:
  Installed: 1.0.8776+2.6.17.6-1
  Candidate: 1.0.8776+2.6.17.6-1
  Version table:
 *** 1.0.8776+2.6.17.6-1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
        100 /var/lib/dpkg/status
     1.0.8774+2.6.17.5-11 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages

---

### Post by mahiyar on 2006-12-31
Please help. I'am waiting for an answer.

---

### Post by tseliot on 2006-12-31
try my repositories:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by mahiyar on 2006-12-31
Thanks tseliot. Its an intresting site, I will spend some time there. But I did not download the beta drivers. I installed the beryl on the 8776 driver version, and it works fine, cubes, rain drops and all. My only crib is that beryl does nothing to the gnome panels.

---

