---
title: "Installing OpenWengo 2.1.1"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Killtown on 2007-06-28
Like, how?

[http://www.openwengo.org/](http://www.openwengo.org/)


GNU/Linux
* OpenWengo 2.1.1 binary package - 23.0 Mb
[http://download.wengo.com/wengophone/release/2007-06-27/WengoPhone-2.1.1-linux-bin-x86.tar.bz2](http://download.wengo.com/wengophone/release/2007-06-27/WengoPhone-2.1.1-linux-bin-x86.tar.bz2)

---

### Post by ukripper on 2007-06-28
I think skype has more feature then this also my wireless phone works great on skype

---

### Post by Seisen on 2007-06-28
You can install it through synaptic its in the repos.

---

### Post by Killtown on 2007-06-28
> **Seisen said:**
> You can install it through synaptic its in the repos.
That's only the 2.0.0 version.

I want to try version 2.1.1.

How do you install this puppy?

---

### Post by Killtown on 2007-06-28
I'd like to install this today, can anyone help me out in installing it?

---

### Post by Killtown on 2007-06-28
Bueller?

---

### Post by lapichiflati on 2007-07-04
I just downloaded and untared it to a good directory,  /usr/local/bin, I had to chown -R root:root the directory and make the files readable for everyone, chmod -R 644, then I erased my old wengophone directory in my home folder, then ./wengophone.sh from the directory.  You have to let it think for about 10 seconds before it fires up ok.  Sorry didn't use more code brackets and give you cut and paste possibilities, but I lost my bash history.

---

### Post by kodoku on 2007-07-08
You don't actually need to "install" it, just extract the tar.bz2 to where you want it and navigate to that folder in a terminal, and then type ./wengophone.sh

Then give it a few seconds to boot.

---

### Post by desijays on 2007-07-09
got it right the first try itself, thanks to you guys.

This is to the guy that said you have to use chown and chmod.

Well, i found it completely unnecessary. Didn't even have to sudo.. no root nothing.

These are the steps to follow if you want to install wengo phone 2.1

1) download wengaphone from their website to your 'home/yourname' folder. Obviously version 2.1 and for linux :) 

2) open a terminal Application->Acessories->Terminal

3) mkdir Wengo

4) bunzip2 -k WengoPhone-2.1.1-linux-bin-x86.tar.bz2 ( -k to keep the copy just in case )

5) tar -x --directory Wengo -f WengoPhone-2.1.1-linux-bin-x86.tar 

6) cd Wengo

7) ./wengophone.sh

Thats it. happy wengoing

---

### Post by jis on 2007-07-10
> **desijays said:**
> 
[...]
5) tar -x --directory Wengo -f WengoPhone-2.1.1-linux-bin-x86.tar 

6) cd Wengo

7) ./wengophone.sh

Thats it. happy wengoing

I get directory named WengoPhone-2.1.1-minsizerel in the wengo directory, but when I cd to it, command (7) works.

---

### Post by Schoappied on 2007-07-13
Is 2.1.1 much better than 2.0 in the synaptic?

How do I get a account?
Ik get a strange console.... and can not type my nickname for example in it :confused:

---

### Post by jis on 2007-07-13
According to [OpenWengo community blog]("http://blog.openwengo.org/")  WengoPhone release 2.1.0 for Linux has big improvements.

---

### Post by p1977p on 2007-08-09
> **desijays said:**
> 

These are the steps to follow if you want to install wengo phone 2.1

1) download wengaphone from their website to your 'home/yourname' folder. Obviously version 2.1 and for linux :) 

2) open a terminal Application->Acessories->Terminal

3) mkdir Wengo

4) bunzip2 -k WengoPhone-2.1.1-linux-bin-x86.tar.bz2 ( -k to keep the copy just in case )

5) tar -x --directory Wengo -f WengoPhone-2.1.1-linux-bin-x86.tar 

6) cd Wengo

7) ./wengophone.sh

Thats it. happy wengoing

Thanks a lot desijays................ that was great!!


> **jis said:**
> I get directory named WengoPhone-2.1.1-minsizerel in the wengo directory, but when I cd to it, command (7) works.

same with me. I think it's got something to do with the latest version. btw, using xarchiver (in Xubuntu) can directly extract files (saves one step) to the specified path.

Happy wengo-ing

---

### Post by Richardky on 2007-08-26
here ya go the easy way [http://www.getdeb.net/release.php?id=1211]("http://www.getdeb.net/release.php?id=1211")

---

### Post by SunshineSmile on 2007-09-01
Okay, I followed you all the way to the ./wengophone.sh

Wengophone opened once, but when I closed it, I couldn´t find it again. Where is wengophone?

---

### Post by jis on 2007-09-01
SunshineSmile, please try ```
locate wengophone.sh
``` to find out the location of wengophone.sh.

---

### Post by jis on 2007-09-19
There is repository for WengoPhone, see:
[http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki/DebianUbuntuPackages](http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki/DebianUbuntuPackages)
Note that the repository is unauthorized and contains also other software besides WengoPhone. My installation of Ekiga refused to launch after WengoPhone installation from the repository.

Repositories would allow easy updates, if update-notifier is installed and run and updates configured in Synaptic Settings > Repositories. However, the version 2.1.1 in the repository is currently old, as there is 2.1.2 (and 2.2 alpha1) available.at [http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki](http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki)

---

