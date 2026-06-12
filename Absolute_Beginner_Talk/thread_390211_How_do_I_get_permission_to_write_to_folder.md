---
title: "How do I get permission to write to folder?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-21
Im trying to copy a theme to the skins2 folder for VLC media player but I get the error:

You do not have permission to write to this folder.

How do I get permission?

---

### Post by bulldog on 2007-03-21
You need to put sudo in front of your command and provide your password.

---

### Post by Brucey on 2007-03-21
Is there any way I could do it without having to use commands?  I´d like to just drag and drop the files in.

---

### Post by bulldog on 2007-03-21
Don't know,I use the command line to copy or move files,so you have to try.
But you need to be root to do so I think.

---

### Post by sad_iq on 2007-03-21
Press ALT+F2 and enter **gksu nautilus**...that should open nautilus as root and it will allow you to copy paste anywere.

---

### Post by linuxisgod on 2007-09-20
sad_iq i ******* love u soooo much thank wow a true hero what a life saver thank youuuuuuuuuuuuuuuuu ssoooooooo mucccchhhhhhhhhh

---

### Post by go_lanche on 2008-04-07
sad_iq FTW! Thank you so much.

---

### Post by dndrich on 2008-04-07
Yes, I am with you that I like a graphical method for this kind of thing, so I also use Nautilus as root sometimes.  But you have to be really careful with that, as you can really cause major problems if you delete something important, or over-write something.  There is a reason not to be root for most things!  So, be careful out there!  But I do the same thing...

---

### Post by JoshuaRL on 2008-04-07
> **dndrich said:**
> Yes, I am with you that I like a graphical method for this kind of thing, so I also use Nautilus as root sometimes.  But you have to be really careful with that, as you can really cause major problems if you delete something important, or over-write something.  There is a reason not to be root for most things!  So, be careful out there!  But I do the same thing...

Right, which is why you only use that command if you are told you need to.  You can hose your system fast if you just start deleting stuff.  But when needed, this is the safest and supported way to do that.  Sudo and gksu/gksudo are the appropriate ways to deal with root privileges in Ubuntu.

---

### Post by SunnyRabbiera on 2008-04-07
yeh currently there is no real graphical tool to get into superuser mode for nautilus...
wish there were, I suggested one but I got flamed out for it...

---

### Post by JoshuaRL on 2008-04-07
> **SunnyRabbiera said:**
> yeh currently there is no real graphical tool to get into superuser mode for nautilus...
wish there were, I suggested one but I got flamed out for it...

I'm sure you of all people already know this, but you could probably make one with a little bash script and Alacarte.

It'd be in the menu and everything.

---

### Post by aysiu on 2008-04-07
> **SunnyRabbiera said:**
> yeh currently there is no real graphical tool to get into superuser mode for nautilus...
wish there were, I suggested one but I got flamed out for it...
[I suggested this as well but didn't get flamed](http://ubuntuforums.org/showthread.php?p=2456140#post2456140), but it still hasn't been implemented.

We have something very close, though, if you create a launcher or keyboard shortcut for ```
gksudo nautilus
```

---

### Post by lackofcreativity on 2008-04-07
You only need to get superuser privileges one time. Open a terminal, then cd to the directory containing the folder you want to write to. Do:

```
sudo chmod a+rw ./[insert folder name here without brackets]
```

That *should* do it.

---

### Post by dndrich on 2008-04-07
I have a launcher as described above, since I use root Nautilus fairly often.  I just click and go!

---

### Post by JoshuaRL on 2008-04-07
Cool.

Just be careful.  Do your research about root and sudo and you should be fine.

Happy Ubuntuing!

(is that a word?)

---

