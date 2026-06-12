---
title: "Install update problems"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by dazziec on 2006-11-21
I Have just tried to update my computer because i now have 11 updates to install but all i am getting is an error message?

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

any ideas how i can get round this

thanks

daz

---

### Post by jstueve on 2006-11-21
Applications>Accessories>Terminal
```
sudo dpkg --configure -a
```
If it fails, cut&paste the output of the command to this thread.

---

### Post by lonniehenry on 2006-11-21
I have similar problem and my output to  sudo dpkg --configure -a     is sudo: dpkg: command not found 
What is next to solve problem?  synaptic give similar results.
Thanks

---

### Post by dazziec on 2006-11-22
I have done that but now i have got this message...
E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory


argghh..what is happening..its like XP all over again

---

