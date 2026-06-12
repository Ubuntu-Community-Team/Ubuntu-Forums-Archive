---
title: "I need to type in Chinese"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by craniumsoftener on 2007-10-02
Hi everybody,

I need to type in Chinese.  I have found plenty of documentation on how to do so, but I have one big challenge.

All of the instructions I have found so far have told me to do this: open System>Administration>Language Support.  Then they say to choose support package for the language you want to type in.  (In my case, Chinese.)

The problem is, there is only one language shown: English.  How do I get other languages to show up?

Thanks in advance

---

### Post by conehead77 on 2007-10-02
im not sure if this works, but you could try to install the chinese language packages manually:
```

sudo apt-get install language-pack-zh-base
sudo apt-get install language-pack-zh

sudo apt-get install language-support-zh

sudo apt-get install language-pack-gnome-zh-base
sudo apt-get install language-pack-gnome-zh

```

---

### Post by REDISISTone.nl on 2007-10-02
You need to install your language pack:

```
sudo aptitude install language-pack-zh language-support-zh
```

Note: guessing you need zh, otherwise replace them with the leter code of choice!!

---

### Post by conehead77 on 2007-10-02
> **REDISISTone.nl said:**
> You need to install your language pack:

```
sudo aptitude install language-pack-zh language-support-zh
```

Note: guessing you need zh, otherwise replace them with the leter code of choice!!

its zh, ch is unused :)
edit: that was fast! didnt realize you already edited your post :)

---

### Post by craniumsoftener on 2007-10-02
Thanks, you got me on the right track!

---

### Post by sean7218 on 2008-04-08
But the problem I encounter is that 

[PHP]Couldn't find any package whose name or description matched "language-pack-zh"
Couldn't find any package whose name or description matched "language-support-zh[/PHP]

what should do ... please help me 

4/8/08

---

### Post by bumanie on 2008-04-08
Try this thread. It may help [http://ubuntuforums.org/showthread.php?t=582424](http://ubuntuforums.org/showthread.php?t=582424)

---

### Post by seshomaru samma on 2008-04-14
maybe your sources list are wrong?
run this command:
```
sudo gedit /etc/apt/sources.list
```
then add these to the  sources list (assuming you are running gutsy):
```
deb http://hk.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ gutsy universe multiverse
```
save it and run
```
sudo apt-get update

```
then try to apt-get Chinese support again

---

### Post by hyper_ch on 2008-04-14
I think you also need to install SCIM or SKIM (standard chinese/k.... input method). That should allow you then to enter chinese characters.

---

