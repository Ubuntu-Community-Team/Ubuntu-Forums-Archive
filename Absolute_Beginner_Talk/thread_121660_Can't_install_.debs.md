---
title: "Can't install .debs"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Piggah on 2006-01-25
Hi,

I've followed all the other directions I've found and I still am not able to install .debs. I'm able to get a .deb out of .rpm, so it's not a problem there. The most recent thing I've tried to install was gaim beta2, so I'll post the results of that..

> 
nick@nick1:~/Desktop$ sudo dpkg -i gaim_2.0.0-1_i386.deb
dpkg - warning: downgrading gaim from 1:1.5.0-1ubuntu3 to 0:2.0.0-1.
(Reading database ... 83269 files and directories currently installed.)
Preparing to replace gaim 1:1.5.0-1ubuntu3 (using gaim_2.0.0-1_i386.deb) ...
Unpacking replacement gaim ...
dpkg: error processing gaim_2.0.0-1_i386.deb (--install):
 trying to overwrite `/usr/share/applications/gaim.desktop', which is also in package gaim-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 gaim_2.0.0-1_i386.deb

This is what happens every time I try to install a deb file. 

Thanks in advance.

---

### Post by kaamos on 2006-01-25
You should first remove gaim and gaim-data.
```
sudo apt-get remove gaim gaim-data --purge
```

---

### Post by Piggah on 2006-01-25
I've tried that and I still get the same error message. 

Thanks

---

### Post by kaamos on 2006-01-25
what is the output of "dpkg -l | grep gaim" ?

---

### Post by Piggah on 2006-01-25
> ii  gaim                                   1.5.0-1ubuntu3 multi-protocol instant messaging client
ii  gaim-data                              1.5.0-1ubuntu3 multi-protocol instant messaging client - da


thanks

---

### Post by kaamos on 2006-01-25
The *ii* means that the gaim packages are still installed. What happens when you try to remove them with synaptic?

---

### Post by Piggah on 2006-01-25
After I remove with synaptice nothing comes up.

I'll try to install again..

edit: This time is appears to have installed, but now it's running gaim beta1 for some reason... =\

---

### Post by kaamos on 2006-01-25
what does "dpkg -l | grep gaim" show now ?
You could also try to locate if you have more that one gaim installation with
```
gaim --version
```
This shows the version
```
which gaim
```
This shows the gaim executables in the system.

Hope this helps!

---

### Post by Piggah on 2006-01-25
> ii  gaim                                   2.0.0-1 A Gtk+ based multiprotocol instant messaging


It still shows Gaim beta1 with that. 

It also only shows one executable. 

nick@nick1:~$ gaim --version
Gaim 2.0.0beta1
nick@nick1:~$ which gaim
/usr/local/bin/gaim

Thanks

---

### Post by kaamos on 2006-01-25
That is just what you were trying to install, right?
> nick@nick1:~/Desktop$ sudo dpkg -i gaim_2.0.0-1_i386.deb
> ii gaim 2.0.0-1 A Gtk+ based multiprotocol instant messaging
So it looks good to me.

---

### Post by JoshHendo on 2006-01-25
Umm. Why don't you just upgrade gaim in synaptic? The problem is that it is already installed.

---

### Post by Piggah on 2006-01-25
Yes. 

It's just that when I check the version in the Gaim client it still says beta1, so that lead me to believe it wasn't working. Could just be a glitch I suppose..


Thanks for your help :)

edit: > Umm. Why don't you just upgrade gaim in synaptic? The problem is that it is already installed.
The version in synaptic is 1.5 I'm pretty sure. I was unable to get anything other than that at least.

---

