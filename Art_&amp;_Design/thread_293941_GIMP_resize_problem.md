---
title: "GIMP resize problem"
date: 2006-11-05
forum: Art &amp; Design
---

### Post by muz1 on 2006-11-05
Hi everyone. I am hoping that this is the right place to ask this but I am at my whits end when it comes to resizing selections.
Basically, I run a dial boot with XP and I have to reboot back into windows when I want to do something like resizing a selection in an image. ](*,) 
Okay. Basically GIMP is what everyone uses in Linux. So will I. No need to recreate the wheel.
I have an image that I need to adjust.
It is 200 x 200 pixels.
I want the image to be 300 pixels wide by 200 high so I change the canvas to be that size
next I want to take the right five pixels of the image and streech it to cover the never added canvas
It does it during the stretch but as soon as I apply the change, it disappears.
Dores anyone have any ideas because I really hate having to reboot everytime I want do something like this.

Thanks in advance.
Cheers
muz

---

### Post by trash on 2006-11-05
I just spent 1/2 hour trying to do a similar task!
scale image is what you want, to change the size or resolution you will need to 'undo' the chain like icon to the right of the values... hope this helps

---

### Post by Aelfric5578 on 2006-11-06
If you're only changing the canvas size, than your stretched selection isn't disappearing.  It's just getting cropped.  You changed the size of the picture, but not the size of the layer.  As a result, your stretched area is getting cropped.  After you resize the canvas, right click on the layer you'll be stretching in the layer panel, and select "Layer to Image Size."  Then scale your small area and apply.  Remember, when you transform only a small selection like that you'll only be creating a floating layer.  Select "Anchor Layer" from the layer menu when you're done resizing.

---

### Post by muz1 on 2006-11-10
Hey Aelfric5578,
Thanks heaps for your post. I am still having problems but that is cool.
Just wanted to say thanks for opening my mind to afew things about Gimp that I did not know. I think I really need to get some sort of book or ebook about it so I can look fully into it. It actually seems okay as in it kinda works but I am sure that I am missing something out and with some more research, things will clarify themselves.
Cheers bigtime for your post.
Thanks again
muz

---

### Post by Dan777 on 2006-11-15
[Grokking the GIMP]("http://gimp-savvy.com/BOOK/"): I havn't read all of this yet, in fact I've not even read half. But I'm sure you'll be able to find something of help in there.

---

