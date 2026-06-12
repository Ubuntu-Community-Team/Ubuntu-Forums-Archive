---
title: "Big theme problem:  Change EVERYTHING"
date: 2008-09-12
forum: Art &amp; Design
---

### Post by Rimdeker on 2008-09-12
Hi guys, I got the following problem: I can't really get themes to work as they should work. A little example:

Check this out 
[http://gnome-look.org/CONTENT/content-pre1/87514-1.jpg]("http://gnome-look.org/CONTENT/content-pre1/87514-1.jpg")
This guy basically changed everything. If I tried to install that I'd end-up having the same window borders and that's it. Everything else would be "Human".

[http://gnome-look.org/content/show.php/Slickness+Black?content=73210]("http://gnome-look.org/content/show.php/Slickness+Black?content=73210")
I'd love to use this but I just can't.
Also, how do you start creating themes. I know you gotta use engines, what engines would I have to use to create such themes? Also , is creating themes more like programming or designing? I can design but programming...well... lol

Anyhow , thanks a bunch for your help. I really wanna use Ubuntu instead of Windows.

---

### Post by ellalan on 2008-09-12
Try "sudo apt-get install ubuntustudio-desktop" and see whether you like it. Its awesome.

---

### Post by Rimdeker on 2008-09-12
> **ellalan said:**
> Try "sudo apt-get install ubuntustudio-desktop" and see whether you like it. Its awesome.

Haha , that doesn't look too bad but I don't wanna just avoid the problem. I kinda wanna solve it. I tried some stuff anf I got to use the theme a little bit. I got the window borders. the colours within the windows (which I actually never managed to get) now the only thing I need are the taskbars. I still got the usual Ubuntu ones. Once I'm done this I'm good for least 6 months , haha. I did whatever this guy said , just ain't working. I am not simply asking him because I want to solve this problem for future themes. Like what do I got to do when such a problem occurs.

---

### Post by Ub1476 on 2008-09-13
Some themes require the Aurora engine. Search for a .deb file for it on gnome-look. To install themes, unpack the .tar.gz file and the folder with another folder called "gtk-2.0" and maybe also "metacity" in it, you copy to the Appearance>themes app.


Or you can just copy the entire tar.gz file over to Appearance (but this will install everything inside, as many themes comes with different color variations).

To customize/select new themes, just click on Customize in Appearance. 

It's very easy, really:)

NOTE: As said above some themes require the Aurora engine. There are more engines available, like Clearlooks, Murrine and Ubuntulooks. All these are preinstalled in Ubuntu, but some themes now use the alpha/beta version of Murrine (murrine-svn). So you might have to install that... Always check for which engine the theme require in the notes or it might not look correct.

---

### Post by Rimdeker on 2008-09-14
> **Ub1476 said:**
> Some themes require the Aurora engine. Search for a .deb file for it on gnome-look. To install themes, unpack the .tar.gz file and the folder with another folder called "gtk-2.0" and maybe also "metacity" in it, you copy to the Appearance>themes app.


Or you can just copy the entire tar.gz file over to Appearance (but this will install everything inside, as many themes comes with different color variations).

To customize/select new themes, just click on Customize in Appearance. 

It's very easy, really:)

NOTE: As said above some themes require the Aurora engine. There are more engines available, like Clearlooks, Murrine and Ubuntulooks. All these are preinstalled in Ubuntu, but some themes now use the alpha/beta version of Murrine (murrine-svn). So you might have to install that... Always check for which engine the theme require in the notes or it might not look correct.

Thank you a lot for your help. I really did manage to configure lots of stuff and well. I understand the engine thing. My question now is whether creating a theme is more like programming or designing à la Photoshop?
I'd really like to create themes but yet I didn't even manage to know how you actually do it >_>

---

### Post by smartboyathome on 2008-09-14
Creating themes is more like programming unless you go with the pixmap engine. Reason is because the engines allow the color to be changed by e.g. GNOME's Appearance tool. Pixmaps themes can't have this. I recommend you poke around ~/.themes (thats /home/*username*/.themes, and the .themes folder is hidden) and look at different themes to see what you think.

---

### Post by mewithafez on 2008-09-14
> **Rimdeker said:**
> Hi guys, I got the following problem: I can't really get themes to work as they should work. A little example:

Check this out 
[http://gnome-look.org/CONTENT/content-pre1/87514-1.jpg]("http://gnome-look.org/CONTENT/content-pre1/87514-1.jpg")
This guy basically changed everything. If I tried to install that I'd end-up having the same window borders and that's it. Everything else would be "Human".

Well, to be fair that is "Whats in a name?", he is here on the ubuntu forums and ridiculously talented. Look on the community cafe screenshot sticky for some examples he has done. 

Yes that theme uses the Aurora engine, so go on gnome-look and search for aurora deb packages, you can just run those and it'll install the engine. After that, just go to appearance-themes and install the glow-ibex.tar.gz file.

---

### Post by Rimdeker on 2008-09-14
> **mewithafez said:**
> Well, to be fair that is "Whats in a name?", he is here on the ubuntu forums and ridiculously talented. Look on the community cafe screenshot sticky for some examples he has done. 

Yes that theme uses the Aurora engine, so go on gnome-look and search for aurora deb packages, you can just run those and it'll install the engine. After that, just go to appearance-themes and install the glow-ibex.tar.gz file.

Thanks for your help, I'll do that and well, we'll see.

---

### Post by Flimm on 2008-09-16
The application I'm developing, [Epidermis](http://epidermis.tuxfamily.org), is one that aims to customise the look and feel of the Ubuntu (GNOME) desktop, all of it, quickly and easily.
It's open source and hosted on [launchpad](https://launchpad.net/epidermis/).

---

### Post by Rimdeker on 2008-09-16
> **Flimm said:**
> The application I'm developing, [Epidermis](http://epidermis.tuxfamily.org), is one that aims to customise the look and feel of the Ubuntu (GNOME) desktop, all of it, quickly and easily.
It's open source and hosted on [launchpad](https://launchpad.net/epidermis/).

1st , thanks for you help. Really appreciated. About your software:
Is it reliable , yet? I mean , you said developing , isn't really encouraging...

---

### Post by Flimm on 2008-09-18
Yeah, sorry, it's not reliable, yet.... But I'm working on it regularly! I have got a more or less working prototype, but I'm changing it all the time.

---

