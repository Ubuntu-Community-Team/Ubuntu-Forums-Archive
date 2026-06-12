---
title: "[SOLVED] my custom ubuntu cannot adding ppa"
date: 2013-06-29
forum: Any Other OS
---

### Post by asdeps on 2013-06-29
my custom ubuntu cannot adding ppa, via terminal.
this is the error message:

```

Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 125, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp
    curl.perform()

```

any suggestions?

---

### Post by sanderj on 2013-06-29
Is that all the output you get? Aren't you leaving out a few lines at the end?

Did you Google "File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 84, in get_ppa_info_from_lp"?

Is your Internet working? Are you behind a proxy?

---

### Post by asdeps on 2013-07-01
my internet is working, and no proxy use.
my custom distro named "asdeps" and customization used based on "precise"

---

### Post by 2Stoned on 2013-07-09
You should have kept the original Ubuntu and Precise names for the custom build or you can get problems updating and adding ppa. What program did you use?

---

### Post by asdeps on 2013-07-16
yes, thank you for all answer.
I understand now it turns out the problem is the name of the distro that I made, and the PPA should be added to the distro with the code name "precise".

---

