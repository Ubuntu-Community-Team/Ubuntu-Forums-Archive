---
title: "Wine Problem! &quot;Help&quot;"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Lance1 on 2008-01-02
Hi all!
Over the holidays I downloaded VMware with Ubuntu 7.10 Gutsy Gibbon bundled in. It was so slick no Ubuntu installation, just install VMware and go! The first thing I did was install all the updates and then “Wine” because I’m a Windowsoholic  and still need a fix at times :-\" The problem I am having is with Wine. I installed it and then installed some win32 app’s to test. The app’s install without a hitch and are there in Wine programs so I added them into application settings. I run the app and it shows in the lower task bar for about 10 sec and disappears. It looks as though the app is starting but doesn’t. What is it that I’m doing wrong?

---

### Post by Zafrusteria on 2008-01-02
Try running the commands from a command promt and looking at any error message that is output.

The symptoms you describe could be caused by something as simple as a misspelled directory name.

example command line.

```
env WINPREFIX='Linux/path/to/.wine" wine "C:\Program Files\whatever\programe.exe"
```

You can also try changing to the directory where the windows exe is located and just running

```
wine ./program.exe
```

---

### Post by LowSky on 2008-01-02
your trying to run windows apps in ubuntu which is in a VM on a winodws box... that is sick, I think  you need help...LOL

What apps are you tring to run

---

### Post by Lance1 on 2008-01-02
Hi LowSky.

YA! I know I’m sick… But braking free from an addiction is day by day. So as I am a Windowsoholic  I need folks like you! Think of this as a sort of WAA. (Windows Aoholic Anonymous) The app’s I am trying to run are Diskeepr and Printkey2000.

---

### Post by metalpancake on 2008-01-02
I have a similar problem with a windows digital tv dongle application.

It appears in the taskbar for a few seconds then disappears and then apparently does nothing at all.:mad:

---

### Post by chronic on 2008-01-02
is diskeeper a partitioning tool? and printkey200 is obviously a printing tool

the reason these dont work is because trying to get at the heart of windows and there isnt one id also like to point out there both useless under linux since there are linux apps which will do the same thing

wine is great but only for apps that arnt avalable under linux

if there is a linux app that will do the same job then use that

id also like to point out im fairly drunk so exscuse my english an typos

i dont knwo what eaither of these apps really do but you should really be psting ot find linux native programs that will do the same job

---

