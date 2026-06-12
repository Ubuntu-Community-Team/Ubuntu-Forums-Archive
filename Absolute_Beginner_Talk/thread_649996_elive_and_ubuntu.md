---
title: "elive and ubuntu"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2007-12-25
hey i got a question about elive. is it an OS like ubuntu or is it something that u download on ubuntu? if so how do i do that?

---

### Post by srunni on 2007-12-25
Elive is a Linux distribution that allows you to run Debian in a live CD environment with the Enlightenment window manager. Debian is another Linux distribution, which Ubuntu is based on.

I'm guessing that you want to use Enlightenment, which you can do in Ubuntu (or any other Linux distribution). Here are instructions on installing Enlightenment in Ubuntu Gutsy Gibbon: [http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/22/HowTo-Install-Enlightenment-on-Ubuntu-Gutsy-Gibbon](http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/22/HowTo-Install-Enlightenment-on-Ubuntu-Gutsy-Gibbon)

---

### Post by shayvasa on 2007-12-25
ok thanx...but is it the same?

---

### Post by p_quarles on 2007-12-25
The only real difference between Elive and Ubuntu is that while Ubuntu comes with Gnome by default, Elive comes with Enlightenment 17 by default. There's no reason you need to reinstall the entire OS if you're just curious about E17. 

Plus, the version of E17 that srunni's tutorial will install gives you a slightly more up-to-date and stable version.

---

### Post by srunni on 2007-12-25
> **shayvasa said:**
> ok thanx...but is it the same?

Well if you want Enlightenment on your computer, follow the guide I linked. It will give you the same window manager used by Elive, which is what I'm guessing you want.

---

### Post by shayvasa on 2007-12-25
yeah thanx...im still trying to figure out how this works cause when i do sudo apt-get install e17 it tell me it cant find the e17 package. and one more question if i dont like this can i change back?

---

### Post by srunni on 2007-12-25
You can't find the package because you haven't added the repository, as stated in pre-installation requirement A. Follow the link in that section for the guide to adding the repository. 

Once you've installed Enlightenment, you will be able to pick when logging in which desktop environment/window manager you want to run. So you can choose between Enlightenment and GNOME (or whatever other main desktop environment you have installed). If you don't like it, you can log into Ubuntu with the default GNOME environment and uninstall Enlightenment.

---

### Post by smartboyathome on 2007-12-26
The reason you can't find the package is because it changed names from e17 to e17-cvs. I would rather recommend [this guide]("http://ubuntuforums.org/showthread.php?t=546746") which is more up-to-date.

---

