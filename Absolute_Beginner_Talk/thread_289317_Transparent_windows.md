---
title: "Transparent windows?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2006-10-30
I would like to make all of my windows and XMMS transparent, how do I go about doing this? I read a thread that said to get beryl, but I use ATI (but not the ATI driver, I use the glrfx(sp?) one, so Im not sure if it will work, any suggestions?

---

### Post by slimdog360 on 2006-10-30
you can try the built in compositor in xfce or kde. I havent used the one in kde yet but Ive heard its buggy. The one in xfce is good, you can go to [http://www.psychocats.net/ubuntu/xubuntu]("http://www.psychocats.net/ubuntu/xubuntu") to see how to install the xubuntu desktop (which uses xfce).

to get the compositor working try [http://support.zenwalk.org/index.php/topic,583.0.html]("http://support.zenwalk.org/index.php/topic,583.0.html")

This will give you the tranparent windows but none of the fancy effects like in beryl.

---

### Post by Daergeth on 2006-10-30
thank you :)

---

### Post by John.Michael.Kane on 2006-10-30
Have a read.
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)
[http://ubuntuforums.org/showpost.php?p=1547638&postcount=7](http://ubuntuforums.org/showpost.php?p=1547638&postcount=7)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)
[http://ubuntuforums.org/showthread.php?t=271123&highlight=beryl+ati](http://ubuntuforums.org/showthread.php?t=271123&highlight=beryl+ati)

**Note: you may have to update your drivers**

Slimdogs method does offer medium effects for those on low resource machines.

---

### Post by d3v1ant_0n3 on 2006-10-30
Apparently (see [ HERE](http://forum.beryl-project.org/topic-5831-aiglx-beryl-fglrx-edgy-possible)), flgrx and compositing don't play well together.

You might be able to install Beryl using the 'radeon' drivers tho.

I found these howtos (thankyou, Pricechild's sig)

[ For Dapper](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

[For Edgy](http://www.ubuntuforums.org/showpost.php?p=1547638&postcount=7)

*edit* beaten to it.

---

### Post by Daergeth on 2006-10-30
Ok so I found a guide that helped me install beryl on my system, I see the green emerald on the panel, but when I make any changes nothing happens!

when I type 'beryl-manager' it gives me

> XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

Any ideas?

---

### Post by d3v1ant_0n3 on 2006-10-30
Is composite enabled in xorg.conf?

I have no idea for ATI, but for my intel, I had to add this section to xorg.conf:

Section "Extensions"
Option "Composite" "true"
EndSection

---

