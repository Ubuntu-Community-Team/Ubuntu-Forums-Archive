---
title: "Problems installing Restricted Formates."
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-08-15
I am attempting to follow the instruction layed out on the Wiki page

[Installing_Restricted_Formats]("http://knowledge76.com/index.php/Installing_Restricted_Formats")
However one instruction does not seem to want to work.
> sudo /usr/share/doc/libdvdread3/examples/install-css.sh
It returns the following.
> ed100@ed100-desktop:~$ sudo /usr/share/doc/libdvdread3/examples/install-css.sh
Password:
sudo: /usr/share/doc/libdvdread3/examples/install-css.sh: command not found


I have looked into the folder describe but there is no **install-css.sh** however there was one in the folder /usr/share/doc/libdvdread3/install-css.sh. 
I edited the instructions to reflect this but is still did not work.
> ed100@ed100-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found

I also tryed to copy the folder to the **examples folder**, then running it but that returned the same error.

What command is not being found? And how do I get it to find it?

---

### Post by foolsh on 2006-08-15
sudo: should only be sudo without a :

---

### Post by benuski on 2006-08-15
Hm.  I did this last night and it worked just fine for me.  Maybe try reinstalling the libdvdread3 package and then trying whats in Wiki again.  The only other idea I have is that maybe it somehow depends on some other package (unlikely, I know), so maybe try installing the rest of the restricted formats, including the Windows codecs?

Oh, and are you using x86 or AMD-64?  Because if you're using AMD, there are a couple of packages that the restricted formats page lists that you would need before trying to install the package.  But you prolly would have noticed that.

Hope you figure it out.

---

### Post by givré on 2006-08-15
if you found install-css.sh in /usr/share/doc/libdvdread3/ just go in this directory and launch it :
```
cd /usr/share/doc/libdvdread3/
ls #to be sure that it's there
sudo ./install-css.sh
```

---

### Post by gargoyle on 2006-08-15
To givré,
Sorry you suggestion did not work, got the same result. Here is what happened.
> ed100@ed100-desktop:~$ cd /usr/share/doc/libdvdread3/
ed100@ed100-desktop:/usr/share/doc/libdvdread3$ ls #
changelog.Debian.gz  install-css.sh    README.Debian.fr  TODO
changelog.gz         README.Debian     README.Debian.it
copyright            README.Debian.de  README.Debian.sv
ed100@ed100-desktop:/usr/share/doc/libdvdread3$ sudo ./install-css.sh
Password:
sudo: ./install-css.sh: command not found

I tryed the easy solution next is the harder on like **benuski** suggested and reinstall the **libdvdread3**, and see if this works.
Please explain what command is not being found??

---

### Post by givré on 2006-08-16
ok i see the problem. When you want to execute a file which is not executable, bash return command not found.
If you want to execute it, you'll to make it executable.
```
sudo chmod u+x install-css.sh
```
and try it again.

But it strange that you have to do all that to get it working. Try to reinstall it before...

---

### Post by gargoyle on 2006-08-16
To givré,
I am not sure what was supposed to happen but here is the terminal output
> ed100@ed100-desktop:~$ sudo chmod u+x install-css.sh
Password:
chmod: cannot access `install-css.sh': No such file or directory
ed100@ed100-desktop:~$ cd /usr/share/doc/libdvdread3/
ed100@ed100-desktop:/usr/share/doc/libdvdread3$ ls #
changelog.Debian.gz  install-css.sh    README.Debian.fr  TODO
changelog.gz         README.Debian     README.Debian.it
copyright            README.Debian.de  README.Debian.sv
ed100@ed100-desktop:/usr/share/doc/libdvdread3$ sudo chmod u+x install-css.sh
ed100@ed100-desktop:/usr/share/doc/libdvdread3$ sudo /install-css.sh
sudo: /install-css.sh: command not found


As I said not sure what was supposed to happen, **so what was supposed to happen???**

Is there a difference between remove and reinstall and just reinstall? Because I used Synaptic and I choose Reinstall.

Where I go from here. It seem like something is still missing, got any ideas?

---

### Post by foolsh on 2006-08-16
try it with the path just to be sure

sudo chmod u+x /usr/share/doc/libdvdread3/install-css.sh

---

### Post by gargoyle on 2006-08-16
I might have found my problem.
I may not have all of the dependies loaded.
On the home page for [K9copy]("http://k9copy.sourceforge.net/") it lists dependencies , I am in the process of check if I have fufilled the Prerequisite for it.

I will get back after I have check it out.
Thanks for the help.

---

### Post by gargoyle on 2006-08-16
Well it is not going good fufilling the dependences. using Synaptic, it does not seem to find all the files need.

1) DVDAuthor I get a waring box with 4 catagories.
**Not Authenticated**
6 items liste
**To be removed**
1 item listed
**To be installed**
12 item listed
**To be upgrade**
1 item listed

Sorry to say but it just does not seem worth while to go through all of this. I sorry to say I will just have to stick with my WinXp DvdShrink. 

Yes I know I could use Wine but why bother when DvdShrink works well in WinXp.

I would like thank all of you who attempted to help however it seems like I do not have the patience to try and get this going.
I have spent 2 days trying to resolve this program and still nothing may I give it a try in the future but I am to frustrated to continue now.  

Thanks again for trying to help.

---

