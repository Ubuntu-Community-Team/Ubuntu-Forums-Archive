---
title: "Wine: Install eRead. Regsvr32.exe needed?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by pinkkiss110 on 2008-03-04
Hi newbie here.

I am trying to install a program called eRead. It's a chinese program.
It handles .stk files that are becoming pretty popular in novel reading in china...

[SIZE="4"]During the installation, I encountered 2 problems:
1: [COLOR="DarkRed"]Chinese words are not displaying properly[/COLOR]... All the words are like >>>>> or <<<<<<<
2. In the end, it says that it has encountered [COLOR="DarkRed"]some problem trying to write regsvr32.exe[/COLOR][/SIZE]

please help me!

---

### Post by Cypher on 2008-03-05
I think Wine might be ill-suited for this particular application, you're probably better of running Windows within VMWare or VirtualBox.

---

### Post by happyhamster on 2008-03-05
- Make sure you have Chinese language support installed (System-->Administration-->Language Support). Note that you'll have to reboot.

- You can then start wine like this:

LANG=zh_CN.UTF-8 wine program_name.exe

- That's just an example, as I don't know which locale you'll need. You can find the installed locales in this folder: /var/lib/locales/supported.d/
It contains text files with the exact names you can use. For example:

zh_CN.UTF-8
zh_SG.UTF-8
zh_HK.UTF-8
zh_TW.UTF-8

- Concerning the regsvr32.exe error: does that mean the program doesn't work/install? Else you can just ignore it.

Good luck, and keep us informed.

---

