---
title: "play mp3"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-03-31
i cant play mp3... and in the add/remove i click on the gstreamer so it will install and then it says i need to confirm and then reload with internet but bothing happens iit wont install

---

### Post by chucky chuckaluck on 2008-03-31
you need to install the *restricted-extras* package.

---

### Post by Tomatz on 2008-03-31
> **chucky chuckaluck said:**
> you need to install the *restricted-extras* package.

Yeah use synaptic for this :)

---

### Post by stchman on 2008-03-31
> **patchido said:**
> i cant play mp3... and in the add/remove i click on the gstreamer so it will install and then it says i need to confirm and then reload with internet but bothing happens iit wont install

This will do it:

[http://www.stchman.com/codecs.html](http://www.stchman.com/codecs.html)

---

### Post by gobbles414 on 2008-03-31
> **Tomatz said:**
> Yeah use synaptic for this :)

I believe that the *restricted-extras* packages are also available in Add/Remove. My Add/Remove is set to *All Available Applications* or whatever in the drop-down menu. But, I don't think that's even necessary in this case.

---

### Post by patchido on 2008-03-31
i cant do that....i have restricted drivers manager installed but asked me the cd... i cant install the extras happens the same thing

---

### Post by gobbles414 on 2008-03-31
> **patchido said:**
> i cant do that....i have restricted drivers manager installed but asked me the cd... i cant install the extras happens the same thing

Go *System => Administration => Software Sources*. Now, remove the checkmark from the CD area at the bottom of the window. Examine the rest of the Software Sources control panel to make sure that the settings are what you'd like to use. You should now be able to install software in Ubuntu. EDIT: I have found that Ubuntu asking for the CD is caused by a bug. The workaround is to be connected to the internet while you're installing Ubuntu from the LiveCD. It'll be interesting to see if Ubuntu 8.04 still has this bug.

---

