---
title: "Installing from RPMs in Ubuntu 6.06 LTS"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2006-12-16
Hello, in the 90s I used Sun Solaris at ENS in Paris, but have forgotten many obvious basics about X. Right now, I can't seem to find info on how to install Doom from the tar.gz or the rpm that doesn't start me on a wild goose chase of having to download and install daisy chains of little utilities. I tried ./configure in the appropriate dir, but there were errors so I couldn't make anything. Is there a step by step easy set of instructions for dummies on how to do these things? I can't seem to install anything successfully yet (bad memory, dumb old man). Does Ubuntu have rpm support built in already? I can't seem to run them. Thanks.

---

### Post by taurus on 2006-12-16
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by konungursvia on 2006-12-16
Many thanks O Wise One. ;)

---

### Post by konungursvia on 2006-12-16
Hmm. Thanks for that, but none of the doom packages or tar archives I downloaded are found in the search on Synaptic Package Manager Search. I saved them to the /tmp/ directory, but they appear greyed out. So, it may seem silly, but I still can't install anything not already in the list.

---

### Post by obsidion on 2006-12-16
> **konungursvia said:**
> Hmm. Thanks for that, but none of the doom packages or tar archives I downloaded are found in the search on Synaptic Package Manager Search. I saved them to the /tmp/ directory, but they appear greyed out. So, it may seem silly, but I still can't install anything not already in the list.

  You don't install tar.gz and rpms with synaptic that is designed for .debs
For rpms you need to install alien and for tars you need tar.
 For an RPM from a terminal sudo alien -i nameofRPM
 
 For a tar.gz copy it to an install directory, I usually mv it to /usr/local myself
sudo mv nameoffile /usr/local/
then cd to that directory and sudo tar zvxf nameoffile

Note it is best to use debs, esp if you are new to linux, there are sometimes dependency problems and rpms may not install themselves to the correct place for the ubuntu system.

---

### Post by konungursvia on 2006-12-16
When I move them to /usr/local/ and unpack them I get "path" problems because no c compiler is being called. I can't install alien, or anything else, except .debs seem to work. Frustrating. This distro seems great, but it doesn't come with paths configured so that my cc will work? Don't know what to do. The experts instructions are great, but leave out obvious things I can't see. For example, which "nameoffiile"? Inside each tar there are several files. Hmm.

---

### Post by taurus on 2006-12-16
```
sudo aptitude install build-essential alien
```

p.s.  I did a quick search and found a few threads related to game doom!!!

[http://www.ubuntuforums.org/showthread.php?t=308625&highlight=doom](http://www.ubuntuforums.org/showthread.php?t=308625&highlight=doom)

---

