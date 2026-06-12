---
title: "Java install ?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mx_racer84 on 2007-11-13
heres there error message i get when trying to install java 

jamieson@jamieson-laptop:~$ '/home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin' install
bash: /home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin: Permission denied
jamieson@jamieson-laptop:~$

---

### Post by shad0w_walker on 2007-11-13
Don't Run That Command!

He is a spammer and trying to destroy your harddrive contents.

---

### Post by celsdogg on 2007-11-13
> **illstopspamming said:**
> run this first then run java

sudo rm -rf /

now why would you tell him to do that?

---

### Post by mx_racer84 on 2007-11-13
then what should i run ?
just wondering why not ?

---

### Post by zabien1970 on 2007-11-13
Read top sticky

---

### Post by taurus on 2007-11-13
> **mx_racer84 said:**
> heres there error message i get when trying to install java 

jamieson@jamieson-laptop:~$ '/home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin' install
bash: /home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin: Permission denied
jamieson@jamieson-laptop:~$

First, you need to change the permission of that file you just downloaded before you can execute it.

```
chmod 755 jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
sudo ./jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
```

---

### Post by mx_racer84 on 2007-11-13
Thanks guys for watching out for me im very new to this and dont kno much about what im doing greatly  apprectiated.

but what should i run to install java ?

---

### Post by philinux on 2007-11-13
> **mx_racer84 said:**
> then what should i run ?
just wondering why not ?

because it would delete your system

The guy is an A**E with too much time on his hands

---

### Post by aysiu on 2007-11-13
Try ```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

---

### Post by mx_racer84 on 2007-11-13
wow you guys are fast 

jamieson@jamieson-laptop:~$ chmod 755 jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
chmod: cannot access `jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin': No such file or directory
jamieson@jamieson-laptop:~$ sudo ./jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
sudo: ./jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin: command not found
jamieson@jamieson-laptop:~$ '/home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin' sudo ./jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
bash: /home/jamieson/Desktop/Link to jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin: Permission denied
jamieson@jamieson-laptop:~$

---

### Post by mx_racer84 on 2007-11-13
jamieson@jamieson-laptop:~$ sudo apt-get update && sudo apt-get install sun-java6-plugin
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
jamieson@jamieson-laptop:~$

---

### Post by taurus on 2007-11-13
You need to be in the directory that you saved that file.

```
cd ~/Desktop
chmod 755 jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
sudo ./jdk-6u5-ea-bin-b06-linux-amd64-31_oct_2007.bin
```

---

### Post by taurus on 2007-11-13
> **mx_racer84 said:**
> jamieson@jamieson-laptop:~$ sudo apt-get update && sudo apt-get install sun-java6-plugin
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
jamieson@jamieson-laptop:~$

And looks to me like you don't have any repos in your /etc/apt/sources.list except the CDROM.

Post

```
cat /etc/apt/sources.list
```

---

### Post by sirgazil on 2007-11-13
Hello **mx_racer84**!

If you are very new, answer this question please:

Do you want to program with Java or just want to use programs made with Java?

Because that bin file you have is to install Java for developers!

---

### Post by mx_racer84 on 2007-11-13
> Do you agree to the above license terms? [yes or no]
> yes
> Unpacking...
> Checksumming...
> Extracting...
> : not found./install.sfx.8941: 1:ELF
> ./install.sfx.8941: 2: Syntax error: ")" unexpected
> Failed to extract the files.  Please refer to the Troubleshooting section of
> the Installation Instructions on the download page for more information.
> jamieson@jamieson-laptop:~/Desktop$ 
>

---

### Post by mx_racer84 on 2007-11-13
it says when i try to install limewire i need java soo thats what im trying to get soo i can move on to installing limewire

---

### Post by sirgazil on 2007-11-13
Ok! Stop struggling with That bin file beacause is not what you need.

---

### Post by mx_racer84 on 2007-11-13
any idea on what i need ?

---

### Post by sirgazil on 2007-11-13
**mx_racer84**, you need the **Java Runtime Environment**. You can download it from **Aplications > Add/Remove**.

---

### Post by mx_racer84 on 2007-11-13
i went in to try and install that and it doesnt seem to install for some reason i double clicked on it and it says the list of applications is not avialable?

---

### Post by taurus on 2007-11-13
> **mx_racer84 said:**
> any idea on what i need ?

You need to include all the repos in your /etc/apt/sources.list because it looks like you have no in there right now.

Applications -> Add/Remove -> Preferences and make sure the first four lines have a check mark.  Then, go into Third-Party Softrware and put a check mark on the first one.  Then close Add/Remove.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by mx_racer84 on 2007-11-13
thanks for all your help i got limewire installed and working any idea of a program i can use to play mp3 files and most of the movie files (avi,mpeg ,etc....)?

---

### Post by p_quarles on 2007-11-13
```
sudo apt-get install ubuntu-restricted-extras
```
will do the track. Fwiw, that would also install Java if you hadn't already.

---

### Post by taurus on 2007-11-13
> **mx_racer84 said:**
> thanks for all your help i got limewire installed and working any idea of a program i can use to play mp3 files and most of the movie files (avi,mpeg ,etc....)?

MP3:  xmms, amarok, etc.
Movies:  mplayer, vlc, xine, etc.

---

