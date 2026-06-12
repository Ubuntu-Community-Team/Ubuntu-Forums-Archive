---
title: "[SOLVED] Cannot find these files in Synaptic"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-14
I Cannot find these files in Synaptic in ubuntu 7.10. the files are gtk2-engines-murrine and 
gtk2-engines-pixbuf. I want to install it for installing a theme

---

### Post by kesman on 2008-02-14
have you enabled all the repositories in system -> administration -> software sources?

---

### Post by jw5801 on 2008-02-14
```
sudo apt-get update
sudo apt-get install gtk2-engines-pixbuf gtk2-engines-murrine
```
You'll probably find they're already installed. I think they're part of the default install.

---

### Post by mikeyphi on 2008-02-14
And also make sure you search under ALL in synaptic

---

### Post by hyper_ch on 2008-02-14
murrine installs by default?

---

### Post by jw5801 on 2008-02-14
Well, I have it installed on an almost vanilla install, so I'd assume so! It is an Xubuntu install though.

---

