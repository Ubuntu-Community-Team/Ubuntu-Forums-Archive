---
title: "problems installing nvidia drivers"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by unabatedshagie on 2007-01-10
I should really stop messing about with things but anyway :)

I'm having problems installing the nvida drivers.

I run this command: sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx but when I do I get this error message:
```

linux-restricted-modules-2.6.17-10-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9742
E: Broken packages
```


How would I go about fixing this?

---

### Post by K.Mandla on 2007-01-11
Unless I'm mistaken (which has happened before ;) ), you're installing the headers for the generic version, which is incompatible with the nvidia driver because it doesn't include the kernel module for nvidia.

Try *sudo aptitude install nvidia-glx linux-386 linux-headers-386*, which ***should*** bring in the linux-386 package and the built-in nvidia support. After you reboot, it will start the 386 kernel and nvidia-glx should be installed as well.

Of course, having said that, I'm wondering if it's going to work, since the last time I suggested it, it turned into a fiasco. :rolleyes:

---

### Post by pcomelade on 2007-01-11
You can try to install them with automatix2

add to your source.list:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
and update

Good luck!

M;

---

### Post by RaZoR-x11 on 2007-01-11
No no no no, Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That will solve ya problem's. :)

---

### Post by spockrock on 2007-01-11
> **unabatedshagie said:**
> I should really stop messing about with things but anyway :)

I'm having problems installing the nvida drivers.

I run this command: sudo apt-get update && sudo apt-get install linux-restricted-modules-$(uname -r) nvidia-glx but when I do I get this error message:
```

linux-restricted-modules-2.6.17-10-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9742
E: Broken packages
```


How would I go about fixing this?

what repositories do you have enabled? the error to me seems to be a missing repository issue.

And you can use the nvidia driver with the generic kernel I am doing it on two machines.

---

### Post by Sunflower1970 on 2007-01-11
> **RaZoR-x11 said:**
> No no no no, Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That will solve ya problem's. :)

I would second this. Even though I'm still having some trouble with getting my screen to look right, it's *almost* there...

It took me a few tries to figure out Envy, though....

(still working on getting the hard drive problem resolved now, though

---

### Post by rhand on 2007-02-19
I'm having the same problem here is my sources.list
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

deb http://nl.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy restricted main multiverse universe #Added by software-properties

deb http://nl.archive.ubuntu.com/ubuntu/ edgy universe

deb http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe


#codecs:
deb http://seveas.imbrandon.com edgy-seveas all
# deb-src http://seveas.imbrandon.com edgy-seveas all

#picasa
deb http://dl.google.com/linux/deb/ stable non-free

#beryl
deb http://ubuntu.beryl-project.org edgy main
deb http://beryl.limitless.lupine.me.uk edgy main

#compiz
deb http://gandalfn.club.fr/ubuntu edgy stable

#nvidia
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy unstable

```

```
roeland@aldazar:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9742
E: Broken packages

```

```
roeland@aldazar:~$ apt-cache policy nvidia-glx
nvidia-glx:
  Installed: 1.0.8776+2.6.17.7-10.1
  Candidate: 1.0.9742+2.6.17.6-2~beta.lupine1
  Version table:
     1.0.9742+2.6.17.6-2~beta.lupine1 0
        500 http://nvidia.limitless.lupine.me.uk edgy/unstable Packages
     1.0.8776+2.6.17.7-11.1 0
        500 http://security.ubuntu.com edgy-security/restricted Packages
 *** 1.0.8776+2.6.17.7-10.1 0
        100 /var/lib/dpkg/status
     1.0.8774+2.6.17.5-11 0
        500 http://archive.ubuntu.com edgy/restricted Packages
        500 http://nl.archive.ubuntu.com edgy/restricted Packages

```
I have beryl working and I would rather not use a script or anything to fix this, just apt... Unless that's not possible ofcourse :)

---

### Post by Repent on 2007-02-19
Use this to install your drivers it's fast and really easy.

[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

It's what I used when all the other ways failed to work.

Repent

P.S. Someone should really put this in a sticky post.

---

### Post by Mottq on 2007-02-19
I used Automatix also. It worked beautifully.

---

