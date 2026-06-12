---
title: "terminal command to determine version?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-14
Ok, i have successfully downloaded and installed version 7.04.   This is after literally over a dozen unsuccessful attempts.   Call me crazy if you would like but i would like to be shown that i am using the current version of Ubuntu.  Is there a command i can use in the terminal i can use to find out what version i am using?

---

### Post by ITdrummer on 2007-06-14
sorry, apparently i enjoy using the word "use"  ha ha

---

### Post by Shazaam on 2007-06-14
uname -r  shows kernel.
uname -a shows a little more.

---

### Post by ITdrummer on 2007-06-14
.....doesnt really help....im looking for a command i can input, and the output tells me that i am using xxxxx version of ubuntu.......uny suggestions?

---

### Post by baeckel on 2008-02-18
There are three ways you can go about this:

1: look at the "issue" file --> ```
less /etc/issue
```

2: issue the command --> ```
lsb_release -a
```

3: look at the "lsb_release" file directly --> ```
less /etc/lsb_release
```

---

### Post by MasterJS on 2008-02-18
Just going to the System Monitor and click on the first tab. Thats where you'll find it.

---

