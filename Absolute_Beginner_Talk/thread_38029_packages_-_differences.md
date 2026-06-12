---
title: "packages - differences"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by pravit on 2005-05-29
I'm a bit confused about the differences between stuff I get using the Synaptic package manager and stuff I download. For example nethack usually makes a directory /usr/games/lib/nethackdir, but the one I installed with Synaptic doesn't, and I don't know where to find the readmes. I also installed XMMS with Synaptic and I can't figure out where it put the skin directory - the two directories referenced in the XMMS manual are nowhere to be found. Where can I find documentation specific to package releases? In fact, where do I find documentation for package-installed stuff at all, besides on the net?

Another thing - could anyone tell me how to get colors working in nethack? I installed it with Synaptic(this one had colors), then uninstalled it(couldn't find the readmes and stuff), then installed the package from nethack.org, then uninstalled that, then reinstalled it with Synaptic, and now I don't have colors anymore.  :| It's urgent - being able to tell the difference between a brown 'q' and a gray 'q' could save my life!
EDIT: figured it out - added "colors" to my .nethackrc

---

### Post by tread on 2005-05-29
When you install a package using synaptic, you can right-click the package and view the installed files list.

---

### Post by pravit on 2005-05-29
OK, here's the thing. All these docs are telling me to look for some certain files in ~/.xmms or ~/.thunderbird. If I want to get to these directories, I type cd /.xmms or cd /.thunderbird, right? Apparently, they weren't created, and I don't know where to look for the profile(I did muddle around in some of the stuff it listed it installed, but there's just so much of it).

---

### Post by tread on 2005-05-29
They are telling you to modify the files/folders in your home directory

1. start a terminal
2. type 'cd' .This brings you to your home directory
3. then type 'cd .xmms' etc.

Alternately, you can type 'cd ~/.xmms' in the terminal from any directory and that will take you to the .xmms directory in your home.

---

### Post by jobezone on 2005-05-29
Also, all the docs for packages you install using apt (apt-get or synaptics) are placed in
/usr/share/doc/<name_of_package_or_application>

If you find a file called README.Debian inside the program's documentation directory, start by reading it. These usually contain instructions, explanations and tips on the application, especially how it relates and is configured in a Debian system (which Ubuntu is a derivate of).

---

### Post by pravit on 2005-05-29
Thank you, guys! I feel silly now :D

---

