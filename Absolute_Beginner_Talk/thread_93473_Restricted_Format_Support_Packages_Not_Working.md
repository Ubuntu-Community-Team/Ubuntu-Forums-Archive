---
title: "Restricted Format Support Packages Not Working"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by mrgnash on 2005-11-22
Ok, I enabled the repositories in Synaptic and typed:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-
ffmpeg
```

But I get a: 

```
E: Couldn't find package gstreamer0.8-plugins-multiverse
```

:confused: What's going on here?

---

### Post by oskude on 2005-11-22
i doubt that "gstreamer0.8-plugins-multiverse" exists...
i assume you have misundestand something, i think it should be gstreamer0.8-plugins in multiverse reposity...```
apt-cache search gstreamer0.8-plugins
```

---

### Post by souki on 2005-11-22
did you forget to
"sudo apt-get update" ?

---

### Post by souki on 2005-11-22
[QUOTE=oskude]i doubt that "gstreamer0.8-plugins-multiverse" exists...
i assume you have misundestand something, i think it should be gstreamer0.8-plugins in multiverse reposity...```
apt-cache search gstreamer0.8-plugins
```[/QUOTE]

it exists, here is the description from synaptic
> All Multiverse GStreamer plugins
This package will ensure that all GStreamer Multiverse plugins are installed.

This package is a "metapackage"; meaning it contains no programs;
instead, it just Depends on other packages.

---

### Post by oskude on 2005-11-22
[QUOTE=souki]it exists, here is the description from synaptic[/QUOTE]
DOH :oops:

---

### Post by nlippincott on 2005-11-24
The Ubuntu FAQ guide does refer to a package called gstreamer0.8-plugins-multiverse, among a couple of others that don't seem to exist:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

Perhaps this doc is out of date, as I followed the instructions, aside from the things mentioned that were not found (baically anything that says multiverse), and I did get the various formats working that I wanted.

I thought I followed these instructions a couple of weeks ago, and don't remember any problems. Perhaps I am wrong and my memory fails me.

I am fairly new to Ubuntu, being a long-time Fedora user. I really like Ubuntu, and I am in the process of making the switch (gradually) from Fedora to Ubuntu.

---

### Post by Brunellus on 2005-11-24
you haven't enabled the multiverse repository.

follow the directions on the AddingRepositories wikipage:

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

