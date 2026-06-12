---
title: "Which download do I choose?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-10-24
I need to download a Java missing plugin.  Which one do I choose? And if anyone had time, can you tell me if that is the same type I should always choose?

[LIST]
[*]Linux RPM (self-extracting file) filesize: 17.74 MB
[/LIST] 
[LIST]
[*]Linux (self-extracting file) filesize: 18.23 MB
[/LIST]
[LIST]
[*]Linux x64 * filesize: 17.24 MB
[/LIST]
[LIST]
[*]Linux x64 RPM *
[/LIST]

---

### Post by danm-koder on 2007-10-24
First of all, you should try Synaptic (or Adept for Kubuntu ) and check if it's there (which I'm pretty sure it is) and the install will be sort of automatic, if you are completely sure that it isn't there, then download the self-extracting one and use a terminal to install it...

---

### Post by p_quarles on 2007-10-24
The Java plugin is available in the Ubuntu repositories. The quickest way to get is to open a terminal and type:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install various popular proprietary software, including Sun Java and Macromedia Flash. 

As for package types, Ubuntu uses the ".deb" package type. ".rpm" is for Red Hat based Linuxes.

---

