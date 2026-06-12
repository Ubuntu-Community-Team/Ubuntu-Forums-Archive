---
title: "sudo apt-get install thunderbird not working"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Cool Surfer on 2007-11-06
> bet@bet:~$ **sudo apt-get install thunderbird**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package thunderbird has no installation candidate



How to fix this pl.

---

### Post by Dr Small on 2007-11-06
```
sudo apt-get install mozilla-thunderbird
```

---

### Post by discmaster on 2007-11-06
It is avail. thru synaptic too.

---

### Post by Cool Surfer on 2007-11-06
> **Dr Small said:**
> ```
sudo apt-get install mozilla-thunderbird
```

it says
=
sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-thunderbird
:confused:

---

### Post by Dr Small on 2007-11-06
System > Administration > Software Sources
and check the Universe checkbox.

Dr Small

---

### Post by mozetti on 2007-11-06
In the future when you want to see if a package is available through the repos, you can use ```
aptitude search <package name>
```

---

### Post by aysiu on 2007-11-06
Thunderbird is in Main, not Universe.

Cool Surfer, can you post the output of these two commands? ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by Dr Small on 2007-11-06
> **aysiu said:**
> Thunderbird is in Main, not Universe.

Cool Surfer, can you post the output of these two commands? ```
cat /etc/apt/sources.list
sudo apt-get update
```
Oops.

---

### Post by hyper_ch on 2007-11-06
To find the package names in the CLI:
```

apt-cache search thunder

```

That will output all packages that have "thunder" in the package name or in the description.

---

