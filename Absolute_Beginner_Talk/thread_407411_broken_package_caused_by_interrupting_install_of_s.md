---
title: "broken package caused by interrupting install of sun-java5-bin"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by poscogrubb on 2007-04-12
Uh oh.

I'm not new to Linux, but I am new to Linux system administration. I just installed Xubuntu 6.10 on an old Thinkpad T22 and everything was working fine. Even got a Windows share mounted so that Amarok could play MP3s from my Windows PC. Feeling bold, I went poking around the Synaptics Package Manager to see what other useful software I could install.

Sun Java 5 Run-time Environment caught my eye. So I selected it and applied the changes. The normal Synaptic install dialog appeared, showing the install details. During install of sun-java5-bin, the install details showed a text-screen dialog asking for agreement to licensing, I think, with a text OK button. Since this screen was INSIDE the Synaptic install progress dialog, I couldn't interact with the text terminal. The install was stuck, waiting for me to agree to the license terms.

I panicked. I couldn't figure out how to get to that OK button. So I opened up a terminal and killed dpkg.

There were some error messages in Synaptic, but the install procedure aborted and I was able to close Synaptic.

Of course, later when I opened Synaptic again, it reported one broken package, sun-java5-bin. I tried to remove it completely; the output :

```
dpkg: error processing sun-java5-bin (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 sun-java5-bin

```

Now what?  I can't install anything else until this broken package is fixed... How do I install it correctly or remove it completely?

Thanks in advance for your time.

---

### Post by Bias on 2007-04-12
Try opening synaptic, choosing Edit and taking the fix broken packages option. Hop eit works :)

---

### Post by jvc26 on 2007-04-12
Can you not try:
```

sudo apt-get install sun-java5-bin

```
Again? When you get the licence agreement, tab takes you to OK and then you press enter.
Il

---

### Post by poscogrubb on 2007-04-12
Thanks, Illuvator. What you suggested worked. Not sure why I didn't think of that! There were some dependencies, but it installed and then I was able to remove it completely.

Is this a bug of Synaptics? There should either be a warning that this java5 needs a working terminal to accept input, or Synaptics should provide that input... hmm.

---

