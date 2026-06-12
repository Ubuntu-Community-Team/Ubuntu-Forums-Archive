---
title: "update azureus"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2008-01-25
I installed azureus from the latest package on getdeb.net problem is when the internal azureus update try to update the program wont it work, i get the error msg "usr/share/azureus isnt writable"

Is it possible to get azureus to update it self? updateing to version 3.0.4.2

---

### Post by taurus on 2008-01-25
The reason you can't upgrade from azureus because you don't have permission to write to /usr/share.  So, either run azureus with root privilege or upgrade it it by hand.  Since you downloaded the previous version from getdeb.net, see if it has the latest and you can install it from a terminal again.

---

### Post by celticbhoy on 2008-01-25
Why did you not install from the repos ????

---

### Post by rudlavibizon on 2008-01-27
I managed to update it running as root (sudo) but isn't this a security risk? Is there a safer way, for instance to manually copy the updates to /usr or even installing the whole azureus in /home?

PS. I use the get-deb version since its the 3.* version as oposed to 2.5 in repos

---

### Post by taurus on 2008-01-27
If I were to download and install azureus by hand, I would get the .tar.gz or .tar.bz2 and unpack it in my ~/bin.  Then, you shouldn't have any problem running and upgrading or even installing plugins for it.

Clean and easy and no need to mess around with the system.

---

### Post by Perfect Storm on 2008-01-27
> **rudlavibizon said:**
> I managed to update it running as root (sudo) but isn't this a security risk? Is there a safer way, for instance to manually copy the updates to /usr or even installing the whole azureus in /home?

PS. I use the get-deb version since its the 3.* version as oposed to 2.5 in repos

Aye. the best solution would download Azureus from their homepage and run it as user in the user home.

---

### Post by mikewhatever on 2008-01-27
> **taurus said:**
> If I were to download and install azureus by hand, I would get the .tar.gz or .tar.bz2 and unpack it in my ~/bin.  Then, you shouldn't have any problem running and upgrading or even installing plugins for it.

Clean and easy and no need to mess around with the system.

Is unpacking all it needs, does it not require installation?

---

### Post by Perfect Storm on 2008-01-27
cd /into/the/folder
./azureus


should do it.

---

### Post by taurus on 2008-01-27
> **mikewhatever said:**
> Is unpacking all it needs, does it not require installation?

The only requirement is to have a working java on your machine, NOT the gij one.  So, just unpack it somewhere and run it from there or create a short cut to it on the top panel.

---

### Post by Bruce H. McCosar on 2008-01-27
Azureus worked well for me, and I have some tips.  But also a concern.

If you have something else that requires java, you may already have gij or the equivalent on your system, required by that package.  You can install java 1.6 no problem.  But with two different versions, sometimes the packages 'go with what they know'.  There's this little tool called ```
update-alternatives
``` that will let you choose between the different versions.

For example, when I go

```
update-alternatives --display java
```

I get the following output:

```
java - status is auto.
 link currently points to /usr/lib/jvm/java-6-sun/jre/bin/java
/usr/bin/gij-4.2 - priority 42
 slave java.1.gz: /usr/share/man/man1/gij-4.2.1.gz
/usr/lib/jvm/java-6-sun/jre/bin/java - priority 63
 slave java.1.gz: /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-6-sun/jre/bin/java.
```

If you get upset by what you see, you can change it through

```
sudo update-alternatives --config java
```

which walks you through the change in text mode.

Now the concern part:

After my recent update, my internet connection started going up, down, up, down during huge downloads.  I searched all over to find the culprit.  Finally, when I disabled Azureus, everything snapped back into place.  I don't know the actual bug, but that's the end result.

Anyway, I'm new here, so hope my input is helpful.  I just upgraded to (heh heh) **Kubuntu Studio** (when names collide department ... Ubuntu Studio + Kubuntu ) from Debian.

---

