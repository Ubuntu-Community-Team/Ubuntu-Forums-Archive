---
title: "How to find the MD5 sum?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2007-01-19
How to find the MD5 sum? I am downloading an archive (MoinMoin Wiki system) and just want to be sure everything is correct. Where can I compute the MD5 sum and then do a comparison?

---

### Post by mikewhatever on 2007-01-19
See here for instructions: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://help.ubuntu.com/](https://help.ubuntu.com/) has tons of useful information. My advice, bookmark it. :-)

---

### Post by mcduck on 2007-01-19
in Ubuntu? 'md5sum filename'

---

### Post by xyz on 2007-01-19
Also in case of burning .iso with k3b, it'll automatically check it.

---

### Post by Zdravko on 2007-01-19
[mcduck]("http://ubuntuforums.org/member.php?u=17309"), how do I make the comparison? I hope you don't expect me to compare each symbol one by one...

---

### Post by xyz on 2007-01-19
Not sure this is what you mean but:
a. Download the iso;
b. Download the md5sum file;

c. Check the iso's md5sum by using a md5sum checking program (K3b for example will generate one automatically). You do this by pointing the program to the downloaded iso, which it will generate a md5sum for;

d. Open up the downloaded md5sum file, it is simply a text file containing the md5sum. Compare it to the outcome of (c). If they match, cool, if not, there's a problem.

---

### Post by xyz on 2007-01-19
Also this:
 1. Create:
```
md5sum file.iso > file.iso.md5
```
 2. Verify:
```
md5sum -c file.iso.md5
```

---

### Post by mcduck on 2007-01-19
> **Zdravko said:**
> [mcduck]("http://ubuntuforums.org/member.php?u=17309"), how do I make the comparison? I hope you don't expect me to compare each symbol one by one...

I always just paste the md5sum I got and the one from the download page above each other on a text file. It's pretty easy then to check that they are same.

---

