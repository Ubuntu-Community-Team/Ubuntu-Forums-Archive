---
title: "error using apt-get"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by napa on 2005-07-12
I tried to install a statistics package R using the following command, but got error

root@phyr:/ # apt-get install R
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package R
root@phyr:/ #


Any one can give me some help on this, what does this message means?

Thanks!

---

### Post by Xian on 2005-07-12
APT will only install certain file formats.
On Ubuntu the format needs to be a .deb file.

For example:
# apt-get install packagename.deb

Most people just place the .deb file in their /home/username path.
Then issue this command:

$ sudo dpkg -i packagename.deb

---

### Post by napa on 2005-07-12
you know i am a beginner of linux.

But what is the format of .deb file?

how can i get the list of package names in Ubuntu?

---

### Post by Xian on 2005-07-12
A .deb file is a pre-compiled package that has been specifically designed to work on a specific system type. In short, it is a 'debian'-like package and thus the name. Ubunutu uses this file type as it was derived from [Debian](http://www.debian.org/), but it is always best to use packages from Ubuntu's own software repository, as not all .deb files are good replacements on Hoary.

You can browse the software selection in either [Synaptic](https://wiki.ubuntu.com/SynapticHowto?) or the [online](http://packages.ubuntu.com/) repository searchable index.

---

### Post by napa on 2005-07-12
Thanks!
 Now I know what you mean by a deb file. 

But say when I try to install package octave, it depends one a bunch of other packages. Do I need to install each one at a time? Or there is a short way to install all the dependency packages together?

---

### Post by odin on 2005-07-15
apt will look for the dependencies and will install those packages too.It'll ask you first so you just say yes if you agree with the packages it'll installed and that's it.

---

