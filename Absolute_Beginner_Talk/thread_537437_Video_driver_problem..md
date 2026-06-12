---
title: "Video driver problem."
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by musicarvind on 2007-08-28
Started my ubuntu this morning and for the first time in like 3 weeks since i have used ubuntu, this weird problem came up.

It says like this:

"Failed to start the X server (your graphical interface). It is likey that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Click on yes:

and this is the problem:

(EE)Failed to load module "nvidia" (module does not exist, 0 )
(EE) No drivers available.

Then it lets me sign in DOS style and i get this terminal thing:

arvind@arvind-desktop:~$


I am really a newbie and hope someone can help me out step by step on how i could solve this problem. Please please. thanks

arvind..

---

### Post by Hobo Joe on 2007-08-28
Follow these commands:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

dpkg -i envy_0.9.7-0ubuntu8_all.deb

envy -t

```

Then just press install nVidia drivers. Make sure to let it configure your xorg.conf  for you.

---

### Post by musicarvind on 2007-08-28
> **Hobo Joe said:**
> Follow these commands:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

dpkg -i envy_0.9.7-0ubuntu8_all.deb

envy -t

```

Then just press install nVidia drivers. Make sure to let it configure your xorg.conf  for you.

hi thanks for your reply. however after downloading the package and 

sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb

it comes out with this error:

"dependency problems prevent configuration of envy"

and then nothing is installed. 

any further help? 

my system is 64bit AMD Athlon X2

---

### Post by Marat Galiev on 2007-08-29
Install packages!write dependecy packages on the paper,and
found them at packages.ubuntu.com.
then install envy!
that you video card model?
you must install driver only.
get it at the packages.ubuntu.com:)
name nvidia-glx-new(for new chipsets) or nvidia-glx(old)

---

### Post by nosfed438 on 2007-08-29
type     "sudo dpkg-reconfigure -phigh xserver-xorg"
 and then restart i have the same  prob cant get the nivida drivers to work it should work but no drivers

---

### Post by musicarvind on 2007-08-29
> **nosfed438 said:**
> type     "sudo dpkg-reconfigure -phigh xserver-xorg"
 and then restart i have the same  prob cant get the nivida drivers to work it should work but no drivers


hi tried this route and its still not working.  this is getting really difficult.  please excuse my ignorance but i really do need step by step help.

---

### Post by musicarvind on 2007-08-29
> **Marat Galiev said:**
> Install packages!write dependecy packages on the paper,and
found them at packages.ubuntu.com.
then install envy!
that you video card model?
you must install driver only.
get it at the packages.ubuntu.com:)
name nvidia-glx-new(for new chipsets) or nvidia-glx(old)

hi marat, it didnt list the dependent packages.

---

### Post by eeeeepuk on 2007-08-29
My recommendation would be to first get you back into x, albeit without the proprietory drivers (and as an aside, if you have compiz/beryl auto-starting this ISN'T going to work as they require the proprietory drivers), as I don't know about you but I find a graphical interface always helps. Once there we can look at getting your NVidia drivers working again.

We'll start by manually editing your xorg.conf file, being sure to make a backup first.

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf

Replace "nvidia" with "nv" on the "Driver" line in the "Device" section relating to your video card. Hitting ctrl+o will allow you to save the file, and ctrl+x will close nano. You should then be able to get into x by typing

> sudo /etc/init.d/gdm restart

Now we're back in x, try double clicking the envy installer again, and let the gnome package manager (gdebi) try to install it. Hopefully this time it will tell you about any missing dependancies.

Once envy is installed you'll find a graphical tool to install the NVidia drivers under Applications -> System Tools -> Envy. As with the advice above, let Envyconfigure your xorg.conf for you.

---

### Post by schorsch on 2007-08-29
Please try:
```
sudo apt-get install xserver-xorg-dev
sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
envy -t
```

---

### Post by musicarvind on 2007-08-29
> **eeeeepuk said:**
> My recommendation would be to first get you back into x, albeit without the proprietory drivers (and as an aside, if you have compiz/beryl auto-starting this ISN'T going to work as they require the proprietory drivers), as I don't know about you but I find a graphical interface always helps. Once there we can look at getting your NVidia drivers working again.

We'll start by manually editing your xorg.conf file, being sure to make a backup first.



Replace "nvidia" with "nv" on the "Driver" line in the "Device" section relating to your video card. Hitting ctrl+o will allow you to save the file, and ctrl+x will close nano. You should then be able to get into x by typing



Now we're back in x, try double clicking the envy installer again, and let the gnome package manager (gdebi) try to install it. Hopefully this time it will tell you about any missing dependancies.

Once envy is installed you'll find a graphical tool to install the NVidia drivers under Applications -> System Tools -> Envy. As with the advice above, let Envyconfigure your xorg.conf for you.

this so absolutely worked! .. cheers .  you guys are a wonderful bunch.  finally in my ubuntu :) i did install envy and let it download Nvidia drivers for me. but i need to shutdown soon and so i cancelled it. supposed to download 24MB or something like that. will do that first thing tomorrow morning.  thanks again all.

---

### Post by lilbluegremlin on 2007-09-02
i have this same problem except i have an ati instead of an nvidia. i tried some of the things on here but they don't work or are not for my video card can anyone help me or point me in the right direction?
~Erik

---

### Post by lilbluegremlin on 2007-09-03
> **schorsch said:**
> Please try:
```
sudo apt-get install xserver-xorg-dev
sudo dpkg -i envy_0.9.7-0ubuntu8_all.deb
envy -t
```

so once i realized i had an ati not and invidia (some times im a real dunce.) i used schorch's suggestion and just deleted the old ati drivers and installed them again and it works now! thank you everyone for your suggestions!

~Erik

---

