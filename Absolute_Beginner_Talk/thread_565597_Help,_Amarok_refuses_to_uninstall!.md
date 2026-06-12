---
title: "Help, Amarok refuses to uninstall!"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by stavaroti on 2007-10-02
Hi all,

I am a total noob at linux and would like to know how to remove amarok and all the kde dependencies installed with it.  I noticed that when installing amarok, it also installed a WHOLE bunch of kde libraries and dependencies and applications that i did not want appeared on the menu.  Anyway, i have to tried to unistall Amarok using the following without any luck:

Terminal
sudo apt-get remove amarok
sudo apt-get autoremove amarok
make uninstall (using a tarball source)

Add/Remove menu

Synaptic package manager

Update manager.

All of the above say that amarok is not installed but the application still shows up in the applications menu and starts normally as well.

Any help would be appreciated.

---

### Post by Kingsley on 2007-10-02
Remove amarok-xine also.

---

### Post by stavaroti on 2007-10-02
I still get the same message:

stavarotti@stavarotti-laptop:~/Desktop/usplash-fingerprint-sources$ sudo apt-get autoremove amarok-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package amarok-xine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Could amarok be installed anywhere that is hidden from these terminal commands?  Because ubuntu using either package managers or the terminal, says that amarok is not installed.  

Is there any other info you might need me to post that might making identifying the problem manageable?

---

### Post by jon zendatta on 2007-10-02
try

sudo apt-get remove --purge "file"

---

### Post by stavaroti on 2007-10-02
hmm,

That did not work either, amarok is still installed :(  

I tried to reinstall and the uninstall it via both apt-get and add/remove, but that did not work either.  Is there anyway to manually remove it, as one would by deleting folders and registry entries in windows?

---

### Post by andyanderso on 2007-10-02
Have you tried looking at the install history, finding out what was installed with amarok, then searching your file system for those files and then deleting them manually?

---

### Post by stavaroti on 2007-10-02
Sorry, but I am a total noob.  How do i go about looking at the history and removing stuff manually?

Thanks.

---

### Post by skyjacker on 2007-10-02
> **stavaroti said:**
> Sorry, but I am a total noob.  How do i go about looking at the history and removing stuff manually?

Thanks.  Type the following into terminal   [whereis amarok]. The files in amarok will be listed. go to each file and delete as necessary.

---

### Post by mysticmatrix on 2007-10-02
How did you install amorak in first place?

---

### Post by stavaroti on 2007-10-02
i installed amarok using the following command:

sudo apt-get install amarok

---

