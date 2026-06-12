---
title: "X Problem"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Absolute Zero on 2006-10-18
Hey all,
    I recently installed Breezy on a PC at work and after instaling I went into terminal and executed

```

 sudo apt-get update && apt-get upgrade

```

This executed, seemingly, flawless and I was prompted to restart Ubuntu.  After restart X tries to start but eventually fails and am presented with just a console.  

I investigated the error from X and it has to do with the kdb and mouse modules not being loaded? =\ 

Has anyone ever had this problem or a possible fix for it?  Everything was running fine and without error before I ran apt.

Thanks in advance everyone.

-Doug

---

### Post by taurus on 2006-10-18
From a prompt, type

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Absolute Zero on 2006-10-18
Taurus,
   Thanks for the response and I re-ran the X configurator but with the same problem.  

The error is that the modules kdb and mouse could not be loaded because no such module exists and then Fatal Error failed to load core devices.  

So, my best guess, is that X can't find the mouse and keyboard or somewhere during my apt-get update these files were changed somehow?

I am not real sure as I have done nothing to the File System outside of running the above command in the terminal.

---

### Post by Absolute Zero on 2006-10-19
I have solved this problem.  One of the other techs had changed the Repositories to point to Dapper and I wasn't aware of that.  

So when I did an update, the files were pulled from the dapper repositiories instead of Breezy; I upgraded the distro to Dapper through the Terminal and everything is working fine now!

---

