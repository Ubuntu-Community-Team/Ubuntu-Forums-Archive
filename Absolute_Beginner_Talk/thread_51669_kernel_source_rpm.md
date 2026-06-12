---
title: "kernel source rpm"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by kybishop on 2005-07-24
I just installed ubuntu, and am trying to get my wireless card working with ndis wrapper.

In order to do this i need an .rpm file for my kernel.

Does anyone know where to get a .rpm for the linux kernel 2.6.10-5-386?

I've tried google but no luck.

If you'd like to send it to me, although please post just incase anyone else asks the question, you can send it to [email]kybishop@gmail.com[/email]

much thanks, kyle

edit: not necceserally (sp?) a .rpm file, but something with which to install the kernel source.

---

### Post by Xian on 2005-07-24
Why does it have to be a rpm file?
Ubuntu uses a deb format but it should work just as well.

---

### Post by kybishop on 2005-07-24
[QUOTE=Xian]Why does it have to be a rpm file?
Ubuntu uses a deb format but it should work just as well.[/QUOTE]
 whatever would work, it just talked a lot about rpm files in the wiki page for ndis wrapper.

---

### Post by Xian on 2005-07-24
Open a terminal:

```
$ sudo apt-get install linux-source-2.6.10
```

---

### Post by kybishop on 2005-07-24
[QUOTE=Xian]Open a terminal:

```
$ sudo apt-get install linux-source-2.6.10
```[/QUOTE]
 got the messege: linux-source-2.6.10 is not available

then it says someting about it maybe being deleted or only referenced

---

### Post by Xian on 2005-07-24
Enable the [Extra Repos](http://ubuntuguide.org/#extrarepositories).
Then do a 'sudo apt-get update' session.

If that doesn't work here's a direct [LINK](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb).

---

### Post by kybishop on 2005-07-24
no internet on the computer, so i downloaded the .deb file and put it on a cd.

what am i doing with the file now that i have it?

---

### Post by Xian on 2005-07-24
[QUOTE=kybishop]no internet on the computer, so i downloaded the .deb file and put it on a cd.

what am i doing with the file now that i have it?[/QUOTE]
Heh. Well, that would explain why apt-get didn't work.

Transfer the file to your /home/username/ directory.
Open a terminal and input the following:

```
$ sudo dpkg -i linux-source-2.6.10_2.6.10-34.3_all.deb
```

---

### Post by kybishop on 2005-07-25
grr

Well I think the kernel sources installed fine, as there is now a file called linux sources-2.6.10.tar.bz2 inside my /usr/src folder, thanks xian.

Now I'm having trouble with ndiswrapper

I ran the code:
```
ln -s /usr/src/linux-source-2.6.10.tar.bz2 /lib/modules/2.6.10-5-386/build
```

Then I went to my ndis folder, and ran make install, but still getting the "Can't find kernel sources in /lib/modules/2.6.10-5-386/build" error.

Am I doing something wrong?

---

### Post by codejunkie on 2005-07-25
[QUOTE=kybishop]grr

Well I think the kernel sources installed fine, as there is now a file called linux sources-2.6.10.tar.bz2 inside my /usr/src folder, thanks xian.

Now I'm having trouble with ndiswrapper

I ran the code:
```
ln -s /usr/src/linux-source-2.6.10.tar.bz2 /lib/modules/2.6.10-5-386/build
```

Then I went to my ndis folder, and ran make install, but still getting the "Can't find kernel sources in /lib/modules/2.6.10-5-386/build" error.

Am I doing something wrong?[/QUOTE]
it could  be that most rpm based distros refer to the kernel headers package as kernel source try installing the kernel headers package for your kernel and the build-essential package this package provides the basic stuff needed to compile software.

---

### Post by poofyhairguy on 2005-07-25
Um....did you try this way?:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

---

### Post by kybishop on 2005-07-25
got the kernel source from [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb), so it was a .deb.

Where could I find the kernel headers package, and build essential package.

have to slow it down for me, first time linux user as of today.

---

### Post by codejunkie on 2005-07-25
[QUOTE=kybishop]got the kernel source from [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb), so it was a .deb.

Where could I find the kernel headers package, and build essential package.

have to slow it down for me, first time linux user as of today.[/QUOTE]

they should be on your ubuntu cd just find what version of kernel headers you need
open the terminal and type ```
uname -r
``` it will list something like 2.6.10-[COLOR=Blue]386[/COLOR],  2.6.10-[COLOR=Blue]686[/COLOR] etc the last part i listed in blue is what to check for so if you have the -386 kernel you would install the linux-headers-386 package.

---

### Post by kybishop on 2005-07-25
[QUOTE=poofyhairguy]Um....did you try this way?:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)[/QUOTE]

YAY! Finally got it working, wish i knew about that method sooner.

---

### Post by Xian on 2005-07-25
[QUOTE=kybishop]Then I went to my ndis folder, and ran make install, but still getting the "Can't find kernel sources in /lib/modules/2.6.10-5-386/build" error.

Am I doing something wrong?[/QUOTE]
Sounds like you might also need the [linux-headers-2.6.10-5-386](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-headers-2.6.10-5-386_2.6.10-34.3_i386.deb).

---

