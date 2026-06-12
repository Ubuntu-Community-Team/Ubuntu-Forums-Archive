---
title: "How do I add Debian's repositories to my sources.list?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-06-28
I want to try some of debian's packages but I can't find the URL of Debian's official repositories.

How do I add Debian's Repositories to my sources.list?

---

### Post by overdrank on 2007-06-28
> **wersdaluv said:**
> I want to try some of debian's packages but I can't find the URL of Debian's official repositories.

How do I add Debian's Repositories to my sources.list?

Hi have you seen this site. 
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by holihue on 2007-06-28
> **wersdaluv said:**
> I want to try some of debian's packages but I can't find the URL of Debian's official repositories.

How do I add Debian's Repositories to my sources.list?


[Try this]("http://www.linuxquestions.org/questions/showthread.php?threadid=379597")

---

### Post by wersdaluv on 2007-06-28
What's the apt line of the official Debian Repositories?

---

### Post by wersdaluv on 2007-06-28
I found what I am looking for here [http://www.linuxquestions.org/questions/showthread.php?t=330913](http://www.linuxquestions.org/questions/showthread.php?t=330913)

Will there be any possible problem if I add Debian's Repositiories to my sources.list?

---

### Post by mcduck on 2007-06-28
> **wersdaluv said:**
> I found what I am looking for here [http://www.linuxquestions.org/questions/showthread.php?t=330913](http://www.linuxquestions.org/questions/showthread.php?t=330913)

Will there be any possible problem if I add Debian's Repositiories to my sources.list?

Yes, the more you install from repositories not made for Ubuntu the more likely your system will break.

I would not recommend using Debian's repositories. If you really need some package they have that is not in Ubuntu's repositories, add Debian's repos, install what you need (and hope it doesn't break anything) and then remove Debian's repositories again.

---

### Post by Genecks on 2007-08-02
As a quick question, does anyone have any idea as to how much memory (on first time) is used to update from the debian repositories?

> deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) unstable main contrib non-free
deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) testing main contrib non-free

---

### Post by Paulmd on 2007-08-02
> **wersdaluv said:**
> I found what I am looking for here [http://www.linuxquestions.org/questions/showthread.php?t=330913](http://www.linuxquestions.org/questions/showthread.php?t=330913)

Will there be any possible problem if I add Debian's Repositiories to my sources.list?

If you don't install the key, your system will whine about unauthenticated packages. The websites relating to the various repositories have instructions on installing these keys. 

(usually a wget command)

---

### Post by Paulmd on 2007-08-02
> **Genecks said:**
> As a quick question, does anyone have any idea as to how much memory (on first time) is used to update from the debian repositories?

You mean Storage, not ram, i presume. It will depend on what you already have installed. 

It will tell you how much space in required.

---

