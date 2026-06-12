---
title: "download software"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by cmongini on 2006-01-28
hi 
couldnt´ find any answer in the search...i would like to download dvd::rip and skype
they are both not in my repositories. is there a command in the terminal that allows me to put in the web adress of the download, and then the pc installs it automatically? "sudo apt-get install program name" works only if i have the program in the repositories....
thanks !

---

### Post by dueY on 2006-01-28
Do you have backports in your sources.list?

---

### Post by cmongini on 2006-01-28
no, how do you get it?

---

### Post by psomas on 2006-01-28
check this out : [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
and the ubuntu5.10 guide: [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
they say how do add extra repositories...

---

### Post by DiscoKiller on 2006-01-28
i`m not sure how this works but try this to generate a sources list

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

then...

go to terminal and type

 sudo gedit /etc/apt/sources.list

then copy the generated list and paste it to your sources list (overwrite the lot) and click save.

then do sudo apt-get update

you should be able t install skyp through synaptic then

---

### Post by cmongini on 2006-01-28
thanks!!

---

