---
title: "desperately NEED HELP installing a GTK+ engine."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-07-20
hello, i need some help haha.

ive been attempting to install and use this...

[http://www.gnome-look.org/content/show.php?content=41345](http://www.gnome-look.org/content/show.php?content=41345)

basically what i get out of it is that its a special engine written to handle a certain type of gui for linux. ive followed all the instructions i can find but cant get it to work.

i downloaded the source and attempted to use that because the supposed "Ubuntu version" is a .deb file

so i tryed to compile the source. heres what i did, i extracted the source onto my desktop for easy finding.

opened up the terminal and navigated to its folder.

now the readme file says to use ./configure --enable-animation so i type that in.

it starts to configure but then says that it created a config.log because something is wrong.

so i read it and it makes no sense to me at all.

i then asked about it on the forums here and a guy tells me that i need build-essential so i got that.

attempted again and it seemed to configure it ... maybe not i dont know

then im told to type in "make" and this is where i get a little confused cause in the terminal it seems all that is happening is that the program is accessing the folder with the files in it OVER AND OVER AND OVER... around 900 times to be exact.... doesnt seem to do anything


WHAT AM I DOING WRONG.... PLEASE HELP ME!!!

---

### Post by OU812 on 2006-07-20
I'm surprised its not in any of the repos. I'm pretty sure xfce is a gtk based desktop and there is xubuntu. Try to find a debian package so you don't have to install it from source.

john

---

### Post by mattisking on 2006-07-20
> **Mangledbmx said:**
> hello, i need some help haha.
ive been attempting to install and use this...
[http://www.gnome-look.org/content/show.php?content=41345](http://www.gnome-look.org/content/show.php?content=41345)

...

i downloaded the source and attempted to use that because the supposed "Ubuntu version" is a .deb file


Ubuntu installation packages ARE .deb files. Download the deb to your home folder: 
[http://prdownload.berlios.de/candido/gtk2-engines-candido_0.2-1_i386.deb]("http://prdownload.berlios.de/candido/gtk2-engines-candido_0.2-1_i386.deb")

Open a new terminal, making sure you're in your home folder (which you will be unless you've changed things around). Look to see the file is there and then just type:

sudo dpkg -i gtk2-engines-candido_0.2-1_i386.deb

---

### Post by AirRaven on 2006-07-20
Alternatively, for a far easier way of doing things, just double click the .deb file if you're running Dapper. 

It opens the GDebi package manager- it installs the .deb for you without any fuss.

---

