---
title: "[SOLVED] Need help installing Beryl"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by uBrendon on 2007-11-27
sudo apt-get install beryl beryl-manager emerald-themes


Hey, I tryed that and it didn't work. This is what happens.

brendon@Brendon-laptop:~$ sudo apt-get install beryl beryl-manager emerald-themes
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package beryl
brendon@Brendon-laptop:~$
I have main universe restricted and multiverse checked. help please, thanks in advance

---

### Post by Znort_Ubern00b on 2007-11-27
beryl is old, now need to install compiz go to
system - admin - synaptic and search for compiz 

mark it and then click apply

---

### Post by PmDematagoda on 2007-11-27
I know this may not necessarily solve your problem, but why don't you use Compiz-fusion? It is Beryl and Compiz together and as it is, both Beryl and Compiz are over and are not being developed upon or improved officially, so Compiz-fusion would be much better.

---

### Post by uBrendon on 2007-11-27
I have Compiz-Fuzion I thought with beryl I could get even more features

---

### Post by PmDematagoda on 2007-11-27
Since Compiz-fusion is actually built on both Beryl and Compiz, I do not think you could get more features from either Beryl or Compiz than what you are getting from Compiz-fuson since it is the most updated and active.

---

### Post by uBrendon on 2007-11-27
That's the reason I want Beryl, so can anyone help me get it?


```
http://www.youtube.com/watch?v=xC5uEe5OzNQ
```

---

### Post by overdrank on 2007-11-27
> **uBrendon said:**
> That's the reason I want Beryl, so can anyone help me get it?


```
http://www.youtube.com/watch?v=xC5uEe5OzNQ
```
In the terminal use these commands but I will warn you that is will cause problems with compiz-fusion in Gutsy as soon as you update your system to install beryl

```
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Then type in:
```
gksudo gedit /etc/apt/sources.list
```

This will open a file, add this to the very bottom by pasting:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

```
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings emerald emerald-themes
```
Use at your own discretion.

---

### Post by uBrendon on 2007-11-27
Some one finally told me..Thanks. I'm not going to use it because I don't trust it messing up what I have now but thanks anyway.

---

### Post by overdrank on 2007-11-27
> **uBrendon said:**
> Some one finally told me..Thanks. I'm not going to use it because I don't trust it messing up what I have now but thanks anyway.

Ok well could you please mark the thread as solved under thread tools. Thanks. :KS

---

