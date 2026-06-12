---
title: "re-installing ubuntu"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by wenasoga on 2008-01-02
I'm wondering if I can re-install Gutsy over an existing "buggy" install of same without altering any of the files I have created.  Will it just overwrite the existing install?   Thanks

---

### Post by drascus on 2008-01-02
first of all make note of all the programs that were installed other than the ones that come with ubuntu natively. Second go to the home folder and type ctrl+h to show all the hidden files. Back up the entire home folders files except the loced ones in the examples folder. By back up I mean just cut and paste them into some sort of removable media. Then reinstall ubuntu and copy all the files back into the home folder. (Note: any directory you save hidden files in will need the ctrl+h command to reveal them) Then you need to reinstall the programs you noted and everything should be fine. 

I think there might be an easier way to do it. but the above method has worked for me in the past.

---

### Post by erfahren on 2008-01-02
if you don't have a seperate /home partition, then no.

you could .zip up the files (including hidden files) in your /home directory so you can replace them later.

most (maybe all) programs store their configuration files in your /home/<username> directory, and don't create their folders until you first launch them,

I reinstall every so often, and when I do I just stick ~/.mozilla (for example) folder that I have saved back into my /home/<username> so when I first launch Firefox evrything is already set the way I want it,

the more you get the hang of what the files are for, the less you need to configure on a fresh install.

The other thing you can do is back up the packages you have downloaded using Synaptic, (Add/Remove Programs), or apt (as long as you haven't cleared the cache). They are kept in /var/cache/apt/archives

you can really just browse to there and copy the packages (as a normal user) and paste them somewhere to copy them to a CD or whatever. Then to replace them on the new install just do "sudo nautilus" to open the file browser as root, browse to that directory and paste them in there.

so then on a fresh install you don't have to download them again, Synaptic or apt will check for updated versions, and if there are none, it will just use the archived packages to install.

---

### Post by wenasoga on 2008-01-02
Thanks for the help.  Fortunately, this is a pretty recent install and I haven't had time to add many apps.

---

### Post by erfahren on 2008-01-02
> **wenasoga said:**
> Thanks for the help.  Fortunately, this is a pretty recent install and I haven't had time to add many apps.
reinstalling after the first few days is all part of the Linux newbie experience .... trust me on that. lol !

---

