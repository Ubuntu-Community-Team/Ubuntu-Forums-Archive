---
title: "how do I install GIMPShop [Resolved]"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-04-26
I downloaded the source code from their website, but I'm not sure what to do next. I moved the tar.bzz package to my home folder, and extracted the files. Now how do I install it. I tried to follow the instructions on the Gimpshop website, but I keep getting a message in my terminal that says something like file not found. Help.

---

### Post by aysiu on 2007-04-26
Try pasting these commands in the terminal: ```
wget -c http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb
sudo dpkg -i gimpshop_2.2.11-1_i386.deb
```

---

### Post by orwellus on 2007-04-26
That is just what I needed thank you.

---

### Post by Ankher on 2007-04-28
> **orwellus said:**
> That is just what I needed thank you.

ditto! Thanks!

---

### Post by U2XS on 2007-09-04
> **orwellus said:**
> That is just what I needed thank you.
Thirded!  Thanks!

---

### Post by carloslosgrande on 2007-09-04
[FONT="Comic Sans MS"]I actually tried to get this some months without success.
Aysiu you make it so simple.
Thank you.[/FONT]

---

### Post by duruttye on 2007-09-04
What is gimpshop for??

---

### Post by mlentink on 2007-09-04
> **duruttye said:**
> What is gimpshop for??[http://www.gimpshop.com/](http://www.gimpshop.com/)

---

### Post by morgansheffield on 2007-09-04
Hey, I'm really sorry, I'm a long time Winows user who is trying to get into Ubuntu -- total noob. I typed the commands into the terminal, and it said it unpacked the deb and setup gimpshop...now what?

It's not in the Applications menu...how to I access Gimpshop?

---

### Post by carloslosgrande on 2007-09-04
[FONT="Comic Sans MS"]Hi, it updates GIMP, which should be in your applications>graphics menu.
Just open it and it should start up with Gimpshop.[/FONT]

---

### Post by -SpaZ on 2007-09-04
> **duruttye said:**
> What is gimpshop for??

It's just a useless version of The Gimp to make it look and act more like Adobe Photoshop.

---

### Post by n3tfury on 2007-09-04
> **-SpaZ said:**
> It's just a useless version of The Gimp to make it look and act more like Adobe Photoshop.

it's not "useless" if you're accustomed to Adobe Photoshop's menus and layout and have been using it for years.  for those folks it's a huge plus while assisting in making one more comfortable with their new Linux environment.  nothing wrong with that.

---

### Post by -SpaZ on 2007-09-04
> **n3tfury said:**
> it's not "useless" if you're accustomed to Adobe Photoshop's menus and layout and have been using it for years.  for those folks it's a huge plus while assisting in making one more comfortable with their new Linux environment.  nothing wrong with that.

I think that The Gimps' original menus are more intuitive, but that's just me I guess.

---

### Post by Harpoon on 2007-09-04
I am curious if anyone has had luck installing this on a 64 bit system.  I'm running Feisty/64  and  am one of those "useless" <grin> individuals that is used to the photoshop layout.  I'm asking because I am down to one machine, and reluctant to break it if at all avoidable.

---

### Post by Motorhead Kaze on 2007-10-03
Hallo,

Well.  I'm thinking plasticbugs.com is defunked or something.  I couldn't access their webpage today and trying to use the command line I got this:

kaze@kaze-desktop:~$ wget -c [http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)
--19:27:21--  [http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb](http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb)
           => `gimpshop_2.2.11-1_i386.deb'
Resolving [www.plasticbugs.com](www.plasticbugs.com)... 
failed: Name or service not known.
kaze@kaze-desktop:~$ sudo dpkg -i gimpshop_2.2.11-1_i386.deb
Password:
dpkg: error processing gimpshop_2.2.11-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gimpshop_2.2.11-1_i386.deb

Are they "Closed?"

---

### Post by cchevy on 2007-10-28
I had this installed on the new GIMP on 7.10 and I just get the splash screen of gimpshop. How can I turn GIMPSHOP on?

I cannot get my PS look, pls help :(

---

### Post by Igniteflow on 2008-03-15
> **cchevy said:**
> I had this installed on the new GIMP on 7.10 and I just get the splash screen of gimpshop. How can I turn GIMPSHOP on?

I cannot get my PS look, pls help :(d

I've got the same problem, if anyone knows how to fix this it'd be hugely appreciated :confused:

---

### Post by zestycoyote on 2008-04-06
This guide was great.  I had been struggling for a little while trying to do this myself.  

Haha, I should always just look for guides from smarter people.

:lolflag:

---

### Post by newbreed on 2008-05-25
I cannot get my PS look, pls help 


me 3..I followed sudo link...installed, seemed to work, but gimp still looks like gimp, not ps

---

