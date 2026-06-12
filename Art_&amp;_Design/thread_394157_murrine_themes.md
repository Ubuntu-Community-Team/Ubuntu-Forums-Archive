---
title: "murrine themes"
date: 2007-03-26
forum: Art &amp; Design
---

### Post by dbbolton on 2007-03-26
i need a bit of help installing murrine themes in dapper.

first, i installed the package [gtk2-engines-murrine_0.12-1_i386.deb]("http://cimi.netsons.org/media/download_gallery/murrine/gtk2-engines-murrine_0.12-1_i386.deb")

next, i installed a murrina metacity theme, and a murrina GTK theme. the metacity theme works perfectly. however, when i select the murrine theme in System > Preferences > Theme > Theme Details > Controls, it just displays the default gnome controls. i attached a screenshot to display the problem.

any ideas?

edit: i also tried using the murrine configurator, to no avail.

---

### Post by codejunkie on 2007-03-26
> **dbbolton said:**
> i need a bit of help installing murrine themes in dapper.

first, i installed the package [gtk2-engines-murrine_0.12-1_i386.deb]("http://cimi.netsons.org/media/download_gallery/murrine/gtk2-engines-murrine_0.12-1_i386.deb")

next, i installed a murrina metacity theme, and a murrina GTK theme. the metacity theme works perfectly. however, when i select the murrine theme in System > Preferences > Theme > Theme Details > Controls, it just displays the default gnome controls. i attached a screenshot to display the problem.

any ideas?

edit: i also tried using the murrine configurator, to no avail.
that version of murrine you downloaded was probably packaged for a newer version of ubuntu like edgy or feisty, it is not compatible with dapper  since they use a different version of gtk. download the source files and compile the murrine engine or try and find a version that was packaged for dapper.

---

### Post by dbbolton on 2007-03-26
i got an array of errors trying to compile it. i'll live with regular gtk for now.

thanks

---

### Post by wj32 on 2007-03-27
Do you have KDE installed? If so, delete ~/.gtkrc-2.0 or something like that.

---

### Post by dbbolton on 2007-03-27
> **wj32 said:**
> Do you have KDE installed? If so, delete ~/.gtkrc-2.0 or something like that.
no, just gnome.

i figured out that *some* themes work, some won't. i don't know why.

---

### Post by kpolice on 2007-03-27
Some work and some don't because it is an old murrine version and you need the latest to make every theme work.

---

### Post by codejunkie on 2007-03-27
here's the steps you need to take, to compile murrine from source hope this gets it fixed for you.

first make sure you have enabled the multiverse and universe repositories in your sources.list file.

now download the source package from [**[COLOR="DarkRed"]HERE[/COLOR]**]("http://cimi.netsons.org/media/download_gallery/murrine/murrine-0.51.tar.bz2"), and extract the source package.

before compiling you need to install dependencies first, copy and paste this in a terminal this will install all packages required to build murrine.
```
sudo apt-get install linux-headers-`uname -r` build-essential checkinstall libgtk2.0-dev imagemagick
```

when this finishes your ready to build the source package open a terminal and cd into the source dir, and run this command
```
./configure --prefix=/usr --enable-animation
```
when this finishes correctly run 
```
make
```
when this is complete your ready to install murrine with this command 
```
sudo make install
```
now go to www,gnome-look.org download some themes for murrine and enjoy

i hope this helps if you have any trouble when compiling please post the errors here and i'll be more than happy to try and help you fix it.

---

