---
title: "where is opera 9?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by coderboi on 2006-07-08
The only version of opera that I can find in Synaptic is 8.51.  How do I get Opera 9?

---

### Post by Rackerz on 2006-07-08
Go to their website and download the .deb for Ubuntu.

---

### Post by coderboi on 2006-07-08
> **Rackerz said:**
> Go to their website and download the .deb for Ubuntu.

isn't it possible to get it from the repositories and not download it myself?

---

### Post by meng on 2006-07-08
> **coderboi said:**
> isn't it possible to get it from the repositories and not download it myself?
Nope.

---

### Post by catlett on 2006-07-08
Yes you can just add the opera repoisitory to your source list. Enter this command ```
sudo gedit /etc/apt/sources.list
``` When the text comes up, add these 2 lines at the end of the page 
> # Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-freeSave the document. Issue this command to update the cache ```
sudo apt-get update
```Then open synaptic and Opera 9 nwill be there.

---

### Post by beameup on 2006-07-08
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 

Add that to your repos. System/Administration/Software Properties

Initially I could see Opera in Add/Remove and when I selected it, I got a message saying commercial repos would be activated to install this but nothing ever happened. Possibly because there was na update going on at the time, I don't know. But once I added that to my repos, It worked fine. RealPlayer 10 is there too.

---

### Post by jlhughes on 2006-07-09
I followed the instructions here and was able to install Opera 9 without a hitch:

[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/)

---

### Post by christhemonkey on 2006-07-09
Or just add the commercial repository:
```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```
And then install it by the usual methods.
```
sudo apt-get update
sudo apt-get install opera 
```

---

