---
title: "Help me clean my mess in Latex"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by felipe82 on 2007-08-08
Hi.
I decided to install TexLive in my system, so I downloaded the .iso from their site (I wanted to install it in a notebook at my university too and the internet connection is really slow during the day,  so that's why I didn't use synaptics in the first place). I ran the sh install-tl.sh and installed the 1.1GBs of it (I THINK). The problem is that Kile never found the packages, so I installed texlive-full from Synaptics and now it works.

Now I have way too many texmf folders and I don't know which one is the one Kile is using. I'm going to format this PC anyway, but I want to install the .iso instead of using synaptics (call me stupid, but it's just because 1.1GB>400mb or so that synaptics installs), and I realized later that the installer for the iso had the option for changing the install path. I guess the question at the end of the day is 

"where the hell is my texmf folder? (the one that counts)"

I think that there should be a console command for the $PATH or something like that, right?

thanks a lot

---

### Post by arijarot on 2007-08-08
i don't know if this will help but you can type ```
whereis
``` in the terminal... e.g., ```
whereis texmf
```

---

### Post by frisket on 2007-08-13
What you've done now is installed *two* entirely separate TeX systems in parallel.

Kile will only work unmodified with the distribution you installed through Synaptic, because they're both ubuntu-aware, and the directory locations have been modified to make them cooperate.

The TUG .iso distribution is the generic work-anywhere one, but Kile doesn't know this. 

You need to get rid of one of them in its entirety otherwise you'll end up in a horrible mess.

The TUG one is more up to date and keeps things in the places people expect them to be in,
but it's independent of any particular breed of Linux, so Ubuntu doesn't know it exists.

The one installed via Synaptic is known to Ubuntu, and works with kile out of the wrapper, but adding extras to it is difficult because the directories are in different places to where the generic TeX documentation assumes they are.

Both work fine, but you need to pick one or the other, not both.

---

### Post by felipe82 on 2007-08-13
Thanks for the info.
I had to format my PC anyway so I'm using the synaptics version now.
For future reference anyway: what I had problems specifically was removing the TUG .iso installation (could not find any uninstall instructions in the docs) or make Kile aware of this installation.
¿any idea about that?

---

