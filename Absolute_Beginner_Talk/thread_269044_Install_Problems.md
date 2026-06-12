---
title: "Install Problems"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by bubbleblabs on 2006-10-01
I have downloaded mozilla suite mozilla-i686-pc-linux-gnu-1.7.13-installer.tar.gz and saved to desktop i have then tried several ways in the terminal to install the program and am having no luck could someone please give me a step by step guide on how to do this, am i having probs because i have the firefox open when im trying to do this?

---

### Post by raphha on 2006-10-01
Would it be OK to just install firefox and thunderbird? then use synaptic or adept for installing.
if you really want to use the tar.gz package, do the following in a command shell:
1) tar -xzvf mozilla-i686-pc-linux-gnu-1.7.13-installer.tar.gz
2) cd <newly created mozilla-somthing-directory>
3) less <README or INSTALL>

(replace the things in < > as apropriate)

raph

---

### Post by sbergman27 on 2006-10-01
> **raphha said:**
> Would it be OK to just install firefox and thunderbird? then use synaptic or adept for installing.


Or if he really wants the integrated suite, he can enable the universe repository in synaptic.

System->Administration->Synaptic

Settings->Repositories

Make sure Universe (binary) is checked.

Click reload.

And then install the package "Mozilla".

---

### Post by bubbleblabs on 2006-10-01
thank you for your help

---

### Post by petri on 2006-10-01
And next time you want to install anything :) take a look at this [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

