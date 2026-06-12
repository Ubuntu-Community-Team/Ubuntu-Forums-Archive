---
title: "Synaptic Package Manager Error"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Green-Hat on 2006-10-27
Hi everyone,

Just recently i upgraded to Edgy and as I am trying to install nvidia-glx on my box it gives me this error: [http://img177.imageshack.us/img177/816/synapticva2.png](http://img177.imageshack.us/img177/816/synapticva2.png)
System Specs are as follows:

AMD64 X2 4000+
2GB DDR2 Corsair XMS2
320 GB Sata2
Sony DVD-r/CD-r drive
Asus M2N Sli Mobo.

Any suggestions on what might be causing this? Help would be greatly appreciated. 

Thanks in advance.

---

### Post by Green-Hat on 2006-10-27
I failed to mention that the Edgy CD is in the drive, and i'm still getting the error.

Another link to the result after i click cancel:

[http://img243.imageshack.us/my.php?image=synaptic2sf4.png](http://img243.imageshack.us/my.php?image=synaptic2sf4.png)

---

### Post by tronica on 2006-10-27
try going into the sources.list and commenting out the cdrom

> sudo gedit /etc/apt/sources.list

comment out the first two, which are cdrom. save that and the run

> sudo apt-get update

---

### Post by SunnyRabbiera on 2006-10-27
Nvidia gives most linux distros the hiccups...
sadly I have no solutions for you at the moment as I had simular things happen to me and i had no solutions to it.

---

### Post by tronica on 2006-10-27
also, a little off topic, which icons are you using?

---

### Post by Green-Hat on 2006-10-27
gartoon icons, you can find them in the Synaptic Package Manager by searching "gartoon".

I've tried disabling the cd-rom as a repository (source), but to no avail. It worked fine with Dapper, only i couldn't get the 64bit Dapper version working on my box...
](*,)

---

### Post by tronica on 2006-10-27
after you commented out the cdrom, did you sudo apt-get update?

---

### Post by tronica on 2006-10-27
try enabling the extra repos

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

and then try to install it again.

---

### Post by Green-Hat on 2006-10-27
Doing that as we speak... I hope this works. I didn't know there was more than one to comment out...

(a noob aren't I)

---

### Post by Green-Hat on 2006-10-27
It worked!! :) 

Thanks tronica! :KS

---

