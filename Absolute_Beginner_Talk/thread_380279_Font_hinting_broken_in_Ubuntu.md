---
title: "Font hinting broken in Ubuntu?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by neji on 2007-03-09
So I just had to take screenshots to prove that fonts DO look different in Windows and Ubuntu. Both screenshots are taken in 1280x1024, and windows fonts are installed in Ubuntu. I have best-contrast enabled and fonts are set at 96 dpi. The screenshot uses the Georgia font and they are both set at the default size specified by the webpage.

Firefox in Windows:
[IMG]http://img02.picoodle.com/img/img02/7/3/9/f_screenWinm_b01aa24.png[/IMG]

Firefox in Ubuntu:
[IMG]http://img03.picoodle.com/img/img03/7/3/9/f_ScreenUbm_705c550.png[/IMG]

Notice that text is far less readable in Ubuntu. Some of the letters (note Uppercase W) are so badly misshapen.

Sorry, I want to love Linux but this is just unacceptable for me.

---

### Post by igknighted on 2007-03-09
If you go into the gconf editor you can select better font anti-aliasing.  Also a while back there was a thread in the Desktop Enviroments subforum with some tricks to improve font rendering, you could try that out.  Anti-Aliasing is set rather low by default because Ubuntu wants to be able to run on lots of computers, even low end ones that would get bogged down by heavy anti-aliasing.

EDIT: You might want to look into this too... supposed to give better rendering. [http://linuxreviews.org/howtos/xfree/xfs/](http://linuxreviews.org/howtos/xfree/xfs/)

---

### Post by Kateikyoushi on 2007-03-09
This is how it looks for me in feisty.

[[IMG]http://img158.imageshack.us/img158/6803/screenshotjq9.th.png[/IMG]](http://img158.imageshack.us/my.php?image=screenshotjq9.png)

---

### Post by Kateikyoushi on 2007-03-09
Check this thread it made my fonts look beautiful. [LINK]("http://ubuntuforums.org/showthread.php?t=235526&highlight=edgy+font")

---

### Post by dwblas on 2007-03-09
Installing xfs and xft, as per links in previous posts, improved my fonts.  I specifically had problems with truetype fonts.  Note that you have to update font paths and create font.cache and font.dir if they don't exist, but it is all very straight forward and easy to do.

---

### Post by neji on 2007-03-13
I installed the new packages. They're not perfect, but at least fonts are more readable now. Thanks.

---

### Post by Shatrat on 2007-03-13
You have seen the System -> Preferences -> Font configurator right?

---

### Post by neji on 2007-03-13
> **Shatrat said:**
> You have seen the System -> Preferences -> Font configurator right?

what about it?

---

### Post by Shatrat on 2007-03-13
> **neji said:**
> what about it?

You can easily change the font rendering and subpixel shading.
My fonts in linux look as well or better than any other OS.

---

### Post by neji on 2007-03-13
Yes I know about System > Preferences > Fonts. I picked best contrast before I took the screenshots. 

> 
My fonts in linux look as well or better than any other OS.


I'm sorry but they just don't:
[[COLOR="Sienna"]http://scobleizer.com/2006/08/17/linux-achilles-heel-fonts/[/COLOR]]("http://scobleizer.com/2006/08/17/linux-achilles-heel-fonts/")
[[COLOR="Sienna"]http://times.usefulinc.com/2006/01/16-fonts[/COLOR]]("http://times.usefulinc.com/2006/01/16-fonts")

Installing the new libreetype6, libcairo2 and libxft2 seemed to make fonts look better but hinting on some fonts still aren't perfect, but at least more readable now. Anyway thanks.

---

