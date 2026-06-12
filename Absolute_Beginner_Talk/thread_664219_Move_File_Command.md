---
title: "Move File Command?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-10
I just installed MediaWiki and as the final step I need to move LocalSettings.php from the config directory. I can do it via Nautilus/Konqueror, but I'd like to figure it out via Terminal command.

I've looked up the 'mv' command, and have tried:
mv var/lib/mediawiki1.10/config/LocalSettings.php ~etc.mediawiki1.10

I've tried it as sudo, leading backslashes, etc. but I'm getting something wrong with the syntax. The error is always "cannot stat [filename]: No such file or directory".

The usage guides I've found don't show any examples enabling me to get this right. I'm sure it's quite straightforward. Thanks!

---

### Post by PeterJS on 2008-01-10
Yep, mv is right. If you don't put a slash on the front of the path it will start looking based on your current directory. So your source would be /var/lib/mediawiki1.10/config/LocalSettings.php.

Where are you trying to move the file to? Your destination is really mixed up and I can't figure out what it's supposed to be. ~ is shorthand for $HOME which is itself short hand for /home/*username*. etc is the configuration directory and is locate at /etc/

---

### Post by ubuntu-freak on 2008-01-10
You need the full path to it. 
 
sudo mv /home/nathan/filename /usr/share/icons
 
If the filename or folder has a space in it use " marks.
 
sudo mv /home/nathan/"My Stuff" /storage
 
Nathan

---

### Post by jjsonp on 2008-01-11
Thanks guys.

The working command was:
sudo mv /var/lib/mediawiki1.10/config/LocalSettings.php /etc/mediawiki1.10/

---

### Post by hyper_ch on 2008-01-11
> **reassuringlyoffensive said:**
>  
mv /home/nathan/"My Stuff" /storage


That works? I tend to think you had to encapsule the whole path with quotes:

```

mv "/home/nathan/My Stuff" /storage

```

---

### Post by ubuntu-freak on 2008-01-11
> **hyper_ch said:**
> That works? I tend to think you had to encapsule the whole path with quotes:

```

mv "/home/nathan/My Stuff" /storage

```

 
Nah just the file or folder with the space. That's why I said it. ;)
 
Nathan

---

### Post by hyper_ch on 2008-01-11
didn't know that :) by habit I just embrace the full path ;)

---

### Post by ubuntu-freak on 2008-01-11
> **hyper_ch said:**
> didn't know that :) by habit I just embrace the full path ;)

 
Ahh let's see. If you have something like
 
 /home/nathan/My Stuff/Your Stuff
 
Embracing the full path makes more sense. You win :)
 
Nathan

---

