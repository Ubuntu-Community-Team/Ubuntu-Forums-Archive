---
title: "How do I make a dvd?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by ron999 on 2007-03-07
Hi
I have a avi file on my pc that I want to make into a dvd for my friends to watch on their tv set using their home dvd player.
I'm confused.
I understand that I must first re-encode the file to MPEG2 using Avidemux or DeVeDe programs.
But what next?
Do I just burn the MPEG2 file to a blank disc or is there something else to do first?
:confused:

---

### Post by chggr on 2007-03-07
Here you are! 
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/AVI_to_DVD)

---

### Post by ramjet_1953 on 2007-03-07
I have found that QDVDAuthor works well for me.

It is a graphical front-end for dvdauthor.

[http://qdvdauthor.sourceforge.net/](http://qdvdauthor.sourceforge.net/)

You need to also have dvdauthor and dvd+rwtools-tools loaded.

QDVDAuthor is available in the multiverse repository, and can be downloaded using Synaptic.

Regards,
Roger 8)

---

### Post by crispy_420 on 2007-03-07
Doesn't DeVeDe make iso images?

---

### Post by ron999 on 2007-03-08
Thanks for your replies.

crispy_420
I started off by using DeVeDe to create an iso but it doesn't seem to work for me. It ran for hours and hours but didn't do the job. I will try to use DeVeDe again when I have more patience.

ramjet_1953
I have already tried using qdvdauthor. There are no instructions or help files, it just confused me even more. Also, I don't need buttons, menus or chapters just now. I will try to use qdvdauthor again when I have more experience.

chggr
Most of that CLI stuff in your link went way over my head. However, I already know how to generate MPEG2 files using Avidemux. And I know that K3B will allow me to burn AUDIO_TS and VIDEO_TS directories. So I'm going to try using steps 4 and 5 to generate those directories with the BUP, IFO and VOB files. I think that this is the part of the jigsaw that is missing. I've bought some DVD-RW discs. I will experiment and report back.

Thanks again.
:grin: :cool:

---

### Post by baysl on 2007-03-08
You should install Gnome Baker.
It is a very easy program to use.

---

### Post by ron999 on 2007-03-09
Yes chggr, it works.:) :) 
I used Avidemux to re-encode the avi file to MPEG2 (AUTO > DVD > SAVE).
Then steps 4 and 5 did convert the MPEG2 into a DVD file structure and K3B burned it to disc.
:cool: :cool:

---

### Post by mfalcon on 2007-05-15
I'm looking for a complete solution to take MythTV generated .mpg files and create a DVD with them. No menus, just convert to a .vob so that I can get the mpg's off the hard disk and have a archive copy of the show/movie.

I've tried QDVDAUTHOR, but get errors at the end when it can't find an .IFO file. Also, QDVD takes an enormous amount of time to create the DVD, almost 2-3 times the length of  the some - maybe something else is wrong?

What solutions does the Linux community have to complete the puzzle?

Thanks!

---

### Post by laidback on 2007-05-15
Have used DeVede myself just recently and it takes forever to do anything, 1Gb convertion to ISO took around 2 hours, but I did get there in the end. I found along the way that I needed to tell it I was creating a DVD and not any of the CD VCD options otherwise you get a .bin and 1 other file, which apparently can be burned but the process seemed rather long winded. (as if you haven't spent enough time) I also noted that my CPU was at 100% useage all the time that the convertion took place. Good test of my cooling so I didn't really mind.

---

### Post by ron999 on 2007-05-16
I now use **tovid** from the command line (CLI). This is the link:- [http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

I do it in stages.

1) Use **tovid** to convert the file(s) to MPEG2, DVD compliant format.
2) Use **makemenu** to make a menu, if required.
3) Use **makexml** to make an xml file.
4) Use **makedvd** to author the DVD (Creates a VIDEO_TS folder containing IFO, BUP and VOB files).
5) Use** K3B** to create an ISO image file.
6) Use **VLC** to test view the ISO.
7) Use **K3B** to burn the ISO.

There's also a GUI option, but I haven't had any success with it yet. This is the link:-[http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage]("http://tovid.wikia.com/wiki/Using_the_tovid_GUI#Usage")

:cool:

---

### Post by newlinux on 2007-05-16
> **mfalcon said:**
> I'm looking for a complete solution to take MythTV generated .mpg files and create a DVD with them. No menus, just convert to a .vob so that I can get the mpg's off the hard disk and have a archive copy of the show/movie.

I've tried QDVDAUTHOR, but get errors at the end when it can't find an .IFO file. Also, QDVD takes an enormous amount of time to create the DVD, almost 2-3 times the length of  the some - maybe something else is wrong?

What solutions does the Linux community have to complete the puzzle?

Thanks!

How about mytharchive? Nice and integrated with mythtv. I think it does force you to put some kind of menu, however, and burns to .iso

---

