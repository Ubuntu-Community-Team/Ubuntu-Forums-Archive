---
title: "Upgrading Java"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by TNCharger on 2008-03-10
When they say "Absolute Beginner", it's me. I'm sure this is a simple problem for most of you but I'm still learning.

I'm trying Frostwire but I needed to upgrade my Java. Downloaded the file (jre-6u5-linux-i586.bin) to my desktop but I don't know how to install it. Can somebody help a newbie out? BTW, I need line by line instructions.

---

### Post by Papa-san on 2008-03-10
Here is a very good link for us nOObs... LOL
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by taurus on 2008-03-10
Why not do it the easy way, installing it from a terminal or synaptic.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
frostwire
```

p.s.  When you get to the java licensing window, hit the Tab key to highlight the <OK> and then Return to except it.

---

### Post by Papa-san on 2008-03-10
LOL... those are the ones I was looking for! Thanx taurus!

---

### Post by TNCharger on 2008-03-10
Okay, we're getting closer. Ran those commands out of the terminal and it appeared that everything was going to install perfect then at the end it says:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

How do I do that?

---

### Post by TNCharger on 2008-03-11
Okay, here's what I've done since my last post. I went to Java and followed their installation instructions. I got all the way to "Enable and Configure" and got a "Permission denied" when it tried to create a symbolic link. Is this "public key not available" thing the issue? If so, how can I resolve it? Thanks guys for any help!

---

