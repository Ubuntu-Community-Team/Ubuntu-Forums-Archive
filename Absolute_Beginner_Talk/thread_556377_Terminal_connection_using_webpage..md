---
title: "Terminal connection using webpage."
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-09-21
I'm looking for a solution where i can authenticate a user, via a web page. If they authenticate they can create a terminal session on my Ubuntu Server, which is embedded into a webpage.

Ideally i would like this to be possible with the least amount of effort from the client as possible...

Any Ideas? :)

---

### Post by Bothered on 2007-09-21
There is an nxclient java applet, but that allows full remote desktop access (can be found in the [Seveas repository]("https://wiki.ubuntu.com/SeveasPackages?highlight=%28seveas%29")). There is also the jta package in the multiverse repositories, but I've never used it.

---

### Post by robinlennox on 2007-09-22
Would it be possible to have a remote desktop session via a website with a minimal amount of install on the client computer?

---

### Post by Bothered on 2007-09-22
Yes, the java applet nx client mentioned above allows you to do just that.

---

