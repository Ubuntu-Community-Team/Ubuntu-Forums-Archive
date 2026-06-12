---
title: "Hi, new to linux and ubuntu"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by atad6 on 2005-09-14
Hi,
I just installed the lastest version of linux. I've tried linux on and off the last couple years, and have wanted to get into it but haven't ever figured out how to compile programs and such as the terminal scares me away a bit. I just installed ubuntu on my computer and it won't seem to go to any resolutions other than 640x480. I've tried editing the file in the x11 folder that controls this but It says I don't have rights to save it. Anyway, I have three main questions.

1. What are some good resources to help me get started compiling and installing applications in linux, ubuntu.

2. How can I get my screen to go above 640x480 (i have an ati x300),  Is there an easy way to configure my x300 with ubuntu?

3. What steps should I take to get more familar with linux.

I have a fairly extensive background with computers, linux is something I've never really had the chance to learn. Any help would be greatly appreciated.

Thanks again!

---

### Post by xequence on 2005-09-14
It says you dont have the rights? You need to be root. You can type:

sudo gedit (FILE NAME AND PATH HERE)

Sudo lets you get root privaliges for the one command you do. It will ask you for your password. Sudo means super user do. Gedit is the program that edits text files, if you use a different text program, type it instead of gedit.

---

### Post by aysiu on 2005-09-14
[QUOTE=atad6]
1. What are some good resources to help me get started compiling and installing applications in linux, ubuntu.[/quote] [http://www.psychocats.net/essays/winuxinstall.php](http://www.psychocats.net/essays/winuxinstall.php)

> 
2. How can I get my screen to go above 640x480 (i have an ati x300),  Is there an easy way to configure my x300 with ubuntu? [http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

> 
3. What steps should I take to get more familar with linux. [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by aysiu on 2005-09-14
[QUOTE=xequence]Sudo means super user do.[/QUOTE] I couldn't believe it at first, but it's confirmed:

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by Nequeo on 2005-09-14
Hey there,

I'm a little worried that you're talking about compiling software.

It's a mistake lots of Ubuntu newbies who have used Linux on and off before make. Including myself. It also results from the Windows habit of googling up software and downloading it from webpages, then trying to work out how to install it.

The wonderful thing about Ubuntu, and Debian-based linux distros in general ([http://www.debian.org/)](http://www.debian.org/)), is that you don't have to do any of that! Or, at least, the vast majority of desktop users won't need to compile anything. (Though of course, you can if you know what you're doing. And who knows, some people - me included - get a strange glow of pleasure when we see lines of white text scrolling across our screen. We know that our computer is *doing* something. But that's beside the point...) 

Erherm! Where was I? Ahh yes, as far as installing software is concerned, follow the steps on these two pages:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
[http://www.ubuntuguide.org/#synaptic](http://www.ubuntuguide.org/#synaptic)

And enjoy!

---

