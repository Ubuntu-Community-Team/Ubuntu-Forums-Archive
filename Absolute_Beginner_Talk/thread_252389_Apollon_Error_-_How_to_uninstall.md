---
title: "Apollon Error - How to uninstall?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-06
I tried installing this program called Apollon.  It supposedly has 4 of the main p2p networks on it, but when I tried to run it, it doesn't work.  Ever since then my flash has been messed up and everytime I do an update it gives me an error.  Please take a look at the error I am getting from EasyUbuntu.  I searched for Apollon in Synaptic and selected complete removal, then did an update and it says it cannot update file libfaad2-0, then spits this error out.  

The following problems were found on your system:

W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA

This is the thread that I was following on how to configure APollon:
[http://www.ubuntuforums.org/showthread.php?t=198945](http://www.ubuntuforums.org/showthread.php?t=198945)

I just want to undo whatever I did by installing this Apollon.  Thanks for any input.



I also tried running update in the terminal and this is what I get:


```
err0r@Lappy:~/easyubuntu$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  libfaad2-0
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
err0r@Lappy:~/easyubuntu$

```

---

### Post by xpod on 2006-09-06
Running the command "aptitude" instead of "apt-get" is the way to do things it seems.
It removes all the dependencies it installed where as "apt-get" on the other hand dont......seemingly.....Not sure if thats what has happened to you

---

### Post by 3rr0r on 2006-09-07
still not working... please help.

---

### Post by 3rr0r on 2006-09-07
[IMG]http://i53.photobucket.com/albums/g56/learntobndg/Screenshot5.png[/IMG]


This is the error

---

### Post by skymt on 2006-09-07
That error means nothing. Actually, it means you don't have a public GPG key for that repository, which usually means there isn't one, so it's a harmless warning.

---

