---
title: "ndiswrapper"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-14
Hi,

I'm installing (or trying to) ndiswrapper.

under the install help \page it asks me to run :

ls /lib/modules/'uname -r'/build 

and says there should be install and a .config file as a prerequisite.

I have the 1st bit but not the second. How do I get the .config file???

Without it I get a large list of errors about warning and files not there.

Can anyone help or give me a step by step guide please.

Thanks

---

### Post by joshrobinson on 2008-03-14
hmm ive never had to do any of that, i download the source code, extract it, and run the following commands

```
make distclean
```
then
```
make
```
and last
```
sudo make install
```

and that does the job for me

note you might have to install some packages to need to build the program

---

### Post by the beak on 2008-03-14
I had to download it from another PC and move it over as it's not on the net. would that cause any difficulties?

---

### Post by the beak on 2008-03-14
What packages ? and how could I check if I had them?

Thanks for your quick response

---

### Post by joshrobinson on 2008-03-14
> **the beak said:**
> I had to download it from another PC and move it over as it's not on the net. would that cause any difficulties?

na just copy the tarball (tar.gz) file to your ubuntu desktop, extract it and go from there

---

### Post by the beak on 2008-03-14
Same errors I'm afraid.

It gets to 'module2' then falls over!? do you have a hunch over what apps I may be missing.

P.s. what does make distclean do?

---

### Post by joshrobinson on 2008-03-14
> **the beak said:**
> Same errors I'm afraid.

It gets to 'module2' then falls over!? do you have a hunch over what apps I may be missing.

P.s. what does make distclean do?

could you post the terminal output of what happens when you type make distclean?

---

### Post by joshrobinson on 2008-03-14
make distlcean cleans the make files for ndiswrapper, and makes sure that the install location is clear of old files

sorry my post above is missing a step the make command after make distclean, i will edit that

---

### Post by the beak on 2008-03-14
error: stdlib : No such Directory


and the same for 

stdio.h
stdlib.h
errno.h
string.h
........
ctype.h
dirent.h


and loads more!

---

### Post by joshrobinson on 2008-03-14
are you able to hook your computer up to a wired network and get online? your going to need to update and download some packages

you need to install build-essential, and your kernel headers

or use the version of ndiswrapper in the repo's

```
sudo apt-get install ndisgtk
```
this will install ndiswrapper, and a graphical frontend

ive always compiled my own though

---

