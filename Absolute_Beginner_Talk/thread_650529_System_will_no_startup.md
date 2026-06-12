---
title: "System will no startup"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by service@vernoncomputers on 2007-12-26
I have installed the free 2 user version of Userful on my system. After install it auto reboots. When it rebooted it never completes the startup process. It gets to a point then just re boots over and over

---

### Post by Cypher on 2007-12-26
"Free 2 user vesrion of Userful"..could you elaborate more on what that is?

How far does it exactly get? If the Ubuntu progress bar is show up, then you can modify the boot options in GRUB to remove the "splash quiet" options to get a text output of what's really happening during the boot that might be failing..

---

### Post by service@vernoncomputers on 2007-12-26
There is a Ubuntu progress bar then it changes to a bunch of command lines then it states it is shutting down a bunch of stuff the it reboots and will do the same thing over and over. Can I remove the program from the prompt? I can get to the prompt but do not know what to do from there. Or how do I remove Userful from the stratup list then I can remove it from the GUI interface which I am more familiar with

---

### Post by Cypher on 2007-12-26
Ahh..I didn't know Userful was an application..D'oh..OK, get into the Command prompt by choosing the Recovery Console option in the GRUB menu, once at the command prompt remove Userful with
```

apt-get remove userful

```
I'm, of course, assuming that the package is called "userful". If that doesn't work, you can search for it by doing
```

dpkg -l | grep  user

```

---

### Post by service@vernoncomputers on 2007-12-26
thanks for working with me on this. I am not sure what the exact name of the installation file is. I will try to find it. How do I get at the start up list and remove the program from starting? A slight panic on my part as this system has all my photos of our recient trip which included a wedding perposal. If I loose those I might get a devorce instead of a wedding

---

### Post by service@vernoncomputers on 2007-12-26
I finaly fixed it. The program is called Userful but the application file is called desktop-multiplier which I was able to remove with the sudo apt-get remove command and now my system starts up normaly

---

### Post by service@vernoncomputers on 2007-12-26
How do I change this post to Solved? I can not see any link to change the post

---

### Post by philinux on 2007-12-26
look for thread tools on the webpage

---

### Post by overdrank on 2007-12-26
> **service@vernoncomputers said:**
> How do I change this post to Solved? I can not see any link to change the post

HI and it is under thread tools in the right hand corner.
Edit to slow again :(

---

