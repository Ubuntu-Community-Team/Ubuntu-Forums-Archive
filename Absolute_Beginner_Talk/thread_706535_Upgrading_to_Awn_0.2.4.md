---
title: "Upgrading to Awn 0.2.4"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by jasonhaley on 2008-02-24
Awn 0.2.4 is out now and I was wondering how do I upgrade my pre-existing AWN to it? Do I have to completely re-install it? I've downloaded the .tar file from AWN's site, I'm just not sure what to do now.

---

### Post by LuisGMarine on 2008-02-24
This is how I was able to upgrade mine, by running this command.  I have the AWN repos added to my */etc/apt/souces.list*

This command is what I used to update my AWN:
```

bzr update
```

However if this doesn't work, then read this [**wiki**]("http://wiki.awn-project.org/index.php?title=InstallingFromSource") on how to update, you might try to use what they are saying.  Hope this helps.  If worst comes to worst, then yes you might have to remove and reinstall the new version.  

If you decide to do that, then follow the HOWTO on the ubuntu forums on how to go about removing AWN, and installing it from source.

[**http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+curves**]("http://ubuntuforums.org/showthread.php?t=385981&highlight=awn+curves")

---

### Post by glennric on 2008-02-24
"bzr update" won't update awn.  Not by itself.  That will only update the source if you have already downloaded them from bzr.  Then you have to compile and install them with the usual
```
./configure
make
make install
```
or if you know better, by making debs.

To install the source that you downloaded you will have to extract the tar file, change to the directory created and do the above.

---

### Post by glennric on 2008-02-24
By the way I have debs compiled from the latest bzr code if you want them.

---

