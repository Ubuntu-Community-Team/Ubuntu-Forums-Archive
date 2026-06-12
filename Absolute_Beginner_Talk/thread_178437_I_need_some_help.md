---
title: "I need some help"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by Louis_DeVecchis on 2006-05-17
i recently installed ubuntu and i need a driver for an intel extreme graphics card. i think i might have the right one off the website but im not sure wat i need and wen i get it how to install it. Just if u can give me a hand remember im a complete noob rite now.

i also need help with my wireless card. I also do not have a driver.

and on top of that im not too suree on literally  how to install any driver i download.

thanks alot to whoever can give me a hand

---

### Post by Sef on 2006-05-17
> intel extreme graphics card.

What model?

> i also need help with my wireless card. 

What make and model?

> and on top of that im not too suree on literally how to install any driver i download.

Read these web pages:

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

---

### Post by Louis_DeVecchis on 2006-05-17
the wirless card is a linksys wpc54g

and the graphics card im not sure. its a dell laptop 1100, celeron processor,  im pretty sure it has 64 mbs shared video memory

il check thos pages u posted

---

### Post by nalmeth on 2006-05-17
If I'm not mistaken, the driver for your intel card should be the i810, and should have been setup by default. You're *supposed* to have 3D setup out of the box.

DId you install the 64-bit kernel? My intel card wouldn't give me any 3D acceleration with the 64-bit kernel. When I installed the regular kernel it worked out of the box.

For you wireless issue, it may be related to the 64-bit driver situation, so going to the regular kernel may solve that aswell.

Check the Wireless Help link in my signature for help with setting up wireless. There is a lot of reading, but it should help you out alot!

EDIT: about the 64-bit stuff, I misread what you said, you were referring to your graphics card. Sorry
In a terminal, enter GLX info, and if you get Direct Rendering, then you should have 3D already.

---

### Post by Louis_DeVecchis on 2006-05-18
it says command not found for thet GLX info thing. so if my graphics card isnt set up wat driver do i download or how do i install it once i get it. 

i am not worrying about wireless until i get a driver so i can view my desktop at normal res.

thanks

---

