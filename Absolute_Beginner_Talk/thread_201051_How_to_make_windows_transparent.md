---
title: "How to make windows transparent?"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-06-21
Hello friends,

1.I have seen quite a few screen shots of people having transparent windows. The command window looks absolutely cool with this kind of look. Can anyone tell me how to do it. I do not have any ATI or Nvidia cards so please do not suggest any graphic card based solutions. I need it for my laptop :D . Specs are:
P4 Intel centrino 
512 Mb RAM

2. Any other kind of Eye-candy will be much appreciated. I have already tried gdesklets. For GLk-Compiz I have not been able to find a good instruction set for people without any video cards like me :confused: 
 
Thanks for any help.

---

### Post by Jagot on 2006-06-21
This is quite a good thread relating to eye candy:

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

Most of the groovy transparency you see will be done with XGL which is possible with onboard Intel graphics apparently, though I haven't tried it:

[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)

---

### Post by sas on 2006-06-21
It varies from application to application. Eterm is a terminal application which allows transparency. Some IRC clients do as well. I can't remember off hand how to make them go transparent though.

---

### Post by FISHERMAN on 2006-06-21
Gnome-Terminal:
Choose 
-Edit
-Current Profile
-Effects(don't know if it is the correct translation)
-Transparant Background.

Nautilus:
Choose 
-Edit
-Background and ...(No transparancy though)

---

### Post by th3james on 2006-06-21
You can make the gnome terminal do 'fake' transparency by going to
Edit --> current profile and then clicking under the 'Effects' tab

---

### Post by frodon on 2006-06-21
For sure you have a graphic card, it should be an integrated graphic card because you have a laptop. Transparency (i mean for any window) requires to have the graphic card drivers installed to be usable.
So have a look to your laptopn spec and tell us which graphic card use your laptop or the name of the chipset, it will be quite difficult to help you without this information.
If you just want a "fake" transparent terminal the solutions above works really well.

2. For Xgl/compiz it also depends of your graphic card, there're several guides in the forum for almost all the chipsets.

---

### Post by 23meg on 2006-06-21
If a transparent terminal is all you want, check this out: 

[http://ubuntuforums.org/showthread.php?t=81727](http://ubuntuforums.org/showthread.php?t=81727)

---

### Post by hotbrainz on 2006-06-21
thanks a lot guys will try it. 

Hey Jagot, well the link on XGL-Compiz that you have given has different instructions for different video cards. 

> Xgl/compiz on an Intel i915 video card with DRI
Aiglx/compiz on an Intel i915 video card compiz seems to have better performance on Aiglx with this video card.


My case should fall in either of the above two( I hope). Well how do i find out what video card i have? and what is DRI in th above quote?

---

### Post by givré on 2006-06-21
aiglx is definitly better than xgl for intel graphics card, give it a try, this howto is really good

EDIT: and you will have the same eye candy than with xgl

---

### Post by hotbrainz on 2006-06-21
thanks a ton Givre. And all you guys who took time to blog in....

Cheers

---

