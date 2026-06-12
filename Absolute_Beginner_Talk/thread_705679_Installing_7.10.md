---
title: "Installing 7.10"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by henrywm on 2008-02-23
I tried to reinstall Ubuntu 7.10 in order to make a fresh start, but when I cannot make a disk which will work.

1) If I download the ISO on my Ubuntu computer, I receive an error at the end of the disk burn process.
2) If I download it on my Windows computer, and then run the Live CD on the Ubuntu computer and choose the default option to run or install Ubuntu, the screen has nothing but multi-colored vertical lines.

---

### Post by jflarm on 2008-02-23
Try starting the LiveCD with the safe graphics mode

---

### Post by steveneddy on 2008-02-23
Or you might try the alternate CD.

Just a suggestion.

---

### Post by henrywm on 2008-02-23
That worked. I am running the install now. Will installing in safe graphics mode affect my graphics settings after the install is done and when I am running from the new install on the hard drive?

This is a new problem. When I installed 7.10 the first time I did not have this problem. Strange.

---

### Post by shad0w_walker on 2008-02-23
Installing in safe graphics mode should only affect the install session. It's just there if you have a troublesome graphics card that requires some tweaking/closed drivers. It shouldn't make any difference to getting your graphics going normally after it is installed.

---

### Post by noMS4me on 2008-02-23
I had a similar situation and I ended up using a Windows OS disk to boot from, partition, formatted and then re-installed Ubuntu from a disk copied as image in Nero. I know a disk burned as a plain data disk from an ISO file does not work. Hope this at least gives you an option.

Steve

---

### Post by henrywm on 2008-02-24
During the installation process, I received the following message:
   "The security updates on security.ubuntu.com couldn't be accessed, so those updates will not be made available to you at this time. You should investigate this later
   "Commented out entries for security.ubuntu.com have been added to the /etc/apt/sources.list file."

What causes this, and how can I fix it?

---

### Post by angrboda on 2008-02-24
> "The security updates on security.ubuntu.com couldn't be accessed, so those updates will not be made available to you at this time...
This usually means that the connection to the server could not be established. Nothing to worry about. Once the system is running uncomment the entries in /etc/apt/sources.list or via synaptic and the problem should be solved.

---

