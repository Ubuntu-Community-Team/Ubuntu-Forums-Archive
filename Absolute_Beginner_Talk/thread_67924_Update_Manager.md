---
title: "Update Manager"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by The Hedgehog on 2005-09-21
My update-manager deleted Gaim and I cannot reinstall it!
But I want Gaim back.
I get this warning:
gaim:
  Depends: gaim-data (=1:1.4.0-1ubuntu1~5.04ubp1) but 1:1.1.4-1ubuntu4.4 is to be installed

---

### Post by PsyberOneZero on 2005-09-21
I remember readng somewhere (i'll try and find the post) that the hoary backports are down right now so it may take a little bit before you can get it back.

---

### Post by mlomker on 2005-09-21
If that's the case then you could temporarily remove the backports repository and allow your system to download the older version that came with Hoary.

---

### Post by The Hedgehog on 2005-09-21
If it is only temporarily, it won't be much of a problem.
But since I no expert I'll just wait till it is solved.

---

### Post by PsyberOneZero on 2005-09-21
I just looked around some other posts and I sounds like the backports site is back up, If you hit reload in synaptic do you get any errors about any files not found?

---

### Post by The Hedgehog on 2005-09-21
I get the same error message.

---

### Post by PsyberOneZero on 2005-09-21
Is the error during update or when you try to install.
It could be possible that the package maintaner goofed and set the wrong dependencies. :-x

---

### Post by The Hedgehog on 2005-09-21
When I check to box next to Gaim

---

### Post by PsyberOneZero on 2005-09-21
```
deb [http://acm.cs.umn.edu/ubp](http://acm.cs.umn.edu/ubp) hoary-backports main
```
try using this in the repo list

---

### Post by The Hedgehog on 2005-09-22
Still doesn't work

---

### Post by bored2k on 2005-09-22
[QUOTE=The Hedgehog]Still doesn't work[/QUOTE]
 Did you try reloading your sources ? If the problem persists, install it via autopackage: [http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download](http://prdownloads.sourceforge.net/gaim/gaim-1.5.0.x86.package?download)

---

### Post by The Hedgehog on 2005-09-22
The installation through autopackage worked.
Problem solved. Thank you very  much.

---

### Post by Mystery47 on 2005-09-22
Sometimes when i got similar problems....i solve those removing all crosses in repository list(and maybe i unistall package too, if necessary)....and then i install package. Thats because ubuntu see otherwise same package(and those in different versions) in many places....but u need just that one u want....

Im sorry about my bad english...but i hope u can understand what i mean...

 :wink: 

ps. This works fine with downloaded .deb files....and u get latest versions...

---

