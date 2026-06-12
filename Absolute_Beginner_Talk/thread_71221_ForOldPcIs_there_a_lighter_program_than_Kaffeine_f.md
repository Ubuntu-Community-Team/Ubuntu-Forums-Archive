---
title: "ForOldPc:Is there a lighter program than Kaffeine for watching movies and videos ??"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-02
ForOldPc:Is there a lighter program than Kaffeine for watching movies and videos ??

xmms works very fine with mp3 and m3u
but for avi and divX, is there a light program ??
(for older pc)
(Kaffeine requires tooo much for pc for watching a single tiny avi file)

Thank you very much

Pat'


(-----------
example : rox-filer         is damn lighter than nautilus )

---

### Post by SGC on 2005-10-02
Try **Noatun** or **Kaboodle**, both part of kdemultimedia package.

---

### Post by patrick295767 on 2005-10-12
[QUOTE=SGC]Try **Noatun** or **Kaboodle**, both part of kdemultimedia package.[/QUOTE]

I just read about vlc media player : 
[http://www.ubuntuforums.org/showthread.php?t=74631](http://www.ubuntuforums.org/showthread.php?t=74631)

is vlc media player a light program (for old pc) better or comparable to Noatun[/b] or [b]Kaboodle ?

thx

---

### Post by glug101 on 2005-10-12
How old of a PC?  What kind of CPU?  I found mplayer to be more than adequate for most media file formats on my Athlon 600 Mhz.  However, if you computer is in the 300Mhz or slower range, you may be out of luck with the Mpeg-4 video codecs (like divx)

---

### Post by patrick295767 on 2005-10-12
[QUOTE=glug101]How old of a PC?  What kind of CPU?  I found mplayer to be more than adequate for most media file formats on my Athlon 600 Mhz.  However, if you computer is in the 300Mhz or slower range, you may be out of luck with the Mpeg-4 video codecs (like divx)[/QUOTE]


I have a Compaq Presario 1685 (K6-2, 380 MHz)
Ram 64 Mo - Dd 4.3 Go - Cd - Modem - 12.1" 


( [http://www.ubuntuforums.org/showthread.php?t=64557&page=4](http://www.ubuntuforums.org/showthread.php?t=64557&page=4) )

I use for the moment twm and kubuntu hoary... It's very good result when u compare with windows 98.

---

### Post by Wolki on 2005-10-12
[QUOTE=patrick295767]I have a Compaq Presario 1685 (K6-2, 380 MHz)
Ram 64 Mo - Dd 4.3 Go - Cd - Modem - 12.1" [/QUOTE]

I tried playing avis back when my processor was a K6-2 450 128 mb, and neither windows nor linux would play all of them correctly.

That said, i found a solution that would allow me to play most avis (by far more than windows did), but it is a bold step:

Install mplayer, shut down your xserver and play your videos command-line only. Takes a little time to get used to, but is probably the fastest you can get.

Take a look at the mplayer documentation on how to configure it for that, and play a little with the options to find the best setup.

---

### Post by glug101 on 2005-10-12
[QUOTE=Wolki]I tried playing avis back when my processor was a K6-2 450 128 mb, and neither windows nor linux would play all of them correctly.

That said, i found a solution that would allow me to play most avis (by far more than windows did), but it is a bold step:

Install mplayer, shut down your xserver and play your videos command-line only. Takes a little time to get used to, but is probably the fastest you can get.

Take a look at the mplayer documentation on how to configure it for that, and play a little with the options to find the best setup.[/QUOTE]

Ooooo... good trick!  Most people are unaware that you can send mplayer output dirrectly to the frame buffer and bypass X that way. (a deliciously slick feature ;) )

A 380Mhz CPU with 64 meg of ram is pretty slim for playing back most current videos.  And even with lots of time, that 4.3 gig drive is a bit on the small side for transcoding into less demanding formats.  patrick295767 may be out of luck for most of the video files traded these days...

---

### Post by sidd-tx on 2006-03-08
I've been trying to run MPlayer without X for a while now on Ubuntu. I got it working once with Suse, but since I'm addicted to this distro now, I chunked Suse a while ago..

What is the command to get MPlayer to work without X..  I've tried:

mplayer -vo cvidix dvd://1

mplayer -vo fbdev dvd://1

But cannot get playback. Is there another option/argument that I need to use? Is there something else to setup outside MPlayer that I am missing..?

Thanks in advance...
Sidd....

---

### Post by sidd-tx on 2006-04-21
Nevermind. Got it working.
Had to enable framebuffer by editing grub. and played the DVD with:
mplayer -vo fbdev dvd://1
Just in case anyone was losing sleep over it.

---

