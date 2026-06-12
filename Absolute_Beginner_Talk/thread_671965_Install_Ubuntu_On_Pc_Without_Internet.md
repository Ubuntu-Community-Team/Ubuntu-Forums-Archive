---
title: "Install Ubuntu On Pc Without Internet"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by ariel bebbe on 2008-01-19
[B][SIZE="5"][SIZE="3"] i HAVE TO PC , ON THE FIRST PC I HAVE INSTALL UBUNTU AND 

SOFTWARE LIKE OPERA , JDK ,JRE ,VLC ETC; i WANT TO USED MY FIRST COMPUTER TO INSTALL THOSE SOFTWARE AND UBUNTU IN THE SECOND COMPUTER , IS IT POSSIBLE.WITH XP IT'S EASY I JUST HAVE TO COPY THE SETUP , I HAVE TRY IT WITH  UBUNTU BUT THERE ARE ALWAYS LIBRARIES MISSING , CAN I CREATE A CD/DVD CONTAINT ALL THE SOFTWARE FROM MY FIRST MACHINE AND INSTALL IT IN THE SECOND ONE ?[/SIZE][/SIZE][/B]

---

### Post by Saint Angeles on 2008-01-19
first thing: stop yelling at us.

second: ubuntu installs fine on a PC with no internet. internet shouldn't be a requirement for an OS install.

---

### Post by Malta paul on 2008-01-19
You can use APTonCD to transfer the packages you want from your online PC to your off-line PC.
Download using Applications>add/remove search for APTonCD.
Check also;[https://wiki.ubuntu.com/APTonCD](https://wiki.ubuntu.com/APTonCD)
Hope this helps:)

---

### Post by mikewhatever on 2008-01-19
Hey ariel, ever heard of Caps Lock button?

---

### Post by dustman on 2008-01-19
you could try "Ghost for Linux". It's a free program that comes as an .iso that can be burnt on a CD - a bootable CD (more info here: [http://pcquest.ciol.com/content/linux/2005/105041202.asp](http://pcquest.ciol.com/content/linux/2005/105041202.asp)).

---

### Post by ugm6hr on 2008-01-19
You can just install using the Install CD on the second computer.

Assuming you have the same version of Ubuntu on both - you can just copy all the files from var/cache/apt/archives from the first onto the second (in the same directory), then use a dpkg -i command to install them all.

---

