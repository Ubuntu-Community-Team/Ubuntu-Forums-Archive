---
title: "Data DVD's"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by xshady87 on 2006-04-18
Before I installed Ubuntu, I burned a bunch of mp3 and .wav files onto DVD's using a Windows-based burner (Nero). Now, when I place the DVD's into the computer, only two of them work. The others say "invalid encoding" and no files are visible. I was hoping somebody could assist me with this problem. Thanks.

---

### Post by wolfee on 2006-04-19
I had the same problem, try rebooting then put disk in 1st thing before you run anything else. This worked for me. It seems that Ubuntu can act a little Kooky if it's running for hours at a time.

---

### Post by shamim on 2006-11-02
Hi, 
I am having the same problem with data DVD. But last night in another thread I saw that it can be solved by editing the fstab file, located in etc. Just have to change the things to "auto" instead of "udf,iso9660" value.

I am a complete beginner with linux and ubuntu6.10 is my first OS. Just installed it after knowing about Linux desktop system from one of my senior in a group mail. My experience with Linux (=ubuntu) is less than one month. It seems harder for me as I am a general home PC user with non-IT background.

Anyway, I tried to edit the fstab file but found it to be read only. Can anybody tell be how to edit that file.... or at least where I can find the documentation. I dont want to give up here.

Regards,
Shamim.

---

### Post by CatKiller on 2006-11-02
You may want to read these pages:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by power.supply on 2006-11-25
To edit the fstab file write this into the command line prompt
```
sudo gedit /etc/fstab

```
"sudo" gives you root privilages
"gedit" is just a text editing program (any other one can be used instead)
"/etc/fstab" is a parameter that is sent to gedit to tell it the location of the file to be opened.

If you are a newb then it would probably pay to make a copy of the fstab file first before editing just in case. Putting the wrong parameters in can cause problems.

hope this helps:)

---

