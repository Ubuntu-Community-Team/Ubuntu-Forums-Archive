---
title: "trying to install amsn 0.95"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by JGMN on 2006-05-07
I downloaded both the .tar and .deb files. I have no clue how to install them. Also I can't update the prgram directly from the old. 

I'm a new user and have installed things on the terminal only by copying things on forums but bascially haven't had much luck installing programs that I got off the web.

Also some programs downloaded from the add application and synaptic package seem nowhere to be found.

---

### Post by Omnios on 2006-05-07
Hi I wrot a small help file on installing packages. 
[http://ubuntuforums.org/showthread.php?t=171822]("http://ubuntuforums.org/showthread.php?t=171822")
There are a lot of more indepth guides on this forum.
 
 Also do you have extra repositories set up, that openes a up a hole bunch of new packages. Also checkout the backports section on this forum they have a lot of more up to date packages. Regular packages are froven on Ubuntu release  and backports are new versions added.

---

### Post by uzi09 on 2006-05-07
it is a lot easier if you use apt-get or synaptic (gui version of apt-get).

go to System > Administration > Synaptic Package manager.

On the bottom, select the 'Custom' button. click on something in the right panel and start typing: amsn
then just click on the box and select install.

this is a package manager. just about any program u ever want is available here...FOR FREE =D.

if you insist on using the .deb files, heres how u install them:

```
 sudo dpkg -i amsn.deb
```
sub in whatever the programs name is in places of "amsn.deb"

for tar files, it's a bit more work, and leaves kind of a mess if you don't know what you're doing. best to stick with the first to methods, but again, if u insist, post and we'll let u know how. plus if u google, there are MILLIONS of places that teach you how to install tar-gzip files.

good luck
uzi


EDIT: oops, sorry, didn't read the end of your post -  looks like you already know how to use synaptic.
also a good resourse to start off ubuntu with is: [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
it'll teach you how to add extra sources to download even more programs from synaptic.

---

### Post by arnieboy on 2006-05-07
[QUOTE=JGMN]I downloaded both the .tar and .deb files. I have no clue how to install them. Also I can't update the prgram directly from the old. 

I'm a new user and have installed things on the terminal only by copying things on forums but bascially haven't had much luck installing programs that I got off the web.

Also some programs downloaded from the add application and synaptic package seem nowhere to be found.[/QUOTE]
the following thread is what u are looking for:
[http://ubuntuforums.org/showthread.php?t=87001](http://ubuntuforums.org/showthread.php?t=87001)

---

### Post by aysiu on 2006-05-08
[QUOTE=JGMN]I downloaded both the .tar and .deb files. I have no clue how to install them. Also I can't update the prgram directly from the old[/QUOTE] Use [this script](http://ubuntuforums.org/showpost.php?p=978766&postcount=47).

---

### Post by JGMN on 2006-05-08
thanks , all the information really helped me. :D

---

