---
title: "Beryl Help"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-17
When following the guide here:

[http://ubuntuforums.org/showthread.php?t=263851&highlight=Beryl+Help](http://ubuntuforums.org/showthread.php?t=263851&highlight=Beryl+Help)

I ran into the following error:

ross@ross-laptop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  nvidia-glx: Depends: nvidia-kernel-1.0.9629
              Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be inst alled
              Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
              Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be ins talled
              Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1 is to be inst alled
              Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be in stalled
E: Broken packages



What does this mean? How could I fix it? I just saw a video of Beryl and it looks flippin' amazing!

---

### Post by biffta on 2006-11-17
Are you sure you followed all of the previous steps successfully?

---

### Post by Abstract on 2006-11-17
Have you installed the build-essential package?

```
sudo aptitude install build-essential
```

---

### Post by guitarist549 on 2006-11-17
Yes I followed the instructions correctly but this occurred on the second step so I haven't had a chance to mess anything up, lol....

When installing the essentials, I get this:

The following packages have been kept back:
  libwnck18 nvidia-glx xserver-xgl

---

