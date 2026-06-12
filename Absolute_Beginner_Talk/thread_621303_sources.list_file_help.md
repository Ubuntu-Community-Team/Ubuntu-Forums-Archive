---
title: "sources.list file help"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by bonnyrsa on 2007-11-23
Hi,

I am trying to make sence of my sources.list file and it's relationship with synaptic. I have the following questions.

I have added packages medibuntu through synaptic and all works fine but it does not appear in the sources.list file anywhere. Why?

Also, I noticed that [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) seems to have appeared in my third party software list. I am sure I didn't add it my self. Why?

Thanks for your help

Jon

---

### Post by aysiu on 2007-11-23
Take a look at /etc/apt/sources.list.d/medibuntu.list

---

### Post by Toadmund on 2007-11-23
It doesn't have to be labeled 'medibuntu' to get 'medibuntu' stuff, like you wouldn't need to get 'ketchup' at the 'ketchup' store.
Your sources list is web addresses where synaptic gets info for downloading, just like downloading from a website, only you don't have to go to the website yourself.

Canonical is the company that gives us Ubuntu.

---

### Post by aysiu on 2007-11-23
> **Toadmund said:**
> It doesn't have to be labeled 'medibuntu' to get 'medibuntu' stuff, like you wouldn't need to get 'ketchup' at the 'ketchup' store.
Your sources list is web addresses where synaptic gets info for downloading, just like downloading from a website, only you don't have to go to the website yourself.

Canonical is the company that gives us Ubuntu.
It doesn't have to be labeled Medibuntu, but it is:
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by Pumalite on 2007-11-23
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

