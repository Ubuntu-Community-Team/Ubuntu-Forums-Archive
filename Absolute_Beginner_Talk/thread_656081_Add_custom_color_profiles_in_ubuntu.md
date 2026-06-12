---
title: "Add custom color profiles in ubuntu????"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by maduranga on 2008-01-02
Hello.. The LCD I'm using doesn't have most accurate colors. So in windows, I add my custom color profile to get the best color. (wich is a *.icm file downloaded from the net)

 How can I do the same in ubuntu? now my colors arn't good.

---

### Post by nick_h on 2008-01-02
What video card do you use?

If it is an nvidia card then you can use the nvidia-settings utility.

---

### Post by maduranga on 2008-01-02
I use nVidia GeForce FX 5200. Can you tell me how to do that? Do I need to install nVidia from Envy or from repos?

---

### Post by LowSky on 2008-01-02
just enable proprietary drivers under system>admin> resricted drivers manager. Yuo can edit the themes to use what ever colors you want unders system>preferences>appearance. It even allows you took pick colors if you customize the theme

---

### Post by rax_m on 2008-01-02
Hi, 

There's quite a bit of reading here, but this may help: [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

Apparently (if you skip to the bottom), the ICC has to be applied to each ICC aware application. 

The article also lists a few programs that can be used on Linux to generate profiles. 

HTH
Rax

---

### Post by nick_h on 2008-01-02
> just enable proprietary drivers under system>admin> resricted drivers manager.
Yes, that's the easiest way.  Then access the settings program by typing the following command at the terminal:
```
nvidia-settings
```

---

### Post by maduranga on 2008-01-04
is it possible to add the *.icm color profile to linux?

---

### Post by nick_h on 2008-01-04
According to the link that rax_m posted:
>  Linux applications are currently unable to automatically detect display profiles, so the profiles must be applied manually in each program.

Although there is no designated place to store device profiles on Linux, /usr/share/color/icc/ has become a de facto standard, used by several applications.

You can apply the profile to applications that support the ICC standard but not to linux itself.

---

