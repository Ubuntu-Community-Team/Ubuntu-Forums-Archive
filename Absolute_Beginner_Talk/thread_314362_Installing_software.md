---
title: "Installing software"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by SFC on 2006-12-07
I'm new to Linux for about a month now and still cannot install software. I understand the repository concept however, I downloaded kmymoney from the repository, right clicked on the deb file and chose install package. The terminal window open and as the installation started the terminal said that there are about 5 dependant files not installed. I went back to the repository and found a list of files kmymoney is dependant on.
Do I have to download and install each dependant file (about 20)?
If so, why don't they all come in the package?
Anyway, I downloaded the file that the terminal window said were not there (.deb files) and tried to install those in the same manner and then got a dialog box stating "cannot access archive: No such file"
I'm lost, it can't be that difficult to install software.
Any help is greatly appreciated.

---

### Post by meng on 2006-12-07
The quick answer is yes, you need those dependencies.
The even quicker answer is why on earth download the deb when you can install from repositories? (enable universe though)
I think you need a tutorial:
[http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by SFC on 2006-12-07
Hi thanks for the reply.
I could not find it in the repository in the repository manager.
Yes, I sure I need a tutorial, any suggestions?
Thanks

---

### Post by meng on 2006-12-07
The two I mentioned explain how to expand your repositories, then if you want to use the package manager you'll find kmymoney.
Try this one if you don't like the others I gave you:
[https://help.ubuntu.com/community/Repositories/Kubuntu](https://help.ubuntu.com/community/Repositories/Kubuntu)

---

### Post by wpshooter on 2006-12-07
SFC:

If you are not doing so, let **Synaptic** handle installing all software when possible.  Like MENG said above make sure you have access to all of the NON-default source listings by adding them to the repository listings.

---

### Post by SFC on 2006-12-07
Thanks,
I thought I did in the package manager under manage repositories nd enabling the Universe component repository.
I'll give the links you suggested a try.

---

