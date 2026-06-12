---
title: "Gutsy Compizfusion and Dell M1330"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by glaringdarkmatter22 on 2007-10-21
I Recently tried out the new gutsy live cd with my dell M1330 It works great in most areas and finally the screen resolution is correct! However, I am unable to enable the Desktop Effects. This puzzles me as i know my graphics card can at least handle windows vista areo which I have heard is more demanding then compizz...  In any case I was wondering if there is a way around this or if it is just my Intel card (which i chose over nvida in hope of better Linux support) I have the 	Intel Integrated Graphics Media Accelerator 3000 for my XPS M1330 which is I believe the 965 m express chip set.  ALso I think Ubuntu already has the driver but i may be wrong . If anyone knows how to make it all work  I would be greatfull for the help. 

Thanks,
Christian

---

### Post by akniss on 2007-10-23
The X3000 and X3100 have been blacklisted by compiz-fusion on purpose.  The basic explanation is that playing video with desktop effects enabled causes a crash.  More on that here:
[http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/](http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/)

Once you understand the problem, you can enable effects anyway by following the instructions here:
[http://ubuntuforums.org/showpost.php?p=3574331&postcount=1](http://ubuntuforums.org/showpost.php?p=3574331&postcount=1)

Be aware, however, that if you play some video with effects enabled, something is guaranteed to break.

---

### Post by glaringdarkmatter22 on 2007-10-24
Thanks for the info!

---

### Post by glaringdarkmatter22 on 2007-10-26
I attempted to bypass the blacklisting by running sudo mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager but it denies me permissionn any thoughts anyone?

---

### Post by akniss on 2007-10-27
> **glaringdarkmatter22 said:**
> I attempted to bypass the blacklisting by running sudo mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager but it denies me permissionn any thoughts anyone?

You shouldn't have used sudo.  The instructions on the thread do not use sudo.  Since the config file is in your home directory it needs to have your permissions, not root.  Try removing what you've done and copy the command in Amaranth's post EXACTLY.

```
sudo rm -R ~/.config/compiz
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by achoi02 on 2007-10-30
> **akniss said:**
> You shouldn't have used sudo.  The instructions on the thread do not use sudo.  Since the config file is in your home directory it needs to have your permissions, not root.  Try removing what you've done and copy the command in Amaranth's post EXACTLY.

```
sudo rm -R ~/.config/compiz
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

thnx this worked for me:)

---

### Post by pormogo on 2008-02-18
I just recently ordered one of the XPS M1330's with ubuntu pre installed. I was thinking about ordering the Windows based 1330 with the Nvidia video card however in the end I decided that I really wanted to "vote" for linux with my consumer dollar and buy into the ubuntu/dell partnership. In the end I figured that the integrated intel graphics chip would be supported extremely well. I'm a little let down to see that compiz has blacklisted the card. 

How stable is it after using the work around? I don't really watch much video on my laptop (outside of flash video in firefox) and from what I understand that's where the issue here lies.

---

