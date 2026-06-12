---
title: "Boot Screen Kubuntu --&gt; Ubuntu"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-02-19
I installed Kubuntu-desktop, but uninstalled it.  Now my boot screen as the computer boots is Kubuntu instead of ubuntu.  How can I revert that back?

---

### Post by mojorising on 2007-02-19
I'm guessing the Kubuntu meta package replaced your usplash-artwork.png with its own. Not 100% sure but I bet that's it.

Try opening a command line and typing:
```

sudo find / -name usplash-artwork.png [enter]

```

Use a graphics program or web browser to open that file and see what it looks like. If it is the Kubuntu splash screen, then there lies the problem. 

Fixing the issue may be more complicated. This link might prove useful:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

I haven't tried to perform such an operation so I'll stop short of providing you more details. This seems like something that won't be too much trouble to fix given the info at the link I provided. Of course, you could just leave the splash like that unless it really bugs you.

Hope that helps you. 

Mike

---

### Post by brandoncolorado on 2007-02-19
Got it.  Your post pointed me in the right direction.

Synaptic - reinstall Usplash.

---

