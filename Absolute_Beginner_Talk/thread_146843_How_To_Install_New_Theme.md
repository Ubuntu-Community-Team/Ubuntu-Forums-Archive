---
title: "How To Install New Theme"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by awalesminfo on 2006-03-19
hi guys am newbie and down loaded new themes named Polyester(Polyester 0.8.5) & Lipstik 2.2 from the [www.kde-look.org](www.kde-look.org) but i dont know how to install them ,so please help me in installing them and i also downloaded the splash screen , screen saver and bootsplash screen from same site and also not abel to install them ,so what steps should i follow for installing them???:-k :-k

---

### Post by dermotti on 2006-03-19
If you have Ubuntu you should be looking at [http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by niviche on 2006-03-19
First, what I am writing below is valid only if you use Kunbtu. If you use Gnome (Ubuntu without the K), these themes will not work for you.

1. First, use Adept to install the package "build-essential".

2. Check if the theme you want to install is not available as a package for Kubuntu. To do so, look for it in Adept. Installing a pre-packaged theme is easier than building it from the source (what you would have to do with the downloads from kde-look). If the package is available, then you can just install it, and you're done. If not:

3. Download the themes from kde-look, and put it on your desktop. Extract it (right click, extract...) to a new folder.

4. Right click on the folder which contains the theme's files, "actions -> open terminal in this folder"

5. in the terminal window, write, one line after the other:

```

./configure --prefix='kde-config --prefix'
make
sudo make install

```

You should be done. If there are any errors, it might mean that you are missing dependencies, i.e. that some stuff needed by the theme is not installed yet on your machine.

I hope this was helpful. Let us know if you manage to install your themes.

---

### Post by Perfect Storm on 2006-03-19
w00t, you are using my "have an ubuntu" picture as avatar ^^,awalesminfo, I can make a better one if you want to.


If you are using ubuntu (gnome desktop) you might have a look here: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by jackn on 2007-04-06
Thank you, NIviche, for the detailed help.

I'm sorry to say, however, that I cannot put your advice to good use.

The 'open terminal in this foldoer' option in the context menu seems to have disappeared (Edgy Kubuntu).

When I try extract a downloaded theme, there is no configure file... (BlackOrange from kde-look.org).

I've also tried 'KDM theme manager' from kde-apps.org. 
This was very hard to install, with two or three error messages. I had to look up these errors on the net and install dependencies. The upshot - it seems to have installed properly (no errors and the files are there), but there is nothing in the K Menu, where it's supposed to be used from.

Mystified...

Help?
Jackn

---

