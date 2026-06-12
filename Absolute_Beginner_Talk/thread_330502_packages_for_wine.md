---
title: "packages for wine"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by lucman on 2007-01-03
Hi!

Does anybody know what packages I need to install wine? How does it work?
Thanx

---

### Post by bartbes on 2007-01-03
If you add the wine repositories, and you use ```
sudo apt-get install wine
``` doesn't it install all the needed packages?

To add the wine repositories, press ALT+F2 and type ```
gedit /etc/apt/sources.list
```, and add ```

[I]deb http://wine.budgetdedicated.com/apt dapper main
[/I][B]if you are using Ubuntu Dapper Drake (6.06) or
[/B][I]deb http://wine.budgetdedicated.com/apt edgy main
[/I][B]if you are using Ubuntu Edgy Eft (6.10)
[/B]
```
then do ```

sudo apt-get update

```

---

### Post by axle_foley00 on 2007-01-03
If you are using Synaptic to install it you can just do a search for **wine** and install the package titled **wine**.

Or type: **sudo apt-get install wine** at the command line.

Then if you want to use wine, all you need is some **.exe** file and you type:

**wine /path/to/exe/file**

where */path/to/exe/file* is some path to the exe file that you would like to run/install. Once it is installed you can find your installed programs and run them from the following directory:

**/home/<yourusername>/.wine/drive_c/Program Files/**

You may need to show hidden files in order to find the **.wine** directory. To do that you can press **CTRL-H** on your keyboard.

For more info on using wine, you can check out [http://www.winehq.com]("http://www.winehq.com").

Hope that helps.

---

### Post by lucman on 2007-01-03
thanx i'll give it a try!

---

### Post by bodhi.zazen on 2007-01-03
[How to Wine](http://doc.gwos.org/index.php/HowToWine)

---

