---
title: "I'm a little stuck on on how to install this program."
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Ithyn on 2007-07-20
I thought I understood how to install programs from source, but something came up when I tried to install a program and I'm not sure what to do to satisfy the requirement.  I ran ./configure after extracting the source from the tarball and moving into the new directory, and I received the following message:

```
The msgfmt command is required to build libpurple.  If it is installed in your system, ensure that it is in your path.  If it is not, install GNU gettext to continue. 
```

When I attempt to install something and I'm told that I need to install something else, such as in this case, where would I look for it to download or install onto my system if the site that the source came from does not have such a download available?

---

### Post by avik on 2007-07-20
Well, it says to install gettext, which is available in the repos as gettext:

```
sudo apt-get install gettext
```

However, it is already installed on my computer.

You can search for any package in the repos using synaptic, which is found in System->Administration->Synaptic Package Manager.

---

### Post by Ithyn on 2007-07-20
So anytime a program requires me to install something like that, I can find and install it with apt-get?

---

### Post by kevinlyfellow on 2007-07-20
Every once and a while when compiling something it will say things like "file foobar.ko.2 not found" or in your case the program msgfmt.  A handy application to use is apt-file, which will search for packages that has the file you need.  It is available in the repos

You can get almost anything you need with apt-get, including developer packages (they are labeled with the suffix -dev)

---

### Post by Ithyn on 2007-07-20
Thanks for the help.  It seems at this point my problems are more often missing pieces to the puzzle than missing the whole picture.

---

### Post by avik on 2007-07-21
> **Ithyn said:**
> Thanks for the help.  It seems at this point my problems are more often missing pieces to the puzzle than missing the whole picture.

That's the problem with installing from source: dependency hell.  But if you install using apt (apt-get, Synaptic, Add/Remove Applications, etc.), then all the dependencies are marked and automatically installed.  For that reason, you'll want to see if you can get the program you want in Add/Remove or in Synaptic, or at least available somewhere as a .deb file.  Installing from source is a last resort.

---

### Post by por100pre1 on 2007-07-21
This seems to be related to Pidgin, to have a Pidgin package available in the repos would have resolved this issue already!

---

### Post by pyros on 2007-07-21
> **Ithyn said:**
> Thanks for the help.  It seems at this point my problems are more often missing pieces to the puzzle than missing the whole picture.

If I am correct, you are trying to compile pidgin? If you are trying to compile something that is already in the repos, you can often use the command "apt-get build-dep PACKAGENAME" to install the build dependancies. In this case (assuming I was correct), you could try running "apt-get build-dep gaim"

---

