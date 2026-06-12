---
title: "Thunderbird 2?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by azurelight1337 on 2007-09-26
So I want to upgrade from the default version of Thunderbird, but I don't know how...

I have the .tar.gz, but what do I do with it? :confused:

---

### Post by st33med on 2007-09-26
Do:
```
sudo apt-get install thunderbird2
```

---

### Post by Linux_Man on 2007-09-26
Download it from the Ubuntu repositories 

enter 
```
sudo apt-get install thunderbird
```


Im assuming that you don't have it installed yet, if its an update just go to Ubuntu's update manager and install the patch

---

### Post by azurelight1337 on 2007-09-26
I have 1.5 installed, and 2 doesn't show up in the update manager.

I have the .tar.gz file that Mozilla has on their website though.

---

### Post by Kilz on 2007-09-26
You could get [Swiftdove]("http://swiftweasel.sourceforge.net/"). Its an optimized build of the latest Thunderbird (2.0.0.7) code. All themes and extensions work with it. Just download the .deb and double click on it and let gdebi install it.

---

### Post by qpieus on 2007-09-26
Check out ubuntuzilla:

[http://ubuntuforums.org/showthread.php?t=543715](http://ubuntuforums.org/showthread.php?t=543715)

then follow the link to the sourceforge page and follow the directions. It upgraded me to v2.006 easily, with no problems.

---

### Post by kristianz on 2007-10-22
For some reason, Thunderbird has never, and I mean never, been able to find previous accounts to import, when I install a new version. With the upgrade to Ubuntu 7.10, I once again have to start over with a whole new clean thunderbird, configuring it all over and teaching it my spam rules and so one. Very annoying indeed.

---

### Post by LowSky on 2007-10-22
at least thunderbird's spam filter works, I tried using Evolution but that POS cant do filtering worth a snail's slime.

---

### Post by tolremeno on 2007-10-22
> **kristianz said:**
> For some reason, Thunderbird has never, and I mean never, been able to find previous accounts to import, when I install a new version. With the upgrade to Ubuntu 7.10, I once again have to start over with a whole new clean thunderbird, configuring it all over and teaching it my spam rules and so one. Very annoying indeed.
You can do the "import" manually. Just start thunderbird with the profilemanager flag (I think it's just --ProfileManager) and point a new profile to the old profile folder in your home directory.

---

### Post by Absorbed on 2007-10-22
I use the Thunderbird tar.gz because the repository package doesn't automatically setup gmail accounts. It's very simple. You extract the tar.gz to a folder, like /usr/local/thunderbird/, and then you run the following:
```
/usr/local/thunderbird/thunderbird
```

You might also want to create a symlink so that you only need to type "thunderbird" to run it:
```
ln -s /usr/local/thunderbird/thunderbird /usr/local/bin/
```

Then I create an item in my menu, and it's just like it's installed from the repository. All in all, I was surprised how easy it was.

---

### Post by philinux on 2007-10-22
Ubuntuzilla is the best way as it does not mess with synaptic.

---

### Post by kristianz on 2007-10-23
> **tolremeno said:**
> You can do the "import" manually. Just start thunderbird with the profilemanager flag (I think it's just --ProfileManager) and point a new profile to the old profile folder in your home directory.

Thanks, I'll try that next time around.

---

