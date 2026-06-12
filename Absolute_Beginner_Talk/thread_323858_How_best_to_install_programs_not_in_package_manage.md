---
title: "How best to install programs not in package manager"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by txtinman on 2006-12-22
I'm new to Ubuntu, but not to Linux. What is the best method of installing programs that are not listed in the package manager?

---

### Post by Hendrixski on 2006-12-22
There's a few ways.

You can find a .deb file and depackage it.  That's essentially what the package manager does under the hood.  You can also use RPM's, though on a debian-based distribution like Ubuntu you need a program like Alien.  You can get Alien from the package manager.

This will most likely involve the command line.  Though, if there are tools to do this graphicly I would be interested to know of their existence, so I can teach them to new Linux users who don't love the command line the way I do.... It's a holdover from my UNIX days.

---

### Post by Antarctica on 2006-12-22
What about compiling from source?

---

### Post by FenrisAbraxas on 2006-12-22
> **Antarctica said:**
> What about compiling from source?

When you compile from source, and as you said you are not new to linux but to ubuntu, you have to get the tarball download it then:

```

#tar -xvzf package.tgz 
#./configure
#make
#make install

```

Also you have to install all the packages the program depends, you can use the package manager to solve it tho.

Hope that helps (and read the notes in the package for ./configure options :P).

---

### Post by txtinman on 2006-12-23
Here's an example of what I've tried. I found a .deb file for Bluefish, my favorite html editor, on its web site. The instruction there said to issue these commands: apt-get install bluefish and the program would be installed. I did that from the command line and the error message said the file could not be found. Do I have to download the .deb file to some specific folder on my computer so apt-get can find it?

---

### Post by davidU on 2006-12-23
> **Hendrixski said:**
> There's a few ways.

You can find a .deb file and depackage it.  That's essentially what the package manager does under the hood.  You can also use RPM's, though on a debian-based distribution like Ubuntu you need a program like Alien.  You can get Alien from the package manager.

This will most likely involve the command line.  Though, if there are tools to do this graphicly I would be interested to know of their existence, so I can teach them to new Linux users who don't love the command line the way I do.... It's a holdover from my UNIX days.

Hi,
  your answer sounds promising but for a post in the absolute beginners forum, I have to say you lost me on line one.  Forgive me, I am a MS Windows slave and Unix speak is problematic. 

I've installed Ubuntu v.6.06-386 on my laptop, and discovered that with this version there is no "gparted" as there was (?) with v.5.04.

So I've downloaded the "tarball" to the desktop, but I don't have any idea where to put the contents so that synaptic can find whatever it requires.

Can you help please ?

I also would like to run a firewall, and would like to know if I follow the same procedure to  install it.

Regards

DavidU:)

---

### Post by jvc26 on 2006-12-23
Have you looked at the [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) guide to installing on ubuntu? I found it pretty useful working out the different methods for installing things on ubuntu.
Il

---

### Post by jvc26 on 2006-12-23
> **txtinman said:**
> Here's an example of what I've tried. I found a .deb file for Bluefish, my favorite html editor, on its web site. The instruction there said to issue these commands: apt-get install bluefish and the program would be installed. I did that from the command line and the error message said the file could not be found. Do I have to download the .deb file to some specific folder on my computer so apt-get can find it?

To apt-get it you will need to have the other repositories enabled for it to work. Apologies for double posting I hadnt noticed the question above.

To add the other repos to allow the apt-get to install the bluefish follow the guide here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Then in terminal
```

sudo apt-get update
sudo apt-get install bluefish

```

and that should sort you out. To install from the .deb file, merely rightclick on the file on your desktop, go to permissions, allow executing (tick the box) then close that and double click on the file and it should install.
Il

---

### Post by sharperguy on 2006-12-23
> **Illuvator said:**
> 
To add the other repos to allow the apt-get to install the bluefish follow the guide here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)


Actually since you are using 6.06, then go here [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_apt-get_the_easy_way_.28Synaptic.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_apt-get_the_easy_way_.28Synaptic.29)

This is also the synaptic way which is more user friendly.

What you are doing is basically pointing the Package Manager at another database (repository) where it can get access to much more software.

There are also unofficial repositories created - sometimes for specific purposes (ie: the beryl-svn repository which gives you the bleeding-edge version of beryl).

In the latest release of Ubuntu, 6.10 - Edgy Eft, this process is further simplified.

You may also want to try the add/remove application as a more user friendly alternative to synaptic (although I haven't used the dapper version).

You can access it by clicking applications > add/remove

---

### Post by txtinman on 2006-12-23
Thanks for the help guys. I think I've got it figured out now. I've been using Gentoo for three years now and this distro gives me different ways to do things.

---

### Post by sharperguy on 2006-12-25
lol thats a big change

And unexpected from what I've heard of gentoo users :P

---

### Post by TooRight on 2006-12-25
Welcome to Ubuntu!! :D

Automatix is also a handy tool to get alot of finicky stuff installed (java, flash, audio and video codecs)

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by MkfIbK7a on 2006-12-25
the forum staff are always saying to go to [HOW TO INSTALL ANYTHING IN UBUNTU]("http://monkeyblog.org/ubuntu/installing/") when someone has a problem.

---

### Post by MkfIbK7a on 2006-12-25
sorry luvator didnt see your previous post

---

