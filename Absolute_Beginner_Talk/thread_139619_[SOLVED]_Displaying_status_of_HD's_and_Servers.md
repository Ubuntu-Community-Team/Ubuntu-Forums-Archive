---
title: "[SOLVED] Displaying status of HD's and Servers"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-03-04
Is there any program/script/native support in Ubuntu 5.10 that will display my hard drives -- more specifically their size and use?? In the same genre, is there anything like that for my remote servers? I have my remotes servers and windows data hard drive mounted currently... but there are no statistics on them currently (size/use, etc.) so I was wondering if anyone knows of how I can do this... or will I have to learn C++ and write it myself lol?

(The closest thing I can thing of is *shutters* Konfabulator for Windows... I don't need it to be so shiny by any means... but I'm a man that likes his stats :) )

Thanks.

---

### Post by Virak on 2006-03-04
Something kind of like [this](http://img215.imageshack.us/img215/6119/screenshot8us.jpg)?

---

### Post by altonbr on 2006-03-04
Wow... yeah basically like that!

BUT... I was wondering if it could do ntfs hard drives and remote servers??

Such as space, hits etc.

---

### Post by Virak on 2006-03-04
Yes, it can do NTFS partitions; /media/hda1 (in the screenshot) is an NTFS partition. As for remote servers, I wouldn't know (as I haven't tried yet), but you can check its [home page](http://conky.sourceforge.net/) to see if it's what you're looking for. If you want to install it, it's in the repos, so just do "sudo apt-get install conky".

---

### Post by altonbr on 2006-03-04
mmm, I'll try it out. Thanks!

---

### Post by altonbr on 2007-07-05
Well now in Ubuntu Feisty there is a package called 'baobab' if anyone wants to run it. It's also known as "Disk Usage Analyzer".

---

