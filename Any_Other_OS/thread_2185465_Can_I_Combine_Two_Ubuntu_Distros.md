---
title: "Can I Combine Two Ubuntu Distros?"
date: 2013-11-02
forum: Any Other OS
---

### Post by linuxuser196 on 2013-11-02
Is it possible that i can combine two Ubuntu distros into one?  I am a Mac user but ready to end it and windows is not a choice

---

### Post by deadflowr on 2013-11-02
Do you mean delete one and then add the space to the other?

Then yes.

However, more info would be needed to proceed from there.

---

### Post by linuxuser196 on 2013-11-02
I am using two ubuntu distros pear and elementry both have certain feature i like and dislike, I was wondering if i could combine or install that features i like into one  system instead of having to dual boot.

---

### Post by heir4c on 2013-11-02
Yes, normally you can if you can find the packages in the package manager of the distro. Or if you find the .deb or .rpm packages for that program, you can install it on the other distro. (I don't now what packagemanager Pear and Elemantary use, so I mentioned the both: .deb and .rpm.) It will not always work well but try it out. 
If both use dpkg than you can use following command to make a list of the installed packages:
```
sudo dpkg --get-selections > list.txt
```
After execute this command  you will have a file with the name: list.txt in your home folder.

You can write it down all what you like in Pear and in Elementary and the changes you want to do and than asking here if it's possible or not.

Maybe for configuration of some stuff you will have to go deeper into the system to change some of them.

---

### Post by linuxuser196 on 2013-11-02
The eLEMENTRY apps that i want is a .tgz file but i cant get it to excute on pear. Elementry cant find the pear package only the ppg and that nothing else is installed. Pear is using 13.04 and Elementry is on 12.04 is there that big of change in the system????

---

### Post by heir4c on 2013-11-03
Can't you find a .deb file for it? 
What .tgz file is it? Can you give a link? I will try it here on my Ubuntu.

---

### Post by philinux on 2013-11-03
Moved to other os/distro forum.

---

### Post by buzzingrobot on 2013-11-03
Both ElementaryOS and Pear are based on Ubuntu.  Elementary is based on the 12.04 LTS release and Pear, I believe, on 12.10.

Both use apt-get and the deb format.  Both use the Ubuntu repositories along with one of their own. Hence, packages offered by either distribution will be available as deb's in their repos.

Both significantly alter the Ubuntu base, so they are not just new themes running on Ubuntu (particularly Elementary). 

Mixing and matching might work fine, or it might not.  "Foreign" packages can bring in dependencies that clash with installed packages.  Sometimes needed installed packages will be deleted. Apt-get will display the changes about to be made, allowing the user to cancel things if necessary.

---

### Post by BBQdave on 2013-11-03
> **linuxuser196 said:**
> Is it possible that i can combine two Ubuntu distros into one?  **I am a Mac user but ready to end it** and windows is not a choice

Another thought I would offer:

I stepped away from Mac osX Tiger, Ubuntu Unity or Gnome 3 is the most comfortable DE - coming from a Mac world.

Used Ubuntu Gnome 2 - 10.04LTS and then updated to Ubuntu Unity - 12.04LTS. Unity LTS is rock solid and smooth - as close to osX *aqua smooth* as you will get, with out cloning it.

12.04LTS is my daily driver, and is supported through 2017 :)

---

