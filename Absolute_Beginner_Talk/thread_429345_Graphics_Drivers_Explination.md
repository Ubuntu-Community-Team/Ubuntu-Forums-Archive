---
title: "Graphics Drivers Explination"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-05-01
OK, I am sure I am not the only person here that is totally confused by the words VESA, GLX, FGLRX, and all these countless other things.

Now I know that VESA is kind of a default, works-for-all software thing, and that because of that, its slow.

But when it comes to anything else, I just get confused. Is there any chance some knowledgeable person can just explain, how it all works? I am an ATI user, but i am sure NVIDIA users are just as eager to find out what is going on.

Cheers, Andy

---

### Post by lluisanunez on 2007-05-01
See this:
[URL="https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards"]
https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards[/URL]

---

### Post by 3rdalbum on 2007-05-01
fglrx is the actual name of the ATI Proprietry Driver. Since you're an ATI user, you probably will want this.

ati is the name of the open-source ATI 2D driver. nvidia is the name of the proprietry Nvidia driver. nv is the name of the open-source Nvidia 2D driver.

GLX isn't really something you need to worry about. XGL is a graphical display that runs on top of Xorg (Ubuntu's regular display program), to provide 3D acceleration for eye-candy window managers like Compiz and Beryl. I don't recommend running Compiz or Beryl unless you have had a couple of months Linux experience. ATI users need to install and use XGL if they want to use Compiz or Beryl. NVidia users don't.

---

