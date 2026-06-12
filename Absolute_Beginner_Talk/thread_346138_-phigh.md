---
title: "-phigh ???"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by ljpm on 2007-01-25
Hi all, 

I have seen the following commands posted to helps with resolutions issues.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and

```
sudo dpkg-reconfigure xserver-xorg
```

What does the "-phigh" in the first command do?

---

### Post by rocknrolf77 on 2007-01-25
-phigh prevents the reconfigure too reconfigure everything in the xorg.conf, just the graphics and screen section.

---

### Post by benuski on 2007-01-25
-phigh just means that the dpkg-reconfigure is set to a high priority instead of a low one.  I don't know how much difference that makes, but I don't think that it is much.

---

### Post by ljpm on 2007-01-25
Thanks

---

### Post by bodhi.zazen on 2007-01-25
When dpkg-reconfigure, the -phigh flag selects default values for everything except resolution.

> &#8722;pvalue, &#8722;&#8722;priority=value

Specify the minimum priority of question that will be displayed. dpkg-reconfigure normally shows low priority questions no matter what your default priority is. See debconf(7) for a list.

and

> Another nice feature of debconf is that the questions it asks you are prioritized. If you don't want to be bothered about every little thing, you can set up debconf to only ask you the most important questions. On the other hand, if you are a control freak, you can make it show you all questions. Each question has a priority. In increasing order of importance:

low
    Very trivial questions that have defaults that will work in the vast majority of cases. 

medium
    Normal questions that have reasonable defaults. 

high
    Questions that don't have a reasonable default. 

critical
    Questions that you really, really need to see (or else). Only questions with a priority equal to or greater than the priority you choose will be shown to you. You can set the priority value by reconfiguring debconf, or temporarily by passing --priority= followed by the value to the dpkg-reconfigure (8) and dpkg-preconfigure (8) commands, or by setting the DEBIAN_PRIORITY environment variable. 

See man debconf

---

### Post by az on 2007-01-25
-plow will ask you every question there is.  For the xserver-xorg package, there are quite a lot.

-phigh will only ask you the high priority ones, with everything else being given the default value.

---

