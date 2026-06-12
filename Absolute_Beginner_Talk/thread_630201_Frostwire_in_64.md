---
title: "Frostwire in 64"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-03
I read somewhere that in order to install frostwire on 64 linux is to force install it.  Is this still true?  If not, why is it not working for me? I downloaded i586.deb file from the site, and it opens, and places a frostwire icon in my applications>internet menu, but when i try to run it, nothing happens.  What's the problem here?

---

### Post by sethvath on 2007-12-03
Make sure you have the 32bit java installed

---

### Post by jordank on 2007-12-03
that's probably the problem. how do i do that?

---

### Post by PmDematagoda on 2007-12-03
Install he 32-bit version of Java using:-

```
sudo apt-get install ia32-sun-java6-bin
```

Then select the normal JRE as the 32 bit version before running Frostwire using:-

```
sudo update-alternatives --config java
```

---

### Post by jordank on 2007-12-03
worked perfectly, thank you sir.

although, might i ask where you found the code:
sudo apt-get install ia32-sun-java6-bin

or did you just know this off by heart?

---

### Post by PmDematagoda on 2007-12-03
You are welcome:).

And I did not by heart the code, I got it from [here]("http://www.uluga.ubuntuforums.org/showthread.php?t=563819") at the ninth post by master_kernel. Google is the best source you can use for solving your Linux problems, so use it wisely;).

---

