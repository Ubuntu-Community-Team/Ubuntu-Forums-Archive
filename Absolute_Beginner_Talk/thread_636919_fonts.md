---
title: "fonts"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by salvatordarling on 2007-12-10
Hi there.

I'm very new to Ubuntu.  I have no knowledge of coding or programming - I'm afraid I'm rather inept in those areas.  I just wanted a way to get rid of Microsoft from my computer.

I'm running Ubuntu 7.10 (I downloaded it 2 weeks ago) on an Acer Aspire 3690. 
I have some fonts on my Windows system that I want to install in Ubuntu.  This is one of the last things preventing me from deleting Windows for good.

I have no idea how to install the fonts in Ubuntu.  Can anyone give me a really simple way of doing it?  I only have about 100 fonts to install.

Much appreciated.

SalvatorDarling

---

### Post by saj0577 on 2007-12-10
Have you got the font files for these fonts or did you use a .exe in windows to install them?

Saj

---

### Post by saj0577 on 2007-12-10
Found this.

[Link]("http://penguinfonts.com/howto/ubuntu.php")
their are also many user made scripts to install them if you browse around for a good few minutes.

Saj

---

### Post by mahiyar on 2007-12-10
Windows has a fonts folder. There is a fonts folder in Ubuntu /usr/share/fonts/, also there can be a font folder in your home direcdtory ~/.fonts, copy the windows fonts to either of these folders, to the share folder if you want to share the fonts with other users. After copying run this from cmd >>sudo fc-cache -f -v   Do you really need windows fonts? A good page on installing fonts is this --> [https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

P.S: You may need to relog/restart into Ubuntu

---

### Post by salvatordarling on 2007-12-10
Thanks!  
I have found the fonts folder.  I get a permission denied message when I try to create a folder or directory, and I can't put anything in the fonts folder because I get the same message.  Any thoughts?

---

### Post by NilsE on 2007-12-10
> **salvatordarling said:**
> Thanks!  
I have found the fonts folder.  I get a permission denied message when I try to create a folder or directory, and I can't put anything in the fonts folder because I get the same message.  Any thoughts?
In a terminal do a 

gksudo nautilus 

and you will have root permissions for all folders in Nautilus.  You can then create and modify to your hearts content. But be careful what you delete.

---

### Post by salvatordarling on 2007-12-10
Thanks everyone - I'm sorted now.  I used the terminal to get access to the folder I wanted, and then just dropped my existing font files in there.  There's some that I use for various things, and I didn't want to lose them...

---

### Post by stchman on 2007-12-10
For future reference I have a procedure to install fonts in Ubuntu.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

