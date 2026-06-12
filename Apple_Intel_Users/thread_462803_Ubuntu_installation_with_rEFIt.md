---
title: "Ubuntu installation with rEFIt"
date: 2007-06-03
forum: Apple Intel Users
---

### Post by liberalist on 2007-06-03
Hi everyone,

I am trying to turn my Mac into a dual-boot machine. Since I have already made 2 partitions (one system partition and one for files), BootCamp does not work. I want to use 20-30 GB of space from my 2nd (file) partition for installation of Ubuntu. I am not a big fan of Gparted (as it will not allow me to resize my 2nd HFS+ partition), is there any other way? Is this possible and how can I make this work with rEFIt? 

Thank you very much in advance for your help.

PS: I know about [http://www.mactel-linux.org/wiki/Dual_Booting](http://www.mactel-linux.org/wiki/Dual_Booting)
[http://felipe-alfaro.org/blog/2006/08/19/installing-ubuntu-linux-on-a-macbook-pro/](http://felipe-alfaro.org/blog/2006/08/19/installing-ubuntu-linux-on-a-macbook-pro/)

---

### Post by kzm. on 2007-06-03
i used the commandline for the partitioning:
sudo diskutil resizeVolume disk0s2 20G "Linux" linux 100G
and then installed refit:
[http://refit.sourceforge.net/#download](http://refit.sourceforge.net/#download)
click on the installer in the archive.

it works all very nicely and easy.

---

### Post by liberalist on 2007-06-03
I now have a 20 GB hard drive partition for my files... I wish to revert back to my two partition scheme, so one for my system and 120 GB for my files. How can I achieve this?

---

### Post by ronocdh on 2007-06-03
> **liberalist said:**
> I now have a 20 GB hard drive partition for my files... I wish to revert back to my two partition scheme, so one for my system and 120 GB for my files. How can I achieve this?
I'm sorry, but I don't think you have been very clear about the nature of your partition scheme as was originally and how you would like it to be. Please try to post back more explicitly; I assume kzm's advice did not work because he was not certain what you meant by "files partition."

---

