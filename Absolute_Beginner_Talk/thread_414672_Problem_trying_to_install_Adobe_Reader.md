---
title: "Problem trying to install Adobe Reader"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-20
I downloaded Adobe Reader 7.0 for Linux. I untared the file to my desktop. Tried the sudo aptitude install command several different ways and keeps telling me it can't find it, even though it's right there on the desktop. Please look at the snapshot and tell me what I'm doing wrong. Thanks.

---

### Post by Famicommie on 2007-04-20
Heh, see, Aptitude only installs precompiled binaries which are located in the repositories. You can't just tell Aptitude "Hey look, install this file I've downloaded!" In order to install the Adobe Reader that you just downloaded, you will most likely have to compile it from source. There are a number of ways that programs can be compiled, the folder should have a file called "README" that elucidates on the method you would use.

However, it -is- possible to skip compiling and simply use aptitude to install adobe reader. It won't work right now (heavy server load due to the release of Feisty), but when you get a chance open up a terminal and paste the following into it:
```
sudo aptitude install acroread mozilla-acroread
```

---

### Post by jacatone on 2007-04-20
Precompiled binaries? That's something I need to learn about. I have been able to install a few programs using Aptitude that I got from Sourceforge. How would I tell if a program is precompiled or not? Also, can you use Synaptic PM to find a program, download and then install it? Thanks.

---

### Post by starcraft.man on 2007-04-20
Yes, you can search Synaptic from the terminal the command you want to use is:

```
sudo aptitude search X
```

Just replace the large X with the term you'd like to search, like if you try "acro" you'll see most of the versions of reader and addons you can install.

Then you just pick off which things in the list you want and type like above... x y and z are the EXACT names that appeared in your search. You can install as many programs as you like all at once this way.

```
sudo aptitude install x y z
```

As for how this all works its not too complicated. Read [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") page, I think it explains it very well. And most of the Feisty stuff applies to any version your using.

---

### Post by Famicommie on 2007-04-20
> **jacatone said:**
> Precompiled binaries? That's something I need to learn about. I have been able to install a few programs using Aptitude that I got from Sourceforge. How would I tell if a program is precompiled or not? Also, can you use Synaptic PM to find a program, download and then install it? Thanks.

A precompiled binary is the program and its necessary pieces. Think of it as the Windows version of an .exe file. See, linux programmers don't really do the whole graphical installation thing. Instead they will write the program in a high level language (called source code), and from the terminal the end user will compile it into a lower level language that the computer itself can run (called object code). By using something called "flags" users are able to tailor what they are compiling to their very specific needs.

Synaptic/Aptitude work by connecting to servers defined by your sources.lst file, querying for the product you have asked to install, and then sending the data to your system and placing the appropriate pieces into the appropriate directories. The reason that you are able to download something from sourceforge and then install it with Synaptic/Aptitude is not because they are able to see it on your computer, but because it is coincidentally also located in the repositories. If you had downloaded something that wasn't in the repositories then you wouldn't have been able to install it with Synaptic/Aptitude. Basically, I am saying that so far you have been pretty lucky! Synaptic/Aptitude do not install anything from anywhere on your computer.

If you open up Synaptic Package Manager (System->Administration->Synaptic Package Manager) you will notice that there are quite a few categories of programs/libraries, and that at the top you also have a search function. For instance, if you do a search for Adobe, then you should see a number of packages such as "acroread" in the results. For more information about repositories, [look here](https://help.ubuntu.com/community/Repositories).

---

### Post by jacatone on 2007-04-20
So the programs listed in Synaptic are already on my HDD waiting to be selected and installed? Say I found a program that wasn't listed, how would I use Synaptic to go to a repository and download it. I'm on dialup, does SPM have a resume feature like most download managers? Thanks.

---

### Post by Famicommie on 2007-04-21
> **jacatone said:**
> So the programs listed in Synaptic are already on my HDD waiting to be selected and installed? Say I found a program that wasn't listed, how would I use Synaptic to go to a repository and download it. I'm on dialup, does SPM have a resume feature like most download managers? Thanks.

No, the programs that are listed in Synaptic are on Ubuntu's servers. Synaptic is simply the go-between; it asks the servers for the pieces that you want, and then places them in the appropriate places.

If you find a program that you want which isn't in Synapitc, then you have to compile it or look for a debian package (the extension will be .deb). Debian packages are installed simply by double clicking them.

I am not sure if SPM has a resume feature, as I have been spoiled with broadband for several years.

---

