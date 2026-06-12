---
title: "I need a good CD burner"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by durkhrod chogori on 2007-09-21
I need something similar to CDBurnerXP Pro (Windows) capable of burning and creating ISO-files, create bootable discs, burn on the fly, etc.

Thanks for your suggestions.

DC.

---

### Post by bendystraw on 2007-09-21
there are many programs that are already available to you, go System > Administration > Synaptic Package manager (something like that spelling)

then click on search and type CD burner and you will get a list of programs that you may want to try out, if all else fails get automatix2 and then click on CD burners and choose the one you want 

Obtained at this link
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)


Hope this helped
:popcorn:

---

### Post by z0mbie on 2007-09-21
K3b - Kubuntu/KDE

Gnomebaker - Ubuntu/Gnome

Brasero (Bonfire) - Simple one.

---

### Post by durkhrod chogori on 2007-09-21
Thanks. I went to SPM and got three. See screenie:

[[img]http://xs119.xs.to/xs119/07386/Screenshot.png[/img]](http://xs.to)


Now, which of those allows you to burn ISO-file and create a bootable disk?

Don't suggest me K3b, don't want to install KDE stuff in here.


Thanks.

---

### Post by bendystraw on 2007-09-21
im not 100% sure read the description, they tell alot about the program

---

### Post by Jussi01 on 2007-09-22
> **bendystraw said:**
> there are many programs that are already available to you, go System > Administration > Synaptic Package manager (something like that spelling)

then click on search and type CD burner and you will get a list of programs that you may want to try out, if all else fails get automatix2 and then click on CD burners and choose the one you want 

Obtained at this link
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)


Hope this helped
:popcorn:

PLEASE DONT USE AUTOMATIX!! 

Automatix2 is a block of code which attempts to install some software.  When it fails and breaks systems, we don't provide support for it.  A creditable analysis from a debian/ubuntu developer is here - [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by alienexplorers on 2007-09-22
If you want a good CD Burner then I can say there are two, gnomebaker and K3B.

---

### Post by TenPlus1 on 2007-09-22
Brasero is a really good disc burning program for Gnome users that has more features than GnomeBaker and doesnt require the KDE libraries unlike k3B

---

### Post by Voland on 2007-09-22
> **TenPlus1 said:**
> Brasero is a really good disc burning program for Gnome users that has more features than GnomeBaker and doesnt require the KDE libraries unlike k3B

Agree and recommend Brasero

---

### Post by durkhrod chogori on 2007-09-22
> **Jussi01 said:**
> PLEASE DONT USE AUTOMATIX!!l]

Thanks for the warning, but I knew already. I am quite an intuitive person.

Guys, I appreciate your input but I need to know if Gnomebaker and Brasero can actually write ISO-files.

Thnx.

---

### Post by Steveway on 2007-09-22
+1 for Brasero
It even integrades perfectly into thunar.
Right-click on an .iso and choose: Burn as image.

---

### Post by bendystraw on 2007-09-22
> **Jussi01 said:**
> PLEASE DONT USE AUTOMATIX!! 

Automatix2 is a block of code which attempts to install some software.  When it fails and breaks systems, we don't provide support for it.  A creditable analysis from a debian/ubuntu developer is here - [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

I did not know that, i will remove it asap, thanks for the tip

---

### Post by Duck2006 on 2007-09-22
> Don't suggest me K3b, don't want to install KDE stuff in here.

I run gnome and K3b and never loaded KDE stuff.
gnomebaker is a good one.

---

### Post by bendystraw on 2007-09-26
you can mount iso's via terminal by 

mount -o loop image-file.iso /mnt/mount-directory 

Of course depending on the image type, you have to tell the mount command what type of image it is. Example if it is a Apple image (dmg), then hfs 

mount -t hfs -o loop image-file.dmg /mnt/mount-directory 

but to burn them i have no idea, im pretty sure that code will work for ubuntu Feisty Fawn, not sure about other versions

---

### Post by misfitpierce on 2007-09-26
K3B or Gnomebaker... Both can be used in Kubuntu or Ubuntu or Xubuntu or anything really...

I prefer Gnomebaker tho

sudo apt-get install gnomebaker

---

