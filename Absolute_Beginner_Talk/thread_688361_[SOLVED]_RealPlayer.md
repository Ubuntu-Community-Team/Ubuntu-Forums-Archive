---
title: "[SOLVED] RealPlayer"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-05
Hello!
I downloaded RealPlayer10GOLD.bin from [http://www.real.com/linux](http://www.real.com/linux) but I couldn't install it:
```
hooman@hooman-laptop:~/Downloads$ sh RealPlayer10Gold.bin
sh: Can't open RealPlayer10Gold.bin

```
So I used apt-get, but I got:
```
hooman@hooman-laptop:~$ sudo apt-get install realplay
[sudo] password for hooman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay

```
What should I do and how can I install it?
Thanks.

---

### Post by Seisen on 2008-02-05
do this in order to make the .bin file executable.

```
sudo chmod a+x RealPlayer10GOLD.bin
``` then ```
./RealPlayer10GOLD.bin
```

---

### Post by Hoom@n on 2008-02-05
Thanks, but:
```
hooman@hooman-laptop:~$ cd Downloads
hooman@hooman-laptop:~/Downloads$ chmod a+x RealPlayer10GOLD.bin]
chmod: cannot access `RealPlayer10GOLD.bin]': No such file or directory
hooman@hooman-laptop:~/Downloads$ chmod a+x RealPlayer10GOLD.bin
hooman@hooman-laptop:~/Downloads$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
hooman@hooman-laptop:~/Downloads$ 

```

---

### Post by Seisen on 2008-02-05
My fault add a sudo in front of the chmod command and I see something else I did. I will edit that post to make it the right command.

---

### Post by Hoom@n on 2008-02-05
Again thanks, but:
```
hooman@hooman-laptop:~$ cd Downloads
hooman@hooman-laptop:~/Downloads$ sudo chmod a+x RealPlayer10GOLD.bin
[sudo] password for hooman:
hooman@hooman-laptop:~/Downloads$ ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
hooman@hooman-laptop:~/Downloads$ 

```
(i'm installing some programs at the same time, but I don't think that this error is because that)

---

### Post by Bablefish on 2008-02-05
If you want a simpler way of installing Real Player as in an actual deb file you can find the link here.  [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by Hoom@n on 2008-02-05
So you mean I have to:
```
 $ sudo aptitude install libstdc++5
```
Is it right?

---

### Post by andybleaden on 2008-02-05
> **Bablefish said:**
> If you want a simpler way of installing Real Player as in an actual deb file you can find the link here.  [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

This is what I did the other day and this worked for me just fine. Saved the deb file on my desktop then moved to the Home folder did sudo install "NAMEOFFILE" and it was fine

---

### Post by Hoom@n on 2008-02-05
Thanks for your help. But I just " $ sudo aptitude install libstdc++5" and then I could install the file wich was downloaded from the real site.
Again thanks.

---

