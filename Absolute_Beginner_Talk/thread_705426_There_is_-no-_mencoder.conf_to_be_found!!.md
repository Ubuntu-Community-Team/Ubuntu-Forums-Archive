---
title: "There is -no- mencoder.conf to be found?!?!"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by locoHost on 2008-02-23
In terminal I type: 

       find / mencoder.conf 

and after it traverses every single folder on every drive, I get nothing. 

I have the newest mplayer. Where is this file?

Thanks for your help :-)

---

### Post by taurus on 2008-02-23
Are you having a problem with codec?  Have you installed the ubuntu-restricted-extras package?

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
What exactly are you trying to do anyway?

---

### Post by happyhamster on 2008-02-23
Is mencoder installed? (It's a separate package from mplayer.)

---

### Post by oldos2er on 2008-02-23
I'm sure you can create one yourself. If you type "man mencoder" in a terminal, it shows you a sample mencoder.conf .

---

### Post by locoHost on 2008-02-23
Running Mythbuntu 7.10. I've slowly muscled through most everything so far. With help from here of course ;-)

I'm using AcidRip to rip my DVDs. It's working great but I want to change the default paths in the GUI. Is that in the 
mencoder.conf? Or another conf? I'm still learning.

Thanks everyone :-)

---

