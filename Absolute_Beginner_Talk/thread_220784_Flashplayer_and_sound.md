---
title: "Flashplayer and sound"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Wadeisabeast on 2006-07-22
I'm trying to install a flashplayer so I can watch videos on youtube.  I downloaded it, but don't know how to install.

Here are teh dicections - 
Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

where is the command line?

Also, I downloaded a different video, and I get no sound with the media player.  Does anybody know how to fix this?

---

### Post by Jagot on 2006-07-22
The commandline is from Applications -> Accessories -> Terminal

HOWEVER, flash is available in Ubuntu's repositories - you do not need to compile from source.  You need to add the multiverse repo ([http://www.psychocats.net/ubuntu/sources.php)](http://www.psychocats.net/ubuntu/sources.php)), then issue this command:

```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

With regards to your video question, you probably need to correct codecs.  Have a look here for instructions:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There are also a couple of programs which do this for you:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
[http://getautomatix.com/](http://getautomatix.com/)

---

