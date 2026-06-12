---
title: "Couple of questions (documenation? External HDD? Install programs not in repos?)"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-24
I've got a couple of questions.  First, where are the 7.10 docs?  Ubuntu doc site only has 6.06 lts, 6.10 and 7.04 listed.  How long does it usually take for the 7.10 docs?  

Secondly, my friend has an external HDD, I'm not very sure of the brand.  It's formatted NTFS and connects through USB.  I'm going to use it to back up my music from my Windows installation, then retrieve them once Ubuntu is installed.  Is it likely I'll run into any problems?

Lastly, how difficult is it to install a software that isn't in the repos?  I like to use Jgrasp for my Java development because of it's very good visual debugger and UML modeling support.  As long as we're at it, how hard is it to set up the JRE and JDK as well as development environments?  Does it take a lot of tinkering?

Thanks.

---

### Post by jfinkels on 2007-10-25
> **TheOrangePeanut said:**
> I've got a couple of questions.  First, where are the 7.10 docs?  Ubuntu doc site only has 6.06 lts, 6.10 and 7.04 listed.  How long does it usually take for the 7.10 docs?  

For the most part, many things will be the same in 7.04 and 7.10. Also, take a look at the community docs, as they are wiki pages and can (and will) be updated more frequently by community members.
> 
Secondly, my friend has an external HDD, I'm not very sure of the brand.  It's formatted NTFS and connects through USB.  I'm going to use it to back up my music from my Windows installation, then retrieve them once Ubuntu is installed.  Is it likely I'll run into any problems?

Search around for the model/manufacturer of the HDD and see if anyone else has had any problems. Most likely, no, you won't. If you are using Ubuntu 7.10, NTFS read/write capabilities come pre-installed, if you are using an earlier version, you will have to install them yourself.
> 
Lastly, how difficult is it to install a software that isn't in the repos?  I like to use Jgrasp for my Java development because of it's very good visual debugger and UML modeling support.  As long as we're at it, how hard is it to set up the JRE and JDK as well as development environments?  Does it take a lot of tinkering?

Thanks.

To install the JRE and JDK:```
sudo aptitude install sun-java6-jre sun-java6-bin sun-java6-jdk
```

If the program is designed for Linux, then there may be a .deb package for it, which is a simple one command install (or one click if you prefer). Read the first link in my signature for more information on installing software.

---

