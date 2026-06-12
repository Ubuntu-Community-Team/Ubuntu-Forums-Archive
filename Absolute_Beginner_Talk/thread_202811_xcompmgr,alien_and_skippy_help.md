---
title: "xcompmgr,alien and skippy help"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by J.J Morrison on 2006-06-24
I downloaded it and it won't do anything I ran it in the trminal and it said "no composite extension."  I installed skippy too and it won't work either. I ran it in the terminal again and it gave me this
WARNING: Couldn't load config file '/root/.skippyrc'.
WARNING: $HOME/.skippyrc not found loading default config.

I heard expocity was better than skippy so I downloaded as .rpm and I read you could change it to a deb file with Alien. So I installed Alien and now I don't know to get Alien running? I am so confused](*,)

---

### Post by siccness on 2006-06-24
sudo alien rpmfilename.rpm &#8211;to-deb

---

### Post by J.J Morrison on 2006-06-24
It says

File "expocity-2.6.2-100.lintellect.expo.i686.rpm" not found.

but it is right on my desktop

---

### Post by angkor on 2006-06-24
Open up a terminal:

```

cd Desktop
sudo alien [packagename]

```

What are you trying to accomplish with xcompmgr btw?

---

### Post by gborzi on 2006-06-24
At the end of your /etx/X11/xorg.conf file you must put the following 3 lines (at least)
> Section "Extensions"
       Option "Composite" "Enable"
EndSection
also you may need to put the > Option  "AllowGLXWithComposite" "true" in the Device section. It is needed to have glx enable along with the Composite extension. Finally restart Xorg (Ctrl-Alt-Backspace).

---

