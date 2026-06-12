---
title: "missing stuff"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Artist22405 on 2006-05-05
ok I just did a fresh install of dapper. heres my problem I am missing alot of stuff that I had with 5.10 like xmms and other stuff too. I tried to use p[ackage manger like in 5.10 nope aint finding stuff tried a command line from easylinux info that didnt work either . my question is is there anyway to add 5.10 stuff to dapper through the package manger

---

### Post by krusbjorn on 2006-05-05
You need to enable the universe/multiverse repositories. The easiest way to do that would be to Settings->Repositories in Synaptic and just check the boxes, I believe. Or you can manually change your /etc/apt/sources.list file (remove the #'s in front of the correct lines.)

---

### Post by ComplexNumber on 2006-05-05
install a package called automatix. its a package that automatically installs a lot of the necessary stuff such as codecs and useful applications etc.

---

### Post by Sef on 2006-05-05
> am missing alot of stuff that I had with 5.10 like xmms

To install xmms, open the terminal and type this:

sudo apt-get update

sudo apt-get install xmms

that will install xmms.  For other packages that you are missing, replace xmms with the package name.  If you are not sure of the package name go to 'packages.ubuntu.com' to find them. (don't use the quotes.)

---

### Post by krusbjorn on 2006-05-05
[QUOTE=ComplexNumber]install a package called automix (automax?), i can't remember the exact name (mental block), but its a package that automatically installs a lot of the necessary stuff such as codecs and useful applications etc.[/QUOTE]
It's called [Automatix]("http://ubuntuforums.org/showthread.php?t=138405") :) But I think it is breezy only.

---

### Post by Artist22405 on 2006-05-05
I did check all the repsitories that didnt help and as for automatix I used it with 5.10 worked great but the guide says it doesnt work with dapper

---

### Post by ComplexNumber on 2006-05-05
[quote=krusbjorn]It's called [Automatix]("http://ubuntuforums.org/showthread.php?t=138405") :) But I think it is breezy only.[/quote]
cheers for that :). i've edited my post. i knew it was somerthing that sounded like that.

---

### Post by Sutekh on 2006-05-05
XMMS is available in the supported Ubuntu repositories, no need for the universe repository, although thats where alot of stuff lives, you should be able to install it with
```
sudo apt-get update 
sudo apt-get install xmms
```
and it should be in Synaptic (its there in mine).

What error do you get when trying to install xmms?  What other software (specifically) are you wanting to install.  If it was in Breezy its almost 100% likely its available in Dapper.

---

### Post by Artist22405 on 2006-05-05
Sef you are a life saver I am new and the update work right off the bat thanks alot now if I can just remember all the junk I had on 5.10 thanks again

---

