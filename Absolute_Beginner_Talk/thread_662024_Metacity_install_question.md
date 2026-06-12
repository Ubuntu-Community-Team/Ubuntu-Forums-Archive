---
title: "Metacity install question"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by ckamc on 2008-01-08
So I followed the install featured on this other site

[http://epologetics.org/ubuntuhowto.php](http://epologetics.org/ubuntuhowto.php)

Now I am down to the "start using it" portion

i am still in /home/*user*/metacity in terminal and when I type in

> gconftool-2 --set --type=bool /apps/metacity/general/compositing_manager true

nothing happens

and doing sudo make install just does what I have (think) installed already

basically, how do I launch/get this started now?

thanks for your help

---

### Post by ckamc on 2008-01-08
Here are the instructions I followed in the link posted above

> 
Install required packages     

sudo aptitude install subversion gnome-common build-essential autoconf gnome-devel libtool

Build Metacity
     
svn co [http://svn.gnome.org/svn/metacity/branches/iains-blingtastic-bucket-o-bling/](http://svn.gnome.org/svn/metacity/branches/iains-blingtastic-bucket-o-bling/) metacity
cd metacity
/bin/bash autogen.sh
./configure --enable-compositor
make

---

