---
title: "Where does Linux install things?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by AceRimmer on 2006-07-29
Hello.  I've been using Ubuntu since 6.06 came out and I really like it.  However I have one problem, I don't understand the filesystem.  When a package is installed I have no clue where it is putting files.  When I installed wine and then isntalled DVDShrink it worked at first, but now I can't find any of the DVDShrink files since I have no clue where it may have put them.  What is a good resource to help me understand the linux file system so I can understand how to really use Linux on my system.  I guess I look at it like a windows user and it is really different so I get frustrated.  I looked through the threads but didn't really see what I needed.   Thank you for any tips. 

P.S. the sys admin at my work showed me a command to find stuff, it was something like "Where"  He would type in "where wine" and it came back showing a path like \usr\lib\... or something like that.  I can't seem to get it to work so I think I'm messing the command name up.  

Thanks again.

---

### Post by taurus on 2006-07-29
Most likely will be in /bin or /usr/bin.  The command to find something is (if it's on your path)...

```

whereis <app>

```

---

### Post by Rumor on 2006-07-29
A very helpful "map" can be found here: [http://www.secguru.com/linux_file_structure](http://www.secguru.com/linux_file_structure)

---

### Post by Crosbie on 2006-07-29
Are you talking about installing it under Wine?  If so, I believe wine keeps things separately, in its own fake windows folder in your /home.

For native apps you fetch from repositories (using Synaptic etc) you don't really need to worry about it - since Synaptic will (fairly) reliably be able to remove it for you.  Most progs keep settings files in your /home directory... often in hidden folders starting with a '.'.  By default, you need to 'show hidden files' to see these in Nautilus.

---

### Post by Indras on 2006-07-29
A really handy thing to do is to open Synaptic Package Manager, find a package you've installed, right-click and go to properties.  One of the tabs at the top says "Installed Files" which will tell you every file that package put on your system and where.  This includes help files, executables, working directories, and occasionally config files (though many config files are created after the first time you run it).

---

### Post by shanepardue on 2006-07-29
i mostly use aptitude to install things, but if i'm ever installing something manually, i never know where to install it. i usually end up installing it to my home folder to avoid any problems, but if i ever went multi-user, i'd run into problems with other users trying to run those programs.

what should be my go-to folder for installing programs in that manner?

---

### Post by confused57 on 2006-07-29
I believe packages downloaded by SPM are in the file

/var/cache/apt/archives

I'm not sure exactly where they're installed to...

---

### Post by kinematic on 2006-07-29
if you mean installing form source you can put it in the /usr/local directory.
that's were thing get installed by default when installing from source.

---

### Post by shanepardue on 2006-07-29
> **kinematic said:**
> if you mean installing form source you can put it in the /usr/local directory.
that's were thing get installed by default when installing from source.
thank you! that's all i needed to know!

---

### Post by jonifen on 2006-07-29
try looking in /home/your_username/.wine/drive_c

that is your so called "C drive" for Windows/Wine.

---

### Post by az on 2006-07-29
Applications installed using wine are not really installed on your system.

Packages installed by any package manager frontend (Apt-get synaptic, apdetp, aptitude, dselect) are installed according to the filesystem hiarchy and you really don't need to fool around with them since that's the package manager's job.

dpkg -L (package) lists the contents of a package just like looking at the package in synaptic does.

Packages you install by compiling are apart from the package manager.  But it's a good idea to use checkinstall to build a deb package for it so that you can remove it using the package manager. 

Install checkinstall

then compile as usual but instead of running make install you run ckeckinstall.

---

### Post by AceRimmer on 2006-08-01
Thanks for the replies.

---

### Post by steve.horsley on 2006-08-01
> **kinematic said:**
> if you mean installing form source you can put it in the /usr/local directory.
that's were thing get installed by default when installing from source.

I tend to use /opt, mainly because it's easier to type.

---

