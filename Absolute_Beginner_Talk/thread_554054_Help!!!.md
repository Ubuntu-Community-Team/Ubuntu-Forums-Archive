---
title: "Help!!!"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Travis8dmc on 2007-09-18
Hi, I am trying to get the internet working on my computer. I used aol on windows, and i am trying to install peng. I downloaded the build-essential pack and that had an error. Also i was thinking of using wine doors to run aol. So.. I installed the deb package for wine doors, but when i open it I get a welcome screen wher i enter my name and if i have a valid win license. When I hit procees it doesn't go to another page. Someone please give me detailed instructions on what to do.

---

### Post by mali2297 on 2007-09-18
> **Travis8dmc said:**
> Hi, I am trying to get the internet working on my computer. I used aol on windows, and i am trying to install peng. I downloaded the build-essential pack and that had an error.

What kind of error?

---

### Post by Travis8dmc on 2007-09-19
something called c-lib i think was missing. And also I need to know where to download java.

---

### Post by mali2297 on 2007-09-19
> **Travis8dmc said:**
> something called c-lib i think was missing. And also I need to know where to download java.

Be more precise, you probably just need to install some package from the repositories.

For Java, run
```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```
or use Synaptic.

EDIT: Of course, this can be difficult if you don't have internet connection. Are you able to download stuff when you're in Ubuntu?

---

### Post by Travis8dmc on 2007-09-19
No, I am trying to set up the internet connection. I was installing the buld-essential package so that I could install Peng(aol dialer) with the terminal. Also I was going to try to install wine and run aol through wine. And I need to get a linux driver for a lucent winmodem.

---

### Post by mysticmatrix on 2007-09-19
> **Travis8dmc said:**
> No, I am trying to set up the internet connection. I was installing the buld-essential package so that I could install Peng(aol dialer) with the terminal. Also I was going to try to install wine and run aol through wine. And I need to get a linux driver for a lucent winmodem.

Did I heard WINmodem? Well, those are made specifically for windows, I guess. Perhaps someone else might tell you where to find drivers, but get a REAL HARDWARE if you want something to work. Also, Wine method would not work as far as I know.

Plus please copy paste entire output of errors. We will not be able to help you if you tell us I got some error related to "...."

---

