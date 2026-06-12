---
title: "Assistance please!!"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by hyby on 2007-02-02
G'day guys,

Many maybe aware of my never ending saga to getting my sound to work. I think i may be getting close to solving my problem. However, i have a little hicup i hope you guys can help me.

I have recompiled my ALSA-modules that are supposed to solve my problems with various guides. However, when it comes to running the .deb file i have an error: 

davinci@davinci:~$ sudo dpkg -i alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb
(Reading database ... 91539 files and directories currently installed.)
Preparing to replace alsa-modules-2.6.17-10-386 1.0.14rc1-0ubuntu1 (using alsa-modules-2.6.17-10-386_1.0.14rc1-0ubuntu1_i386.deb) ...
Unpacking replacement alsa-modules-2.6.17-10-386 ...
Setting up alsa-modules-2.6.17-10-386 (1.0.14rc1-0ubuntu1) ...
FATAL: Could not open '/boot/System.map-2.6.17-10-386': No such file or directory

However, when i search the /boot/ folder i find that the file it requires is /boot/system.map-2.6.17-10-generic. 

Now, i was wondering is there a way i can rename this folder? or do i have go through the deb. file and find the line where i have to change so that i targets the xxx-generic folder rather than the xxx-i386 folder??

---

### Post by an.echte.trilingue on 2007-02-02
You can symlink it with ln -s.

---

### Post by hyby on 2007-02-02
Hi what is symlink -s? 

And what do i have to do? Sorry, my apologies for my poor linux level

I have installed symlinks, i have tried running the symlinks but i am not sure how to change the files

---

### Post by an.echte.trilingue on 2007-02-02
My appologies.  I assumed you would know since you are rolling your own stuff.

"Symlink" is short for symbolic link.  The command that links is called ln.  The syntax is pretty similar to cp or mv, so it goes 
```
ln [OPTION] TARGET LINK_NAME
```

You are making a symbolic link, so the option you want is -s.

Thus, the command you want is
```
sudo ln -s /boot/system.map-2.6.17-10-generic /boot/System.map-2.6.17-10-386
```

Hope this helps
-mat

---

### Post by xgrendel on 2007-02-02
I think what the responder was trying to say was to use the command

ln -s

See:

[http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html](http://www.thelinuxlink.net/lvlinux/resources/commands/ln.html)

They are basically the equivalent to a "shortcut" in some ways. For example, most websites allow you to access a domain name at "www.mysite.com" or just by going to "mysite.com" (sans www). This is often done with a symlink to connect a shortcut.

In your case, the command would be something like:

ln -s system.map-2.6.17-10-generic System.map-2.6.17-10-386

^command (ln)^ ^options(-s)^ ^name of file you want to link^ ^name of the new link^

Please note, you may want to be careful - sometimes when you create a symbolic link to a file that looks like what you want, it will turn out that it isn't the file that is needed and my have unintended consequences.

---

### Post by xgrendel on 2007-02-02
whoops, someone else posted inbetween....

---

### Post by hyby on 2007-02-02
thanks guys,


it looks like the alsa-module doesnt work via linking.

thanks...

---

