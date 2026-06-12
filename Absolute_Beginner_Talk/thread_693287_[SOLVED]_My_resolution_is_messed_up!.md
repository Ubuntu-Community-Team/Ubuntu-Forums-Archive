---
title: "[SOLVED] My resolution is messed up!"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-02-10
After using a dual moniter setup with my laptop I decided to go back to one screen. I can't get my resolution right on my screen now though... Can anyone tell me what to do? I have it set to a 1200x800 moniter like usual but it wont give me the option for a resolution over 1024x786

---

### Post by JoshuaRL on 2008-02-10
Try:

```

sudo dpkg --reconfigure -phigh xserver-xorg

```
That will reconfigure your Xorg file, and there will be resolution choices in there.  When it's done, hit CTRL+ALT+Backspace to restart Xorg.

What type of hardware are you running?

And your name sounds familiar, have I helped you before?

---

### Post by -gabe-noob- on 2008-02-10
I'm not sure.... but your name is familiar as well, and I'll try that

---

### Post by -gabe-noob- on 2008-02-10
oh and intell 945 graphics chip 

1gig ram 

intel dual-core

Edit: that code gave me 
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
gabe@gabe-laptop:~$

---

### Post by JoshuaRL on 2008-02-10
Oops, typed it wrong.  Sorry.
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

That should work.

And I helped you on the Grub Error 17 thread.  Right before Sef came in and saved the day.

---

### Post by -gabe-noob- on 2008-02-10
Ooooh hehe, I ended up reinstalling but backingup all my files an' stuff

... 

Boy fun stuf!


gabe@gabe-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080210220927
gabe@gabe-laptop:~$ 

 thats what that spit out

---

### Post by -gabe-noob- on 2008-02-10
nvm did the ctrl alt backspace and it worked

Thanks man

---

### Post by JoshuaRL on 2008-02-10
SWEET!

+1 for ubuntuforums.org

---

### Post by -gabe-noob- on 2008-02-10
mhmm, is there anywere to go for those customized tuxes you guys have?

---

### Post by JoshuaRL on 2008-02-10
I just searched on Google for "tux avatar" and looked for a while for mine.

---

