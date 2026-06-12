---
title: "I messed up."
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Darrenlaid on 2006-11-07
Yesterday i attempted to add some software, it might have been chess software or perhaps it was anagram software, needless to say i was not very succesfully.
Today i was working my way through "adding repositories" [https://help.ubuntu.com/community/Re...24051d07b8dc64](https://help.ubuntu.com/community/Re...24051d07b8dc64)
When i tried to "Reload" in the synaptic package manager i got an error.
E: Type &#8216;[ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;](ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;) is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory

After seeing this i remember i did a custom add channel yesterday, big mistake i guess.
Could somebody be so kind as to help me correct my error and help me clean up this mess i have created. Thank you.

---

### Post by taurus on 2006-11-07
> **Darrenlaid said:**
> Yesterday i attempted to add some software, it might have been chess software or perhaps it was anagram software, needless to say i was not very succesfully.
Today i was working my way through "adding repositories" [https://help.ubuntu.com/community/Re...24051d07b8dc64](https://help.ubuntu.com/community/Re...24051d07b8dc64)
When i tried to "Reload" in the synaptic package manager i got an error.
E: Type &#8216;[ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;](ftp://ftp.cis.uab.edu/pub/hyatt/&#8217;) is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory

After seeing this i remember i did a custom add channel yesterday, big mistake i guess.
Could somebody be so kind as to help me correct my error and help me clean up this mess i have created. Thank you.

Why don't you remove the line for "ftp://ftp.cis.uab.edu/pub/hyatt/" from your /etc/apt/sources.list!

```
gksudo gedit /etc/apt/sources.list
```
Then update it again and see what happens...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by MasterOfDisaster on 2006-11-07
What exactly is line 34 in your sources list?  Are you sure that it follows the conventions needed for apt-get/synaptic to recognize it?

---

### Post by Jussi Kukkonen on 2006-11-07
(... Taurus and MasterOfDisaster beat my to it)

---

### Post by .t. on 2006-11-07
Just post your sources.list

---

### Post by Super King on 2006-11-07
You can also remove it via the GUI: System->Administration->Software Sources.

---

### Post by Darrenlaid on 2006-11-07
Thanks for the help, seems to have fixed my problem for today.

---

