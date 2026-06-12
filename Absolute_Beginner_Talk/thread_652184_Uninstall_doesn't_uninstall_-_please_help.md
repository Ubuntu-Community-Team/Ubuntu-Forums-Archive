---
title: "Uninstall doesn't uninstall - please help"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by quadrantids on 2007-12-28
Using Synaptic I installed Kubuntu Desktop. After playing around I decided to return to Ubuntu by uninstalling Kubuntu Desktop through Synaptic. The trouble is that Synaptic doesn't uninstall all the 251 (or so) components it installed for Kubuntu Desktop, which leaves my Ubuntu system cluttered.

As far as I can see there is no "restore" function as in Windows XP.

Do I have to do a clean install?

Thanks in advance

---

### Post by zipperback on 2007-12-28
> **quadrantids said:**
> Using Synaptic I installed Kubuntu Desktop. After playing around I decided to return to Ubuntu by uninstalling Kubuntu Desktop through Synaptic. The trouble is that Synaptic doesn't uninstall all the 251 (or so) components it installed for Kubuntu Desktop, which leaves my Ubuntu system cluttered.

As far as I can see there is no "restore" function as in Windows XP.

Do I have to do a clean install?

Thanks in advance


Did you run a system wide backup before running the installation of the Kubuntu desktop? If so then you should be able to restore it from that. 

However, Linux isn't Window$, so things shouldn't be expected to work the same way.


- zipperback :KS

---

### Post by jken146 on 2007-12-28
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Herman on 2007-12-28
Well, you could try 'sudo apt-get remove', that normally does the trick for me. I haven't actually tried it out on an entire desktop, but I know it works well for most applications.
```
sudo apt-get remove kubuntu-desktop
```That should remove it from the operating system, at least functionality-wise.

There will still be a big collection of left-over packages for it and all the other software you have ever installed, all stored faithfully in /var/apt/cache/archives
All the packages are stored there so if you change your mind and decide to re-install them again later, they won't need to be re-downloaded from the internet.
I actually leave mine all there and even make a backup folder and save them in that as well. 
I copy mine to the /var/apt/cache/archives directories of my other Ubuntu computers with the same version of Ubuntu in them too. 
That's better than downloading the same packages again for each computer, it saves me a lot of bandwidth.

Most people won't need the original package again once the software has been installed. They get superceded anyway, so maybe they aren't worth keeping for most people, especially if you only have one computer.
If you're low on disk space and you can just empty your /var/apt/cache/archives directory this way,
```
sudo apt-get clean
```That will clean out your accumulation of  already used packages in your computer and give you back some hard disk space. 

Regards, Herman :)

---

### Post by quadrantids on 2007-12-28
> **jken146 said:**
> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

That was the most succinct and effective piece of computer help I've ever come across: thanks!

---

