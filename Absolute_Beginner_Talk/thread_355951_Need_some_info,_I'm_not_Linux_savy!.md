---
title: "Need some info, I'm not Linux savy!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Kittens on 2007-02-07
I have been using Ubuntu for a while now, and it's been just great. But, I've been a Windows user for years, and I have no idea how Linux works. So just for the sake of me not losing any sleep, I have some questions, and hopefully you wonderful community members can answer them for me.

1. When I was a windows user, I was very analistic about always defragmenting whenever I installed something or installed something. Does anything that apply to Ubuntu?

2. Along with the defragmentaion, I would diligently fix my registry very often. Do I have to regularly check a registry with Ubuntu?

That's all that I can think of right now, thanks in advance!

---

### Post by pay on 2007-02-07
You don't need to defrag a drive with Ext3, reiserFS or NTFS (and others) because of the way that they are designed. Only Fat32 drives needed defraging often (to the best of my knowledge). Ubuntu doesn't have a registry and everything keeps itself maintained quite well with little user interaction.

---

### Post by Kittens on 2007-02-07
That's fantastic. I'm running a well oiled machine with everlasting oil, lol.

---

### Post by old_geekster on 2007-02-07
> **Kittens said:**
> I have been using Ubuntu for a while now, and it's been just great. But, I've been a Windows user for years, and I have no idea how Linux works. So just for the sake of me not losing any sleep, I have some questions, and hopefully you wonderful community members can answer them for me.

1. When I was a windows user, I was very analistic about always defragmenting whenever I installed something or installed something. Does anything that apply to Ubuntu?

2. Along with the defragmentaion, I would diligently fix my registry very often. Do I have to regularly check a registry with Ubuntu?

That's all that I can think of right now, thanks in advance!
I am also new to Linux/Ubuntu.  Because of my lack of knowledge, this will either confuse you or help you, because it is one newbie to another.

From what I have read, the files do not become fragmented as in Windows.  Therefore, there is no need to defrag.  This is a quote from "Linux Forums": "You don't really need to defrag a hard drive running Linux."  In fact, defragmentation tools don't exist for ext3.


As for "Registry", there is none.  There are a series of config files that contain the information about your system.  These are updated automatically when an app or program is added.  You can also update them manually when required.  The way Linux and Windows are similar is, when you change something in a config file, it is best to know what you are doing.  Linux doesn't take kindly to garbage in its files, either.  The files don't appear as ominous as the Registry, but can do as much harm when adding incorrect data.

---

### Post by Sef on 2007-02-07
> This is a quote from "Linux Forums": "You don't really need to defrag a hard drive running Linux." In fact, defragmentation tools don't exist for ext3.

There is a defrag tool for ext3.  Every 30 boots in Ubuntu, it will automatically defrag your system.

---

### Post by tbroderick on 2007-02-07
> **Sef said:**
> There is a defrag tool for ext3.  Every 30 boots in Ubuntu, it will automatically defrag your system.

That's fsck not a defrag tool. Fsck does not reorganize data on a hard drive. It only checks for inconsistencies similar to scandisk on Windows.

---

### Post by sloggerkhan on 2007-02-07
Yeah, it is generally agreed that defragging is uneeded on ext3.

---

### Post by confused57 on 2007-02-07
If you want a technical explanation:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by daxumaming on 2007-04-07
> **confused57 said:**
> If you want a technical explanation:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

aha! there it is. i've been googling around for an hour for a technical explanation on why we don't need a defrag utility in Linux... I should've searched ubuntuforums first to save me time.

---

