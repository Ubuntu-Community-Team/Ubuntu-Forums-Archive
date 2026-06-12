---
title: "New Ubuntu distribution?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-03-30
TOPIC RESOLVED

this feisty fawn i keep hearing about.  when's it going to be released and what's going to be included.  particularly is it going to be able to do the 3d cube effect and wobble the windows like beryl?  i would really like to get these effects ASAP, but don't want to compromise my system with a beryl beta install.  anyone know when a stable beryl beryl release will be made for ubuntu?

---

### Post by overdrank on 2007-03-30
> **locke.dragon said:**
> this feisty fawn i keep hearing about.  when's it going to be released and what's going to be included.  particularly is it going to be able to do the 3d cube effect and wobble the windows like beryl?  i would really like to get these effects ASAP, but don't want to compromise my system with a beryl beta install.  anyone know when a stable beryl beryl release will be made for ubuntu?

Hi, here is what I found on Feisty,
[https://wiki.ubuntu.com/FeistyFawn](https://wiki.ubuntu.com/FeistyFawn)
Now for beryl, I am using it on a couple of systems and have had good luck. But there is always a case that does not go as well as mine. It really depends on you video card and ram if it will be worth the trial. Good luck !

---

### Post by locke.dragon on 2007-03-30
what are the risks of beryl?  if it screwed up, couldn't i just re-install ubuntu?  or would it mess up my windows partition too?  i just had to re-format, so i don't have anything important on my hard drive yet.

---

### Post by lamalex on 2007-03-30
the only risk is a headache, you just uninstall it and you're done. It's not like experimental surgery. you might need to reconfigure your xorg.conf but that's all. It's not like beryl is going to fry your power supply or anything.

---

### Post by locke.dragon on 2007-03-30
so beryl's just a program that you can configure to run at startup?

---

### Post by lamalex on 2007-03-30
Yeah, it's just an OpenGL accelerated window manager. It's not like a program that overclocks your hardware. You can have it start at startup or can start it after, it doesn't matter.

---

### Post by arbulus on 2007-03-30
Yeah, both Beryl and Compiz are separate programs that are installed and configured. But being in beta, they can still be kinda buggy on some systems.  You just have to make sure you have 3D accelerated drivers for your video card, and then edit some xorg.conf settings.  But if it goes sour, then you can uninstall and restore your xorg.conf settings.  It's always a good idea when you edit a config file to back it up before hand in case somethign goes wrong.  Like this:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

And then when you want to restore the backup, just switch it around.

```
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

From what I read, Compiz may be an option on install in the Fiesty release, but I'm not certain on that.  I've heard a lot of conflicting info.  Plus, I recently heard on the Linux Action Show podcast that Beryl and Compiz are remerging, so if that's the case, then i would wonder how it would play out as a feature of Fiesty.  I guess we'll have to wait and see what happens.

---

### Post by locke.dragon on 2007-03-30
and is this a trustworthy guide?  other than that, i think i'm sold on the idea.

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

---

### Post by locke.dragon on 2007-03-30
and how can i know which video card i have?  the tutorial's for ATI cards.  i'm not sure what i have.  would it make a difference?

---

### Post by overdrank on 2007-03-30
> **locke.dragon said:**
> and how can i know which video card i have?  the tutorial's for ATI cards.  i'm not sure what i have.  would it make a difference?

Yes it does  try the command lspci in terminal and that will tell you your video card. Good luck!

---

### Post by locke.dragon on 2007-03-30
would it be this one?

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

and is this the same as the ATI driver?

---

### Post by overdrank on 2007-03-30
> **locke.dragon said:**
> would it be this one?

```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

and is this the same as the ATI driver?

No that is not ATI do a search in here for that intel chipset and it will lead the way. :(

---

### Post by lamalex on 2007-03-30
Intel chipsets are generally way easy as their drivers are open souce. look in the beryl wiki for a good howto.

---

### Post by locke.dragon on 2007-03-30
could anyone tell me how to do this?

Run 'modconf' and scroll down to kernel/drivers/video/i810 (substute with your determined driver, and enable it)

---

### Post by gruffy-06 on 2007-03-30
Installation should be as easy as installing the packages from the repositories. You may have to add external repositories.

Follow the instructions on [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

If that doesn't work, try [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

---

### Post by locke.dragon on 2007-03-30
will that first tutorial work with my chipset?

---

### Post by locke.dragon on 2007-03-30
what's this that's mentioned in the first tutorial?  a graphics card?  

"AIGLX"

---

### Post by locke.dragon on 2007-03-30
ok.  i follow the instructions, but right as i try to install it, it gives me this...

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package beryl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package beryl has no installation candidate

```

help?

---

### Post by locke.dragon on 2007-03-30
ok.  got it working.  thanks for the help guys.  now i just need to figure out how to use 1280x800 resolution.  :P

---

### Post by locke.dragon on 2007-03-30
thanks for the help and info guys.  i downloaded beryl, installed, and it's working like a charm.  UBUNTU RULES!!!

---

