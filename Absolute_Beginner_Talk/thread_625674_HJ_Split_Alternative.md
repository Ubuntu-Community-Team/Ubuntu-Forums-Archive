---
title: "HJ Split Alternative"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-11-28
My former roommate is converting some old party videos to a digital format.  He is using a free webhost that limits the size of files he can post, so he is splitting them with HJSplit.  There is a Linux version of this software, but it requires me to install something from root and I'm really not interested in installing software outside of the repositories.  Is there a program in synaptic that can rejoin videos split by the HJsplit program?

---

### Post by _sAm_ on 2007-11-28
I know there is a cli program to split files, but I don't think it can work with files from HJSplit.

Could you ask your friend to instead use WinRar for Windows(its free), to splitt the files(very easy in winrar)? Then you could use Fileroller to open and rejoin with one click.

---

### Post by mali2297 on 2007-11-28
If HJSplit does the same as the native **split**, then this would join the parts together
```

cat example.001 example.002 example.003 > example 

```
But I'm not certain that it will work in this case.

An alternative is to use one of the Java versions of HJSplit, for example hjsplit_g.jar. Download hjsplit_g.jar from the web, install Java from the repositories, then run
```

java -jar hjsplit_g.jar

```
That way you don't have to install HJSplit itself.

---

### Post by harakiri1976 on 2007-11-28
Hi!


Thank You mali2297!

I had the same problem with a lot of .avi files that I've downloaded from rapidshare. The user that posted the files told to use "Hj Split" to join them. But, I was trying to find a "Linux Solution". Thank you for your Help! :)

It Worked! :)

---

