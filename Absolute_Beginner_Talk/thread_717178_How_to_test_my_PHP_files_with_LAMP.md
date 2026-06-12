---
title: "How to test my PHP files with LAMP?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by jezebel on 2008-03-06
Hi

This is probably a very simple thing, but where do I put my php files to test them in my development environment? I installed LAMP - but when I try to save a file to var/www I receive a message saying that I do not have permission to write it.

Thank you.

PS-I'm very much a beginner at php too.

---

### Post by Dr Small on 2008-03-06
Please use sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by Nythain on 2008-03-06
sudo it up
from terminal
```

sudo cp /path/to/file.php /var/www

```
should do the trick
you could also create a folder within your home folder, and symlink /var/www to that folder and there's other tricks of the trade so you can design in a non root environment

---

### Post by jezebel on 2008-03-06
Thanks -

I tried doing sudo nautilus via the terminal, but when using Quantus and clicking "save as", I can't save to the var/www directory.

Do I have to save somewhere else (home folder, for example) then copy and paste?

---

### Post by jezebel on 2008-03-06
Nythain - my reply must have overlapped yours.

Thanks - um...the symlink thing sounds great; how would I do that?

---

### Post by Nythain on 2008-03-06
you could do it that way... or you could trying running this quantus with a gksu from command line, giving it graphical sudo privileges

---

### Post by jezebel on 2008-03-07
Thank you!

Being a bit too ..."non-technical", I've opened my www directory as super user, and copies my website php files there for testing.

So - LAMP and  the testing working great now.

---

### Post by The Titan on 2008-03-07
It may be a security issue, but you could just chmod /var/www to writable by you.

---

