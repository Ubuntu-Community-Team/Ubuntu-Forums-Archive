---
title: "Screen flickering"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2007-05-01
Ever since I installed Beryl my screen has been flickering. Everything works fine, except that every 3-5 minutes it turns black for a split second. It's not a big issue, but it's really annoying.

Does anyone know what the problem is? Is it my videocard driver?

What I did to install Beryl was:
1.) Used Feisty's new restricted driver thing to enable my Video Card driver (it's an nVidia 7400).
2.) Typed: "sudo nvidia-xconfig --add-argb-glx-visuals --composite"
3.) Changed the default debth in xorg.config to 24.
4.) Installed Beryl using "sudo apt-get beryl-manager emerald-themes" (Or something like that).

---

### Post by toddward on 2007-05-01
Have you tried disabling Beryl?  Can your video card handle it?

---

### Post by RussianVodka on 2007-05-01
> **toddward said:**
> Have you tried disabling Beryl?  Can your video card handle it?

Yeah, my video card can handle Beryl just fine. Also, once I disable it, the same thing goes on in metacity. I've had this same problem on my previous laptop, which had a GeForce 7600, and I was able to fix it. I don't remember how I did it, but I do remember that a few days after "fixing" it, X crashed completely.

I think what I did last time was use Envy to install a newer driver. But I didn't bother removing my old one, which may have been the reason for the crash. What do you think?

---

### Post by zvacet on 2007-05-01
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

