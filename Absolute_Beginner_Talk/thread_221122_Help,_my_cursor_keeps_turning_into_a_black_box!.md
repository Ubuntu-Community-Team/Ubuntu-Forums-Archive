---
title: "Help, my cursor keeps turning into a black box!"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by mfuqua on 2006-07-22
I loaded Dapper onto an older Sony Vaio laptop, and am having problems with the mouse cursor which are driving me nuts.  The cursor tends to work normally and display fine, except at points during loading things it will turn into a black box, about 3/4" x 3/4".  At other times, such as the login screen, in adobe for pdfs, and other random programs, it will be this box and never show the cursor.  Sometimes the cursor is solid block, sometimes its a box maded up of thin black lines.  I've tried loading different cursor themes, but it hasnt seemed to help.  Any help that you guys could offer would be greatly appreciated, because other then this I'm loving Ubuntu and Linux!

Thanks alot.

---

### Post by exif on 2006-07-22
It sounds like it might the display drivers. Check out [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video) there is info there on how to setup your vid card depending on the make of it.

---

### Post by SoloSalsa on 2006-07-22
Hey there!  Is it a PCG-F something?  I'm using an F520 (almost the lowest-end one, but I upgraded a lot of stuff).  I'm kinda new to Ubuntu, but I'd guess that it is a problem with the graphics card.  My VAIO uses a NeoMagic MagicMedia just fine.
Bye.

---

### Post by mfuqua on 2006-07-23
Yep, it is a Neomagic Corporation NM2380 [MagicMedia 256XL+], but I don't really have any idea from a video driver standpoint what I could do, since the HowTo doesn't really adress it.  So I'm still kinda at a loss.

---

### Post by SoloSalsa on 2006-07-24
Ride on...  If you get out of this.  First thing, of course, is run the update manager.  If you turn it on with an available connection, the update manager syncronizes its list.  Otherwise, you can run 'sudo get update' I think, or something like that...  I just know is sounds familiar :-).  Then, you should try a media prep tool.  I like [bumps.]("http://www.ubuntuforums.org/showthread.php?t=181248")  There is also [Automatix ]("http://www.ubuntuforums.org/forumdisplay.php?f=77")and [Easy Ubuntu]("http://www.ubuntuforums.org/forumdisplay.php?f=86").  But if you do not have internet access on your laptop, then I don't think there's much you can do.

---

### Post by mfuqua on 2006-07-24
Thanks for keeping with me here SoloSalsa, I do appreciate it. Unfortunately (or fortunately I guess?) I do use the update manager and have run Automatix, but still have no updates to install :-/. I'm thinking the problem might just lie in the fact that this laptop is old, but I always thought that was one of the beauties of linux was that it should work right on almost any kind of system.  At least I'm happy with everything else though :-).

---

### Post by SoloSalsa on 2006-07-24
No problem!  I'm just excited since I'm helping... 'specially a longer user :-).
   I think it is a problem with the xorg window system.  I think that is the only one Ubuntu uses though; I'm not sure.  I've only heard of xorg from Puppy Linux; it let's you choose between xorg and an older, proven xvesa.  And I only tried Puppy to make use of my really old desktop!

   I'm just curious though, what is your model?  Mine says on the underside and the right screen-hinge.  If it's a gray/Vaio-purple plastic color scheme, then it's definitely the F-series.  It was supposed to be rugged, hence the thickness.  Mine is seven years old, has overheated about weekly, dropped quite a few times, experienced plenty of power failures, and yet works fine-- or did until last week!  Although it never had thermal damage and not a scratch on the screen, I kind of grounded it;  I spilled some water on the keypad on Thursday, just that once, and now it won't work.  I can plug one in at home, but I sure am not going to carry it with me!  But I still love my cripple old laptop.

---

### Post by mfuqua on 2006-07-24
Longer user yes, but admittedly I use a Thinkpad which I dual-boot Ubuntu and Windows, and tend to spend more time in XP only because I'm tied to CAD software such as SolidWorks that doesnt offer a Linux version, nor work in Wine.

But to digress, the laptop I'm trying to fix up is actually my fiance's, which I loaded Ubuntu onto because she crapped up XP with viruses and I didn't feel like dealing with it :-).  Unfortunately she headed out on a buisness trip tonight until Friday, and I'm really not sure what the model is. It's an older model for sure, probably around the same age as yours, but it is all grey.  I'm trying to do some more detective work on the web as I go, but am limited in time, which is why I was turing here.  Hopefully I figure somethign out though :-).


EDIT:  I just found this link: [https://lists.ubuntu.com/archives/ubuntu-bugs/2004-October/012841.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2004-October/012841.html) when searching for the video card and Ubuntu.  I can't be sure it is the issue until I get my hands on the laptop again, but it looks promising!

---

### Post by SoloSalsa on 2006-07-25
I have an idea.  I'm going to look up some stuff about my hardware in the device manager; eventually...  If you haven't done so already, you should submit your hardware list from the device manager.  On the bottom, there is a button that performs a media test and submits the results to developers.

---

### Post by SoloSalsa on 2006-07-27
Hi!  It's not quite Friday yet, but I don't care.
I found this:
> The X server          will correctly detect the NeoMagic chip, but it will not be able to start          up X straight out of the box. [Jeffrey          Carter]("http://www2.shore.net/%7Ejeffc/sonyXG9.html") had the same problem on his XG9 - but was able to run Xconfigurator          and get it to work. I tried running Xconfigurator with no such luck. Then          I found some info on the F490, thanks go [Austin          Donnelly]("http://www.cl.cam.ac.uk/%7Eand1000/vaioF-series.html"), which uses the same NeoMagic NM256XL+ video chipset.
Basically,          run Xconfigurator, and choose NeoMagic as your chipset and LCD1024x768          as your monitor.

      (thanks, Google Linux) on a site about a PCG-FX900 or something.  The FX series came out after the F series.  The difference is that, simply, it is way better in every way.  I don't know yet if you have an F or FX.  An easy way to tell is that the FX has the long intercooler vent thing that opens on the back.  If you don't know what I'm talking about, then you don't have an FX.  Anyway, the F and FX used MagicMedia graphics, and this person had a problem simillar to yours.  So, it seems as though you could do something simillar.  You should make sure the resolution is right though, if it's SVGA instead of XVGA.  Hope this helps!

---

### Post by mfuqua on 2006-07-29
:D It was indeed a problem with the X autoconfiguration failing to include
  Option "SWCursor" "true"
in the "Device" section of xorg.conf.  Upon re-inserting it and restarting X, the problem was gone :-).  Such a relief, as I won't have to hear complaints about it anymore.

Thanks for all of the help SoloSalsa.  Oh, and for the record, it ended up being a PCG 9231 :-).

---

### Post by SoloSalsa on 2006-07-29
Yipee!  Do I get a 'bene' point?
   Umm, you figured that out yourself, I think, as I didn't mention anything *complex* in X...  So would you tell me how you did it; where you found out that SWCursor was the missing piece?  I would like to bookmark the 'site for my future reference.
   And if it is her first time, I hope your fiance likes Linux.

---

### Post by mfuqua on 2006-07-29
No, but it was good to have someone following along and at least hearing me out.  It is a great thing having a community like this where you can turn for help and advice.

As for the how I stumbled upon that solution, it came from the ubuntu bugzilla ([https://lists.ubuntu.com/archives/ubuntu-bugs/2004-October/012841.html)](https://lists.ubuntu.com/archives/ubuntu-bugs/2004-October/012841.html)), and I honestly came across it by googling the video card and ubuntu, and I think I threw the word 'cursor' in. So I don't really have much sage advice.

---

