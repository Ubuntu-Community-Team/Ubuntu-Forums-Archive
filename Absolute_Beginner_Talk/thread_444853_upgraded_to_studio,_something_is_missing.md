---
title: "upgraded to studio, something is missing"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-05-15
I upgraded to studio two days ago and I love it.
my problem is, when I turn on the computer, the old ubuntu boot screen comes up (with the orange colors and stuff)
is there something I need to change manually?

---

### Post by starcraft.man on 2007-05-15
> **Gmbrdilos said:**
> I upgraded to studio two days ago and I love it.
my problem is, when I turn on the computer, the old ubuntu boot screen comes up (with the orange colors and stuff)
is there something I need to change manually?

Search [gnome look]("http://www.gnome-look.org/") for a GDM theme from Ubuntu studio, then you can have the same black log in look.

Edit: [here]("http://www.gnome-look.org/content/show.php/UbuntuStudio+GDM?content=58047") is direct link :)

---

### Post by joejaxx on 2007-05-15
if you are talking about usplash and you have usplash-theme-ubuntustudio installed you want to run:

```
sudo update-initramfs -k all -u
```

also what packages did you install to upgrade?

---

### Post by 67GTA on 2007-05-15
You need to install ubuntustudio-look. 
Add the repository to your /etc/apt/sources.list:
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

Then run these commands in a terminal:
 wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install ubuntustudio-look

---

### Post by MetalMusicAddict on 2007-05-15
Im gonna go out on a limb and say you didnt use our repo. Or if you did you just grabbed our theme and media metas.

Make sure you have our repos:
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then:
```
sudo apt-get install usplash-theme-ubuntustudio
```

Also, a repo install does not a Ubuntu Studio make. ;)

---

### Post by .t. on 2007-05-15
Really, what you need is all that and ubuntustudio-default-settings installed as well.

---

### Post by Gmbrdilos on 2007-05-15
I followed the directions on ubustu.com
added the repository and downloaded everything that starts with ubuntustudio from the synaptic package manager

I am not talking about the splash screen, that one is fine
I am talking about the one that comes before it (black screen with ubuntu written and an orange progress bar showing loading progress)

---

### Post by 67GTA on 2007-05-15
ubuntustudio-look will install that. Follow the instructions in my earlier post.

---

### Post by silent1643 on 2007-05-15
> **Gmbrdilos said:**
> I upgraded to studio two days ago and I love it.
my problem is, when I turn on the computer, the old ubuntu boot screen comes up (with the orange colors and stuff)
is there something I need to change manually?

follow these instructions.. worked for me no problems, then go to sinap and make sure you have what you need under ubuntustudio tags
[http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/](http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/)

---

### Post by Gmbrdilos on 2007-05-15
none of the suggestions worked

the themes and everything else are there just not the boot screen:

---

### Post by .t. on 2007-05-17
Are you sure ubuntustudio-default-settings is installed?

---

### Post by Gmbrdilos on 2007-05-17
yes it is.

---

### Post by samstar on 2007-05-18
Hi,

You have to point the usplash symbolic link in /etc/alternative to the usplash theme you want to use.  Here's a simple way to do that:

```
sudo update-alternatives --config usplash-artwork.so
```

After that, rebuild your initrd file with the command:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

And reboot!

Instructions came from [https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

Hope this helps,
Sam

---

