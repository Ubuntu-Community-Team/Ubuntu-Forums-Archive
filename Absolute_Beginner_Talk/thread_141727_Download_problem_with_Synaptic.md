---
title: "Download problem with Synaptic"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-03-08
I have a high speed connection to the internet. However I am only having problems with downloads from us.archive.ubuntu.com/pool... With Synaptic Package Manager

Are they having a problem? I have tried all day and just completed a download UPDATE. But am unable to download firestarter. any Ideas ?
Thanks

---

### Post by Xian on 2006-03-08
Everybody has problems with that repo sooner or later. It's a dog.
Try just using the 'archive.ubuntu.com' [no 'us' prefix] mirror in your sources.list.

---

### Post by kent41 on 2006-03-08
[QUOTE=Xian]Everybody has problems with that repo sooner or later. It's a dog.
Try just using the 'archive.ubuntu.com' [no 'us' prefix] mirror in your sources.list.[/QUOTE]

Thanks but how do it get the mirror site ?
Do I change all refferences to archive.ubuntu.com rather than us.archive.ubuntu.com/pool...?

---

### Post by Xian on 2006-03-08
[QUOTE=kent41]Thanks but how do it get the mirror site ?
Do I change all refferences to archive.ubuntu.com rather than us.archive.ubuntu.com/pool...?[/QUOTE]

Yeah, just chop off the 'us' and save. Like this:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
```

---

### Post by kent41 on 2006-03-09
[QUOTE=Xian]Yeah, just chop off the 'us' and save. Like this:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
```[/QUOTE]

Thanks  Xian I was able to download everything I needed. Thanks for the help

---

