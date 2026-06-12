---
title: "Install flash on installs?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-09-22
Half of the times I install programs they ask me to accept license for flash that needs to be installed. Even if I say yes it doesnt manage to install it. I have flash installed and working already tough so its kind of confusing. Not really a problem as it doesnt seem to affect the programs but kinda confusing.

---

### Post by Brunellus on 2006-09-22
what programs are you installing, on what operating system?

For issues related to flash, see the RestrictedFormats wikipage

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by jcrnan on 2006-09-22
I got it recently now when trying to install Exaile, Banshee and gnome art manager. Im running Dapper drake with gnome.

---

### Post by _duncan_ on 2006-09-22
It happened to me too.

In my case I tried to install flash using synaptic, but for some reason it didn't work with firefox. So I manually downloaded and configured flash. That worked.

Today, I was prompted to update the flash-plugin from the repository. I did, but the update failed. Since then, every time I added or updated packages from synaptic, it tries to complete the update for flash.

As a workaround, I completely removed flash-plugin and just retained the manually-configured flash player. Firefox is still flash-enabled, but the "nag" from synaptic was eliminated.

---

### Post by jcrnan on 2006-09-22
duncan: How is the flashplayer retained if I purge flash-nonfree package?

---

### Post by Metacarpal on 2006-09-22
Flash solution [here]("http://www.ubuntuforums.org/showthread.php?p=1525778#post1525778")

---

### Post by _duncan_ on 2006-09-23
> **jcrnan said:**
> duncan: How is the flashplayer retained if I purge flash-nonfree package?

The manually-installed flash exists independently of the flash-plugin from synaptic. So basically you don't have to do anything except purge flash-plugin from synaptic. Of course I'm assuming you have successfully installed and configured the flash player manually. If not, just follow the link provided by Metacarpal.

---

### Post by Mimsy on 2006-10-18
> **Metacarpal said:**
> Flash solution [here]("http://www.ubuntuforums.org/showthread.php?p=1525778#post1525778")

I get the "404-not found" error when I click on that link. Is there another place I can download the package from? I need flash.

Thanks,
Mimsy

---

### Post by aysiu on 2006-10-18
> **Mimsy said:**
> I get the "404-not found" error when I click on that link. Is there another place I can download the package from? I need flash.

Thanks,
Mimsy
Several methods outlined here:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by Mimsy on 2006-10-18
And I have flash again. Thanks! :)

/Mimsy

---

### Post by aysiu on 2006-10-18
> **Mimsy said:**
> And I have flash again. Thanks! :)

/Mimsy
If you don't mind me asking--which method did you end up using?

---

### Post by Mimsy on 2006-10-18
At first I copy/pasted the the four commands just below the screenshots into a terminal, shut down Firefox, opened it again, but I don't think it realised that flash was supposed to be installed now. So I tried the first method instead, and just clicked on the "install plugin" button in Firefox when it came up.

I deliberately avoided that solution earlier because it has never worked for me in the past, but for some reason it did this time. Very strange.

/Mimsy

---

### Post by Ba|der on 2006-10-18
I installed flash-installer via the Simple Synaptics.
But it exits then choosing to download from internet. Then running the  >update-flashplugin
Gives:
"automatic installation failed due to network problems or upstream changes"

So I guess the flashplugin in the Ubuntu repositories is outdated.

---

