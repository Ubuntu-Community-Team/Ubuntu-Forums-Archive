---
title: "Please help me, trying to get DVD to work"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by NET WT on 2007-05-03
Hi, I need some help getting my Ubuntu to play DVD. I am using Ubuntu version 7.04. I followed the the instructions at the post below, and was able to get mp3 and some movies to play. 

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I am not sure how to get DVD and Win32 Codecs though. 
I am not sure where to add these lines : 

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 


The post says  "Add the following lines to add the Medibuntu repository to the file"

Where do I add it? Do I add it at the beginning of the sources.list? Does it matter? 
Thanks for any help.

---

### Post by Waappu on 2007-05-03
> **NET WT said:**
> Where do I add it? Do I add it at the beginning of the sources.list? Does it matter? Thanks for any help.

Hi

Add those lines end of sources.list and then update sources by typing in terminal ```
sudo apt-get update
```

---

### Post by NET WT on 2007-05-03
No success for me so far. I added the lines to the sources.list but I wasn't able to save the file, for some reason. I get the following message: 

"Could not save the file /etc/apt/sources.list
You do not have the permissions necessary to save the file.
Please check that you typed the location correctly and try again. "

I don't know what this means.

---

### Post by Nekiruhs on 2007-05-03
Try sudo gedit /etc/apt/sources.list

---

### Post by NET WT on 2007-05-03
I am able to  play DVDs now. This is what I did, I typed :

> sudo gedit /etc/apt/sources.list

Into the terminal, instead of: 

> $gksudo gedit /etc/apt/sources.list

Which this post had said to do:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Then I followed the rest of the instructions on the above post, and it worked.
Thanks for the help.

---

### Post by wataboutbob on 2007-05-04
> **NET WT said:**
> I am able to  play DVDs now. This is what I did, I typed :



Into the terminal, instead of: 



Which this post had said to do:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Then I followed the rest of the instructions on the above post, and it worked.
Thanks for the help.

Nice. Thankfully, VLC player handles menu's for DVDs unlike Totem. So its all good. :D

---

### Post by houstonbofh on 2007-05-04
I like ogle.  Install ogle-mmx and ogle-gui.  More like a Windows DVD player.

---

