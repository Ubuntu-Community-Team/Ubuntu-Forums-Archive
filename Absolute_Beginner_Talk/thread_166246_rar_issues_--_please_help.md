---
title: "rar issues -- please help"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-26
Hi, I have some file compressed with rar software now I installed 7zip to unrar those but it give me this error
```
Extracting xxx.xxx Unsupported Method
```
Is there a a way to fix this issue?

I lso thought of installing rar and I know you can do it by using this command
```
sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar
```
But the problem is that at this time I dont have access to internet on the machine where ubuntu is installed, is there a way to get rar on another machine and install it on ubuntu by transfering the file, if there is a way to do this can someone please give me the link to download rar on another computer and then install it on ubuntu.

Cheers.

---

### Post by joshrobinson on 2006-04-26
[http://packages.ubuntulinux.org/dapper/source/rar]("http://packages.ubuntulinux.org/dapper/source/rar")

make sure to grab the dependencies just in case.. EDIT:above is for dapper sorry

[http://packages.ubuntulinux.org/breezy/utils/rar]("http://packages.ubuntulinux.org/breezy/utils/rar")

that one is for breezy

grab unrar in the dependencies list to unpackage rar files

---

### Post by hezral on 2006-04-26
you can get the packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

search for rar and also unrar. dont take the unrar-free one.

also i think you need to get libstdc++5 packages too

hope that helps

---

### Post by rameez on 2006-04-26
this might be a stupid question but how do i know if I am running breezy or dapper


n00b

---

### Post by joshrobinson on 2006-04-26
[QUOTE=rameez]this might be a stupid question but how do i know if I am running breezy or dapper


n00b[/QUOTE]

hold control, alt then hit f2.. screen should switch black to a command prompt with the version number at the top

hold control, alt then hit f7 to get back into xwindow where you were

5.10 is breezy
6.06 is dapper

---

### Post by rameez on 2006-04-26
Thanks so much guys, I have got rar running now

---

### Post by joshrobinson on 2006-04-26
[QUOTE=rameez]Thanks so much guys, I have got rar running now[/QUOTE]

no problem. you grabbed unrar also correct? so you can extract also

---

### Post by rameez on 2006-04-26
actually i installed rar_3.30-2_i386.deb and now archiver can unrar files did not have to install unrar seperately

---

### Post by joshrobinson on 2006-04-26
[QUOTE=rameez]actually i installed rar_3.30-2_i386.deb and now archiver can unrar files did not have to install unrar seperately[/QUOTE]

ok cool :D

---

