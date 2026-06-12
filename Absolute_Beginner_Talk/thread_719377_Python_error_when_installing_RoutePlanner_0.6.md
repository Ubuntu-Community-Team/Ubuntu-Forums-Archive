---
title: "Python error when installing RoutePlanner 0.6?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Optravis Prime on 2008-03-09
First off, I am brand new to Linux in general, and I'm having a bit of a rough time with it. I'm sure I'll learn eventually, but right now I really need some help.

Basically I'm trying to install RoutePlanner .06. When I downloaded the GNOME deb, it gave me this error while running it in the package installer (default):

Error: Dependency is not satisfiable: python-base

I did the following in terminal:
 sudo apt-get install routeplanner

And everything looked like it went off without a hitch. But there was a hitch: I can't find the program anywhere. It said it was also installing some python files (again, I'm a newb and can't remember which ones) and everything looked successful. But then I couldn't find the program, so I did the same thing in terminal, but it says it's already installed and at the current version. 

So, thinking that maybe the python problems had been resolved, I tried to download the deb again, but I get the same error. I also get a python-related error when I run the non-GNOME version.

Someone, please help?

Cheers.

---

### Post by EdThaSlayer on 2008-03-09
Don't worry too much. All that means is that you need to install python-base.
Just open up Synaptic Package Manager. You can get there through the System option and looking at the submenus there(I use KDE so I'm of no help here).  Then look for Python and download that via the synaptic package manager.

So the steps:
1. Open up Synaptic Package manager
2. Search for Python
3. Install Python

it should work afterwards. If you get any of those type of errors just look them up in Synaptic Package Manager.

[EDIT] I might have misunderstood the question. All you have to do is go to the terminal and type in "routeplanner" and the program should pop up.

---

### Post by Optravis Prime on 2008-03-09
You didn't read the question wrong. I have tried typing routeplanner in terminal to no avail. I have searched for it, and looked for it as installed in the package manager. It's not there anywhere.

Python is also already installed, yet I get above error.

I appreciate the input, but unfortunately I'm still stuck in the same place.

---

### Post by glennric on 2008-03-12
> **Optravis Prime said:**
> You didn't read the question wrong. I have tried typing routeplanner in terminal to no avail. I have searched for it, and looked for it as installed in the package manager. It's not there anywhere.

Python is also already installed, yet I get above error.

I appreciate the input, but unfortunately I'm still stuck in the same place.

Just because python is installed does not mean that python-base is installed.  Are you sure that the package python-base is installed?

---

