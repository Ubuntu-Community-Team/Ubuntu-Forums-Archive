---
title: "installing deb packs"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-18
i downloaded the skype deb pack how do i install it??

---

### Post by krusbjorn on 2005-08-18
open a terminal, navigate to the download location and type > dpkg -i <name-of-package.deb>

Edit: This is a better way, btw.

Add this line to your /etc/apt/sources.list file

> deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

and then "sudo apt-get update", "sudo apt-get install skype"

---

