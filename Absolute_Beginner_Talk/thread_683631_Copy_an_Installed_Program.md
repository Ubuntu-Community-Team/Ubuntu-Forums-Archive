---
title: "Copy an Installed Program"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-31
Hello!
I installed some programs using "sudo apt-get install" and some from the "Add/Remove...". I also uploaded my computer more than 400Mb. Know I wanna install ubuntu on one other computer and I need all these applications and I have to update that computer too. Is there any way to use these downloaded files or I have to do these again for that computer too?
+++
What'll happen by copying home folder?
+++
What if I wanted to install just one of programs downloaded to this computer to one other?
___
Thank you.

---

### Post by schallstrom on 2008-01-31
It's definitely not convenient to copy an installed software package from one computer to another. The different files contained in a software package are spread over the file system (e.g. binary files in /usr/bin, configuration files in /etc). What's so bad about just downloading the packages again on the second computer? Do you pay your internet connection per traffic or do you have a very slow connection?

Copying you home directory from on Ubuntu installation to another is perfectly save and common practice among Linux users.

Hope that helps. Feel free to inquire.

---

### Post by kpkeerthi on 2008-01-31
> Is there any way to use these downloaded files or I have to do these again for that computer too?
The downloaded files should be in /var/cache/apt/ unless you cleaned using **sudo aptitude clean**. 

One option is to share this folder and access it from the other machine. Then, in the other machine, cd to /shared/folder and run **sudo dpkg -i <the-package-you-need>.deb**. 

The other option is to copy the debs from /var/cache/apt/ to a CD/DVD/external HDD and then install using **sudo dpkg -i /path/to/the/package/in/cdrom** in the other machine.

```
What'll happen by copying home folder?
```
Don't copy your HOME folder. Rather consider copying the contents of your HOME folder using the same means above - Share or copy to external disks.

> What if I wanted to install just one of programs downloaded to this computer to one other?
Same as above.

---

### Post by emarkd on 2008-01-31
Synaptic saves it's downloaded packages in /var/cache/apt.  If the other computer doesn't have network access, you could copy the packages you want from there and install them on the other end, but be prepared to fight some dependency errors since the computer can't download what it needs from the repositories.

---

### Post by hums07 on 2008-01-31
Nice info kpkeerthi. Thanks.
If we have several packages with dependencies, do we have to install ('sudo dpkg...') them in a certain order? Or I can just try install and see if it needs any dependency then I will need to install the dependency first...?

---

### Post by emarkd on 2008-01-31
Either way will work.  If you start installing a package that has dependencies, it'll show you what's missing and won't install.

---

### Post by sailor2001 on 2008-01-31
home folder can be copy/paste to a memory stick (includes hidden files -- ctrl/h) and aptoncd from synaptics allows you to burn all your programs to a cd

---

### Post by schallstrom on 2008-01-31
> **kpkeerthi said:**
> 
```
What'll happen by copying home folder?
```
Don't copy your HOME folder. Rather consider copying the contents of your HOME folder using the same means above - Share or copy to external disks.


What's the difference?

---

### Post by jaytek13 on 2008-01-31
Your main point seems to be copying applications so you don't have to download them again... just for clarification purposes, copying your /home directory will not copy any applications that you installed via apt-get. The /home directory is really nothing more than a "My Documents" folder for most purposes.

---

### Post by Wobblybob on 2008-01-31
I've used this method to get the same pkgs on a newly installed o/s on a different PC. 1st collect the list of all the packages you have installed on your current PC so that you can re-install them on the other PC.

In a Terminal and type;

martin@linux:~$ dpkg --get-selections> pkglist

dpkg --get-selections reads all the software packages installed on your PC and > pkglist will make it create a document called pkglist in the current or Home Folder. Now save the list to removable storage to move it to the new PC.

save your pkglist to your Home Folder on the new PC, open a Terminal and type;

martin@linux:~$ sudo dpkg --set-selections < pkglist

This sets the list up ready to be installed, now type;

martin@linux:~$ apt-get dselect-upgrade

and follow the on screen prompts as they appear as you packages are loaded onto your PC in one go.

edited to include < pkglist at the end of sudo dpkg --set-selections, sorry about that.

---

### Post by Hoom@n on 2008-01-31
Thanks. The post #10 seems to be a very good idea. But again for this work I should copy that apt folder or no? (I think I sould copy that too. Am I right?)
+++
I have 256kb/s internet and I pay more than 60$/month and it's a really high speed in Iran. more than 95% of users in Iran are using 56kb/s internet. Plus Middle-East fiber optic has some problem made by a ship from yesterday and the speed is redused in hole middle east. AT&T said that they try to solve it by next 12 days!
___
Thanks.

---

### Post by zvacet on 2008-01-31
Install APTonCD from synaptic.That program will copy all your var/cache/apt/archives.Burn it on CD/DVD and put in other comp and install.

---

### Post by Wobblybob on 2008-02-02
sorry mate, my option only downloads the packages from the internet again, so I don't think thats gonna help you if you are paying for your connection.

---

