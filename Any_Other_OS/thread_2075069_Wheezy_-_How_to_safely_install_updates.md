---
title: "Wheezy - How to safely install updates?"
date: 2012-10-23
forum: Any Other OS
---

### Post by ArtF10 on 2012-10-23
I just installed Debian Wheezy. It came pre-installed with Gnome 3 as the default desktop environment.

Now I need to update it.

What is the command to safely install updates in debian Wheezy?

Would this work:
```
sudo apt-get update
```

Let me know.

---

### Post by Erik1984 on 2012-10-23
```
apt-get update
``` only queries the sources, you need to run ```
apt-get upgrade
``` after that to actually install available updates.

you can put them in one line:
```
apt-get update && apt-get upgrade
```but yes those are the commands to install updates in Debian as well as in Ubuntu. You do need to be root to run those commands. You can become root by running
```
su
```

after doing your root work you can become normal user again by typing
```

exit

```

---

### Post by Majorix on 2012-10-23
I don't know what you mean with "safely". There is always a chance of breakage with every way of upgrading/installing software. If you want extreme, incredible stability, you need to look at Debian Stable.

Please note that I am using Debian Unstable myself for over a year and have never got anything broken.

---

### Post by lykwydchykyn on 2012-10-23
The recommended package management software on Debian is aptitude.

The "safe upgrade" command is:
```

aptitude safe-upgrade

```

Though it's synonmous with just:
```

aptitude upgrade

```

The difference between this and a "full-upgrade" or "dist-upgrade" (same thing) is that the "safe-upgrade" won't install new packages or remove installed packages to resolve dependencies, meaning not all packages will upgrade in some situations.

---

### Post by Bart_D on 2012-10-23
How exactly does Debian unstable work? I mean assuming you wanted to ALWAYS be working with Debian testing, how do you update/upgrade?

EXAMPLE:
The current version of Debian testing is Wheezy. So, let's say a user has installed Wheezy. After a few months, Wheezy will become stable (correct???). If the user does NOT want to install a new version of Debian stable every 8 months, then the version of Debian that he/she has installed must ALWAYS be Debian testing*. However, in 8 months from now, the version of Debian testing is NOT Debian Wheezy...it might be Debian Z***abcdefg. So, how does the user constantly stay with Debian testing (without having do do a new installation every 8 months)? Does:

```
apt-get update && apt-get upgrade
```

accomplish this?

* assume he/she does not want Debian Sid

---

### Post by snowpine on 2012-10-23
To upgrade my Debian Testing and Unstable systems I always use:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Testing/Unstable is too fast-moving in my opinion to use 'upgrade' instead of 'dist-upgrade'.

@**Bart_D** if your /etc/apt/sources.list points to "wheezy" then you will track Wheezy from testing to stable to old-stable. If your /etc/apt/sources.list says "testing" then you will track Testing from Wheezy to Jessie to whatever comes next. If it says "unstable" or "sid" then you will always have rolling-release Unstable/Sid. Also keep in mind Debian releases are more like every 24 months than every 8 months!

---

### Post by Bart_D on 2012-10-23
Here's the thing though:

The OP indicated that Gnome 3 came as default with Debian testing(Wheezy). I read that Debian will be switching to XFCE. So, when Wheezy goes to stable (assume that etc/apt/sources.list says "wheezy") then will your installed version of Debian wheezy automatically switch to XFCE at this time?

---

### Post by snowpine on 2012-10-23
> **Bart_D said:**
> Here's the thing though:

The OP indicated that Gnome 3 came as default with Debian testing(Wheezy). I read that Debian will be switching to XFCE. So, when Wheezy goes to stable (assume that etc/apt/sources.list says "wheezy") then will your installed version of Debian wheezy automatically switch to XFCE at this time?

Debian always has (and always will) allowed you to choose either Gnome or Xfce, whichever you prefer. :)

Wheezy will not change significantly as it is in "freeze" for final testing and release soon. What you have now is pretty much what you will get in the final stable release, except for some bug fixes.

---

### Post by lykwydchykyn on 2012-10-23
> **Bart_D said:**
> then will your installed version of Debian wheezy automatically switch to XFCE at this time?

I don't believe so, because the desktop is installed explicitly by tasksel during the installer.  There's no "debian-desktop" meta-package that installs the default desktop like the "ubuntu-desktop" package does on Ubuntu.

In other words, if the installer installed "gnome3", then APT is just going to keep upgrading gnome3.

---

### Post by ArtF10 on 2012-10-23
Thanks for the replies.

There is a "Software Update" option in the "Applications" menu.

Is this the same as

```
apt-get update && apt-get upgrade
```

---

### Post by BBQdave on 2012-10-23
> **lykwydchykyn said:**
> I don't believe so, because the desktop is installed explicitly by tasksel during the installer.  There's no "debian-desktop" meta-package that installs the default desktop like the "ubuntu-desktop" package does on Ubuntu.

In other words, if the installer installed "gnome3", then APT is just going to keep upgrading gnome3.

Most of the talk about *default desktop* is the switch from Gnome 3 to Xfce on the Debian 7 install CD, which was done for space - a functioning desktop of Xfce that fits on a Debian install CD.

The preferred install method of Debian 7, Net-install, will offer a choice of different desktops.

So which ever desktop you choose, regardless of install method, APT will maintain - update - upgrade :)

---

### Post by snowpine on 2012-10-24
> **ArtF10 said:**
> Thanks for the replies.

There is a "Software Update" option in the "Applications" menu.

Is this the same as

```
apt-get update && apt-get upgrade
```

I've never used it before (I prefer command line) but if it's the same as Ubuntu then it's:

```
apt-get update && apt-get dist-upgrade
```

As I mentioned above, I recommend dist-upgrade instead of upgrade.

---

### Post by mips on 2012-10-24
> **Bart_D said:**
> 
EXAMPLE:
The current version of Debian testing is Wheezy. So, let's say a user has installed Wheezy. After a few months, Wheezy will become stable (correct???). If the user does NOT want to install a new version of Debian stable every 8 months, then the version of Debian that he/she has installed must ALWAYS be Debian testing*. However, in 8 months from now, the version of Debian testing is NOT Debian Wheezy...it might be Debian Z***abcdefg. So, how does the user constantly stay with Debian testing (without having do do a new installation every 8 months)? 

I suspect you could simply change the repo names?

---

