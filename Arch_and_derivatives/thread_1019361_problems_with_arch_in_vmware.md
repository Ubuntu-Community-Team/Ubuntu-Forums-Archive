---
title: "problems with arch in vmware"
date: 2008-12-23
forum: Arch and derivatives
---

### Post by jake43025 on 2008-12-23
iam trying too get arch linux installed in vmware but iam having some problems.i can ping a website so i know my network is setup,but i cant download xorg too start setting up the rest of it.here is a picture of what its doing:

[http://i39.tinypic.com/oi9bom.jpg](http://i39.tinypic.com/oi9bom.jpg)

i have spent a couple hours trying too fix it but i cant figure it out.i think it has something too do with the repository or maybe its just vmware.(or me):confused:

also,i tried too sign up for an account on arch linux but accidently put i was a bot on the answer,not i cant register at all.:( do i just have too wait a day for it too let me try again?

---

### Post by justsomedude on 2008-12-23
According to this page:

[http://www.archlinux.de/?page=MirrorStatus](http://www.archlinux.de/?page=MirrorStatus)

heanet.ie is not valid atm (Remote file not found).

The page above is from the german Arch site and may come in handy if you want to check a mirror.

Have a look at /etc/pacman.d/mirrorlist and configure pacman to use a different mirror.

More info: 

[http://wiki.archlinux.org/index.php/Mirrors](http://wiki.archlinux.org/index.php/Mirrors)


After your first upgrade your /etc/pacman.d/mirrorlist will change again because there was a recent change and the devs split pacman and pacman-mirrorlist:

[http://www.archlinux.org/news/427/](http://www.archlinux.org/news/427/)


Good luck and merry christmas...

---

### Post by jake43025 on 2008-12-23
i ended up changing the mirrors about 5 times but it still didnt work.i couldnt figure out how too merge the 2 files either.is there a way i can just download the files from the terminal screen,then install it? do u you really need too sync it if iam just gonna install openbox on it anyways.i mean i could just update the files once iam in openbox couldnt i?i was following this guide too too setup xorg:

[http://archux.com/page/installing-and-setting-xorg](http://archux.com/page/installing-and-setting-xorg)

---

