---
title: "extract a tar.gz to a specific directory using terminal"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by zmuth734 on 2007-01-03
I'm looking to extract a tar.gz file to a specific folder using the terminal.

I'm following this guide to install MS Fonts on ubuntu: [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

I'm on the step where you are supposed to do:
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

But instead I have a myfonts.tar.gz file to use.  I had to get this file from a given link further into that thread because I get a 404 error when trying to download the files as told in the original guide.

Thanks for your help.

---

### Post by Bachstelze on 2007-01-03
Is there any reason why you don't want to just *apt-get instal msttcorefonts* ?

Anyway, to answer your question, the command is :

```
sudo tar xzvf myfonts.tar.gz -C /etc/fonts
```

---

### Post by zmuth734 on 2007-01-03
> **HymnToLife said:**
> Is there any reason why you don't want to just *apt-get instal msttcorefonts* ?

Anyway, to answer your question, the command is :

```
sudo tar xzvf myfonts.tar.gz -C /etc/fonts
```

I did sudo apt-get install msttcorefonts, I'm on the step where it says 

Download the xml files and extract the file into /etc/fonts/ as root:

sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

I guess it works without doing that? Thanks HymnToLife.

---

