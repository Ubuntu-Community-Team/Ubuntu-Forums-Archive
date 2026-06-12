---
title: "Creative WebCam Live! Pro"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by hetihe on 2007-04-14
Is it possible to enable this spesific Creative WebCam Live! Pro?
product id is 0x4038
vendor id 0x41e
It seems that this webcam is not supported out of the box in 6.10, which I have.
Does spca5xx support this one. Ekiga will not recognize it.

---

### Post by daynah on 2007-04-15
I am running Feisty beta. It's a clean install so I know I haven't installed anything special for my camera, which is a Creative WebCam Live! (maybe pro... I know it's a Live! though, which should require the same drivers, should it require any).

Just yesterday I set up Ekiga, and it recognized my webcam. I can't say that it worked, becuase I don't have anyone to call (if you'd like to test it, I'm dancewithmedr you may want to pm a time with me because I'm an ekiga n00b). But when I went though the set up, it did recognize my webcam, on a clean install of Ubuntu. I used the default driver pack that Ekiga recommended. It did do a weird thing like "test 0 test 1 test 2" but never showed the picture... but I think it will work... and this is why.

For the purposes of this post only (because I seriously dispise this program) I installed camorama (sudo aptitude install camorama) and took a picture. I had to use a color correction filter, maybe it was because it's I'm sitting in the gloom of darkness. The proof is attached.

Anywho, my point is, your camera should work. If you give me more details about how it's not working, maybe someone smarter than me will be able to help. ;) But if your camera is anyting like mine (and it sounds exactly like mine) your pictures will come out as grainy as ever! Hey, it's not the nicest webcam in the world, and we both know it. ;)

Have fun, and if you wanna test out Ekiga (I sure do!) just tell me!

EDIT: my friend informs me that I look eleven. I am not, I am 19, I'm just tired. Not that there's anything wrong with 11 year olds, you're just not allowed to be on a webforum when you are under 13.

---

### Post by ndefontenay on 2007-04-24
Thanks for the tip.

I've upgraded to feisty recently.
I'll see if it's working now.
I was facing the same compatibility problem on Linux Edgy.

---

### Post by drummingpariah on 2007-05-18
Here's my problem with that.  I have an a8jm (same computer, essentially) and here's a picture in linux vs a picture from windows (using the webcam, no modifications, etc).  The webcam isn't bad, really.

So essentially, there's a problem somewhere.  Is there a windows driver wrapper, or a different app that anybody would recommend?  I just installed the new driver, and there was no difference.

---

### Post by Killtown on 2007-05-27
My friend has this:  Live Cam Video IM Pro, but can't get it to recognize.  is it compatible?

---

### Post by Killtown on 2007-05-27
Found this new download:

> NEW!! PIXART PAC7311 Support :)
One driver Upto 244 Webcams supported, thanks Linux :).
until gspca v4l2 is finished, used:
gspcav1 "Generic Softwares Package for Camera Adapters" version 1.00.18 date: 08/05/2007
for kernel up from 2.6.11 : gspcav1-20070508.tar.gz
for kernel below 2.6.11: spca5xx version 0.60.00-1:
spca5xx-v4l1goodbye.tar.gz

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)


How do you install a "gz" file and how do you find out which Kernal you have?

---

### Post by ninja67 on 2007-05-29
> **Killtown said:**
> Found this new download:



How do you install a "gz" file and how do you find out which Kernal you have?

"tar zxf <tar.gz-file>" is the command... and to find the kernel you can use the command 
"uname -r"

---

### Post by murak on 2007-09-18
I have IM Pro also and it is ot recognized by Ekiga. Webcam support is so far the only thing in linux that does not work for me.. I guese there is only a matter of time before someone makes a nice universial way to get it working.

---

### Post by philinux on 2007-09-18
ok got the tar file but not a clue what to do with it. step by step help please.
Well I extracted it to its folder thats as far as I got.

{edit] read howto install anything and it got as far ans instal the packeage but failed to install so I gave up.

---

### Post by Tripletaco on 2007-10-04
I also have a Creative Live! Cam Video IM Pro (VF0230).  I would like to get it working.  Any help out there.  I will need step-by-step directions. :)

---

