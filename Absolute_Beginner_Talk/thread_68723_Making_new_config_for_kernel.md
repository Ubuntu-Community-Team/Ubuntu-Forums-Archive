---
title: "Making new config for kernel"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by hovendal on 2005-09-24
Hello everybody..

I know how to configure a new kernel through menuconfig, how to compile and install the new kernel and so on... But i now wonder if it is possible to "automate" the process of making a new configuration to compile into the kernel - i mean with my current settings, drivers and modules compiled into the kernel - WITHOUT the use of menuconfig.... Im very happy with how my system works right now, but i so really would like to compile everything in to the kernel.... is it possible to do that ??

Regards and thanks in advance...

---

### Post by heimo on 2005-09-24
Have you seen tseliots howto?
[http://ubuntuforums.org/showthread.php?t=56835]("http://ubuntuforums.org/showthread.php?t=56835")

make oldconfig does configuration based on current config. When you're compiling, the config file that will be used is in /usr/src/linux/.config and you can find config files which were used for packaged kernels (installed on your system) in /boot/ directory
 ```
ls /boot/config*
``` 
You can copy anyone of those to /usr/src/linux/.config and run make oldconfig to configure only the changes (in case you're compiling other version and some new configuration options have been added).

Hopefully I made some sense. :) If I didn't answer your question, please go ahead and ask. :)

EDIT: Oh! This may be quite obvious for most people, but these config files are plain text files and can be opened and edited in text editor. 

And about compiling everything into kernel... You will probably run into problems with size of your kernel (I'm not sure if these still apply), but I guess it's doable. However I don't see much benefit of doing that unless you have some very good reason to disable kernel modules. :-/ :-\ But it sure can teach you a lot about your system!

---

### Post by hovendal on 2005-09-24
Thanks alot for the fast response!

I just have one question though... After ive done make oldconfig, do i have to make && make modules && make install or ?? What is the next step after make oldconfig ? just to copy the new .config to boot or ?

Thanks again...

Edit.. BTW! I dont have that many old config files in boot because i havent recompiled my kernel yet... So im running the standard kernel with the extra modules that i have added...

Youre saying theres no point in compiling the modules into the kernel ?? Or did i misunderstand... ?

---

### Post by heimo on 2005-09-24
After configuring you continue compiling as usual. I strongly recommend that you check tseliots great howto and use "ubuntu-way" of compiling - this will make you a deb package (debian software package). It's good practise to install all software on your system using package management (whenever possible). This makes it easy to install it on another system and uninstall when neccessary. :)

That is: use *make-kpkg*

---

