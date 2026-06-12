---
title: "video problems on a new to me P3"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by pharoah007 on 2008-02-08
I am going to make it into a M.A.M.E machine.

It did notcome with a HD, and hence no OS.

So I put in a UBUNTU OS boot disk and a HD and booted her up.

All the "booting screens" and the UBUNTU loading/shutdown screens display perfect.

My prob is that once UBUNTU has loaded... I am getting these weird vertical "distortion" lines in the display?? Same thing on 3 diff monitors.

Here are some videos showing the perfect shutdown/start up screens and the problem once the OS is loaded..

[http://s4.photobucket.com/albums/y145/pharoah007/?action=view&current=MOV03521.flv](http://s4.photobucket.com/albums/y145/pharoah007/?action=view&current=MOV03521.flv)

[http://s4.photobucket.com/albums/y145/pharoah007/?action=view&current=MOV03520.flv](http://s4.photobucket.com/albums/y145/pharoah007/?action=view&current=MOV03520.flv)

anyone got any ideas what my problem is??

 yes I know it is U-bun-tu, I keep saying U-bat-nu int he video....mybad

Here is the info form typing 'lspci' in a terminal window...............

[http://i4.photobucket.com/albums/y145/pharoah007/DSC03524.jpg](http://i4.photobucket.com/albums/y145/pharoah007/DSC03524.jpg)

some info on the P3 computer...

[http://i4.photobucket.com/albums/y145/pharoah007/DSC03507.jpg](http://i4.photobucket.com/albums/y145/pharoah007/DSC03507.jpg)

[http://i4.photobucket.com/albums/y145/pharoah007/DSC03506.jpg](http://i4.photobucket.com/albums/y145/pharoah007/DSC03506.jpg)


Thanks in advance everyone.

:guitar:

---

### Post by neurostu on 2008-02-08
It looks like you don't have Xorg.conf set up correctly or you don't have the right drivers, try forcing the VESA drivers and see if you have atleast a workable system...

If you get that to work then search for the proper drivers for your video card and then install

---

### Post by pharoah007 on 2008-02-09
ok, thank you..I will look into that today.

---

