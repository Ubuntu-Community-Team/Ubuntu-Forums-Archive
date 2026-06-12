---
title: "Uninstalling binaries"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2008-01-07
Hello, I need a little help uninstalling a program called noip so that I can reinstall it using synaptic.

Whats going on is that I have a FTP server I run thats on a dynamic IP. To counter the dynamic IP I use a program called NoIP Duc. For a while  I was un-aware that there was a package via apt-get and when I installed it using directions that weren't written for Debain based distro's I had to use "make" on some binaries in order to install the program.

Because the instructions weren't for Ubuntu, its instructions on how to get the program to start up on reboot didn't work for me. I ran across instructions on getting NoIP working in Ubuntu if its downloaded via apt-get, and I rather do it this way since its so much easier to manage programs via apt-get anyway. The problem is now, is that I have no idea  on how to get my 'make' to uninstall first so that I can reinstall with apt.

I apperciate any help :KS

**EDIT**: For clarification, here are the directions I used to install NoIP - [http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html](http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html)

---

### Post by Steveway on 2008-01-07
Go with a terminal in the folder that you used to compile the app and type:
sudo make uninstall
That should uninstall that application.
EDIT: Also remember kids, always use sudo checkinstall instead of sudo make install, so you'll get a nice .deb that can easily be installed and uninstalled.

---

### Post by Nexusx6 on 2008-01-07
]Tried it on the "binaries" folder, and the noip folder housing the binaries folder (among other things) itself.

> fox@TheLibrary:~/noip/noip-2.1.7/binaries$ sudo make uninstall
[sudo] password for fox:
make: *** No rule to make target `uninstall'.  Stop.
fox@TheLibrary:~/noip/noip-2.1.7/binaries$ cd ..
fox@TheLibrary:~/noip/noip-2.1.7$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
In case it helps:
```
fox@TheLibrary:~/noip/noip-2.1.7$ ls
binaries         LISEZMOI.ENPREMIER  README.FIRST           README.FIRST-SWE
COPYING          mac.osx.startup     README.FIRST.FRANCAIS  redhat.noip.sh
debian.noip2.sh  Makefile            README.FIRST.ITALIANO
gentoo.noip2.sh  noip2               README.FIRST.JAPANESE
LEEME.PRIMERO    noip2.c             README.FIRST.pt_BR

```

---

### Post by Steveway on 2008-01-07
Oh I see.
That just seem to be a few scripts.
Are you sure you actually installed that?
What did you do besides typing make in there?
If that was the only thing then just deleting that should do the trick.

---

### Post by Nexusx6 on 2008-01-07
I posted a link to the site I used to do the installation in an Edit in my OP, but I think the most relivant part to how I installed the program is in this quote

> If you didn't get an error while doing step five, skip this section and go to step six. If you got an error, all it means is your system doesn't have the software it needs to compile applications from their source code. The easiest way to use noip2 without compiling it from its sources is to use the binary file they give you. Type ls binaries to see the files in the binaries folder. There will probably be only one file listed. This is the filename you will use in the next command cp binaries/filename ./noip2 and once that's finished, you can type make install and head over to step six!

I followed the 'using binaries" steps"

Yup, I'm sure I installed it, its been working like it should most of this time; save for the whole not starting up on start up deal.

---

### Post by Steveway on 2008-01-07
Well, thats a pretty messed up guide.
I'm not sure how to revert all that stuff if sudo make uninstall doesn't work.
Apperantly just installing the same program from the repos should overwrite the old one. (Providing that directories etc haven't changed.)

---

### Post by Nexusx6 on 2008-01-07
I whole hardly agree =/ I felt the guide was pretty old and hadn't been updated in some time myself.

I'll try doing a repo install then, and hope that it overwrites. Thanks for your help :D

---

