---
title: "IEs4Linux Installation on Ubuntu"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by fatboysam on 2008-02-18
Hi,

Trying to install IEs4Linux on Ubuntu 7.10 bu unrtunately nothing happens - just stops during the installation with the following messages during installation, i.e:

ownloading everything we need
  Downloading from microsoft.com:
   DCOM98.EXE
   mfc42.cab
   249973USA8.exe
   ADVAUTH.CAB
   CRLUPD.CAB
   HHUPD.CABa
   IEDOM.CAB
   IE_EXTRA.CAB
   IE_S1.CAB
   IE_S2.CAB
   0%   SCR56EN.CAB
  Downloading from macromedia.com:
   -    swflash.cab!! Cannot download flash

And just leaves the installation screen up.

Any assistance would b much appreciated.

Thanks

---

### Post by ice60 on 2008-02-18
maybe you're using an old guide, or something like that?? didn't adobe buy macromedia :confused:

are you following this? (is that the correct page? i've never used it) -
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

[color=RED]**EDIT**[/color] that guide i linked to might be old too!!, it's adding repos for edgy, here -
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) **edgy** main
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) **edgy** universe

i think ubuntu is on gutsy now, sorry, don't follow the link i gave, it's old!!!

---

### Post by fatboysam on 2008-02-18
Would it be because I have previously already installed Adobe Flask 9?

Or perhaps swflash.cab is corrupted - not sure where this file might be so that I can remove it?

---

### Post by ice60 on 2008-02-18
> **fatboysam said:**
> Would it be because I have previously already installed Adobe Flask 9?

Or perhaps swflash.cab is corrupted - not sure where this file might be so that I can remove it?no, to me it looks like it can't find swflash.cab because it's looking on a macromedia site when it probably should be looking at an adobe site. so, it never gets downloaded at all! i could be totally wrong though. 

i'm sure you'll find a howto if you search these forums though. there's wine-doors too, i think that might have an older version of IE, maybe IE 6?
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

you could try running this if you want to try it -
sudo apt-get install wine-doors

there's the ubuntu guide too, it mentions IEs4Linux if you search the page (ctrl-f)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by fatboysam on 2008-02-19
thaaks - will check it out.

---

### Post by JoshuaRL on 2008-02-19
If you go to the wine site and download the latest version of wine (9.55) it should have IE in there I believe.

---

### Post by fatboysam on 2008-02-19
ok - ta.

---

### Post by adlerhn on 2008-02-19
> **JoshuaRL said:**
> If you go to the wine site and download the latest version of wine (9.55) it should have IE in there I believe.

Does that version work for anyone? I have had to revert back to 9.54, as 9.55 was giving me segmentation fault even when executing winecfg.

It is the first thing I read about an embedded IE-clone in wine... It is correct?


Regards!

Jose.

---

### Post by JoshuaRL on 2008-02-19
Nope, sorry for the misinformation.  Still the best way to get IE is IEs4Linux.

And I'm running 9.54 myself.  But I haven't had any problems with it.

---

### Post by teslarage on 2008-02-19
I installed IES4Linux on 0.9.54. Just updated Wine to 0.9.55. IE6 still works fine (thank god).

---

### Post by JoshuaRL on 2008-02-21
I can't get it to install either.  I get this error:

```

Gtk-ERROR **: file /build/buildd/gtk+2.0-2.12.0/gtk/gtktextlayout.c: line 2281 (gtk_text_layout_get_line_display): should not be reached
aborting...
ui/pygtk/python-gtk.sh: line 6: 15022 Aborted                 (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

```

UPDATE
Okay, I got it installed.  But I'm not sure how.  I'll post what I did:

Python kept core-dumping and sudo apt-get install --reinstall python-gtk2 didn't work to fix it.

So when the install menu came up eventually went to IE5.5 without Adobe Flash 9, and I got a lot farther with this error:
```

Gtk-ERROR **: file /build/buildd/gtk+2.0-2.12.0/gtk/gtktextlayout.c: line 2281 (gtk_text_layout_get_line_display): should not be reached
aborting...
ui/pygtk/python-gtk.sh: line 6: 16683 Aborted                 (core dumped) python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py

```

So I thought I'd try a little farther and it worked.  I now have IE5.5 installed.

So I then tried IE5.5 with Adobe Flash 9.  And that worked.

As did IE6 with flash.  So that's the workaround I found.

So fatboysam, I would suggest trying that and see if it works.  Hope that helps.

---

### Post by klco on 2008-04-03
Strange thing, but when I tried to install only IE6 (the default and the one I actually need) it failed, but it worked fine when I installed all three.  Might want to give that a try.

---

