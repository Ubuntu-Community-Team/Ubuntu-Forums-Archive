---
title: "How to install all types of Packages(rpm,deb.. etc) in Debian distro ?"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by stephen_star on 2006-05-11
Hi all,

    Could anyone help me to install all types of packages in Debain distro on  a single click?. I dont want to use Kpackage. I want to go for Gdebi but i dont know how to install it in debain?. Can anyone help me to install gdebi in debain?

  I checked the dadebstaller ( by dabear) for installing debian packages which is working fine but not with RPM packages. Can anyone tell me what are the tools available to install all types of linux packages in Debain? . 


Thanks in advance,


Regards
stephen:-|

---

### Post by revdev on 2006-05-18
Sorry, I don't know about any sort of "one-click" method, but you can install debs by running ```
sudo dpkg -i whatever.deb
``` in a terminal.

for installing rpms, first you need to ```
sudo apt-get install alien
``` and then ```
sudo alien whatever.rpm
``` ... this will generate a .deb that you can install using the above method.

---

### Post by Sef on 2006-05-18
Check out these two sites:

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

---

