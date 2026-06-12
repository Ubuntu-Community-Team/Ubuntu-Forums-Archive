---
title: "can't play rmvb, probably missing codecs"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by henry8596 on 2007-05-29
hi

i try to use VLC and movie player which are the defaut software provided by ubuntu to play rmvb, but there is no display nor sound
i know probably i am missing the codecs, i have spent a few hrs to try to find in the forum but still no result
can anyone help me where i can find the codecs for most of the vedio file? like rmvb, rm, avi,?

---

### Post by lreyes6 on 2007-05-29
i'm using gentoo right now but can you try to search in sinaptics the real media program? 

i think this will solve the problem :D

---

### Post by Inxsible on 2007-05-29
Go to Applications -- > Add Remove
 
search for GStreamer
 
and install all of them. That should take care of the avi for sure.. I havent tried any rmvb files. but they might work too. If not, you might have to get the codecs from some external repository.

---

### Post by henry8596 on 2007-05-29
hx for ur suggestions
but it doesn't work
can anyone help?

---

### Post by EdThaSlayer on 2007-05-29
You need to get the realplayer from the realplayer site and run the binary file. Just visit [www.real.com/linux/](www.real.com/linux/).

---

### Post by henry8596 on 2007-05-29
thx for the suggestion
i have download it and run it in the terminal and follow the direction to install it
and i think i have installed it
but i don't know how to launch it, coz i don't see it in the applications

and  may i ask wt do u mean by   run the binary file?

---

### Post by EdThaSlayer on 2007-05-29
> **henry8596 said:**
> thx for the suggestion
i have download it and run it in the terminal and follow the direction to install it
and i think i have installed it
but i don't know how to launch it, coz i don't see it in the applications

and  may i ask wt do u mean by   run the binary file?

Look for the file "realplay.bin" and right-click properties. Then go to permissions and allow it to execute as a program. After that just double-click on it. If you have sound then everything should work pretty well, and if not you should install alsa-oss.

---

### Post by henry8596 on 2007-05-29
is alsa-oss a software?
coz i type this in terminal and can't find anything
henry@henry-desktop:~$ sudo apt-get alsa-oss
Password:
E: Invalid operation alsa-oss
henry@henry-desktop:~$ sudo apt-get alsa
E: Invalid operation alsa
henry@henry-desktop:~$ 
henry@henry-desktop:~$

---

### Post by Inxsible on 2007-05-29
> **henry8596 said:**
> hx for ur suggestions
but it doesn't work
can anyone help?
 
AVI doesnt work either ?

---

### Post by Inxsible on 2007-05-29
Once you download the realplayer.bin put it on the desktop and do this: (if you put it somewhere else, you will have to cd to that directory)
Make the file an executable:
```

sudo chown +x realplayer.bin

```
 
To install it after making it executable:
```

sudo ./realplayer.bin

```
 
Of course, I am not sure what the file name is when you download. So replace "realplayer.bin" with whatever the file name is

---

### Post by EdThaSlayer on 2007-05-29
> **henry8596 said:**
> is alsa-oss a software?
coz i type this in terminal and can't find anything
henry@henry-desktop:~$ sudo apt-get alsa-oss
Password:
E: Invalid operation alsa-oss
henry@henry-desktop:~$ sudo apt-get alsa
E: Invalid operation alsa
henry@henry-desktop:~$ 
henry@henry-desktop:~$

Use this command instead

> sudo apt-get install alsa-oss

---

### Post by resistantgnome on 2007-07-17
realplayer works great for rmvb files.

---

