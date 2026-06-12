---
title: "Android and Linux - where are the practical similarities?"
date: 2011-09-18
forum: Any Other OS
---

### Post by casbahdk on 2011-09-18
What can I do with Android, that I do (in my case) with Xubuntu? I have been doing a lot of searching on the Net to answer this question, but I haven't found any consistent resources that review the practical similarities between Android and Linux, seen from a Linux users point of view, _without installing a custom ROM_?

I have a rooted Samsung Galaxy Spica (i5700) running Android 2.1, with "a Better Terminal App Pro" installed, as well as BusyBox. Obviously, APT isn't included with Android 2.1, so I won't be doing any software updating that way.

Here are a few basic questions:
[LIST=1]
[*]Is it possible to edit some preferences, with more options, using VI, than from the GUI?
[*]How does the Android file structure compare to Linux?
[*]Is it possible to install some CLI apps like lynx, nano, alpine or mutt, cmus, etc?
[*]What is the path to a microSD card?
[*]Is it possible to use wget and save a file to the microSD card?
[*]Is it possible for me to use ftp to log into my web hotel and copy files to it, as I do from my desktop computer?
[/LIST]

Any comments, URLs, etc. would be appreciated, particularly with regards to the Android CLI and hacking Android 2.1.

---

### Post by jago25_98 on 2011-10-01
I used to think that Android is linux. It's not. It's built on a lot of the kernel, but that's about it. Google take taken quite a lot of things and not contributed back a whole lot, with some people saying that Apple has contributed more. 

There are many similarities but they are rare enough to make it worth having a look at androlinux.com

I've only just got my first android today. sdcard for me is at /sdcard . 

I notice that there's a confusing mass of differences in versions and vendor modifications with little consistency, unlike Ubuntu and iPhone. Well, it's confusing for me as a newcomer anyway. 

The file structure is completely different, commands are more basic. No bash, no colors, no tab completion, no --help:
```
# ls /
rom
sqlite_stmt_journals
sdcard
media
cache
tmp
etc
proc
sbin
default.prop
env.txt
data
init.rc
init.goldfish.rc
init
sys
system
root
dev
# 

```
I think you can get wget, you can ftp but if it's rooted but not custom rom then every phone is different as to how easy that is. Not sure about the other commandline programs. 1st impressions are that there are some commandline programs but only a few have been cross compiled. 


Let me know if you find out more

---

### Post by casbahdk on 2011-10-02
Thanks for your reply. It helped to shed some light on the issue, but as you say, Android can be very confusing due to the lack of a standard implementation. I have read somewhere recently that Google wants to ensure that there is a standard implementation in the future, however. I will post anything I find out on this thread.

---

