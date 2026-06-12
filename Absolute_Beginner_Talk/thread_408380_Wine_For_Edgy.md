---
title: "Wine For Edgy"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-13
My Add/Remove Manager for some reason do not refresh and find the WINE program. how do i get it to find and install it?

---

### Post by garybrlow on 2007-04-13
Errm only the wine configuration and utilities can be found in the menu. To run programs you either right click on an executable using the file manager and choose run with other application and type wine on the command section. You can also use the terminal and run a windows executable like this: wine application.exe.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by anaconda on 2007-04-13
I might be wrong here, but I think add/Remove doesnt have all available programs.

Use synaptic instead. just search for wine. if synaptic cant find wine then it might be in universe/multiverse repositories, so you should enable those in synaptic.

Or from the terminal:
sudo apt-get install wine
should do the trick.

---

### Post by JayDeePlus on 2007-04-13
so how do you use "wine" to get plugins for beryl, like the snow effect and other plugin? so your saying wine is only a command? i thought it was a windows emulator.

---

### Post by AndyCooll on 2007-04-13
I'm not sure which repository Wine is in (I think it may be in the multiverse, someone else may be able to confirm this). If so, you would need to enable this repository.

And two other installation methods worth considering:

1. From the command line:
```
sudo apt-get install wine
```

2. Try installing using Synaptic (System > Administration > Synaptic Package Manager).

:cool:

---

### Post by artir on 2007-04-13
JUst wait until 19 to get Feisty with wine ready to install. TO install it on edgy, do this:.

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install wine
winecfg

You can also download the Artir&#347; wine configurator here: and execute it in console.

---

### Post by JayDeePlus on 2007-04-13
So 

sudo apt-get install wine

Will go and find the install for it and will install for me? how will i then run it afterwords. will it be in the same menu the my beryl manager is in?

---

### Post by AndyCooll on 2007-04-13
> **JayDeePlus said:**
> so how do you use "wine" to get plugins for beryl, like the snow effect and other plugin? so your saying wine is only a command? i thought it was a windows emulator.

Well ...Wine Is Not an Emulator hence the name of the program. In truth it operates very much along the lines of an emulator. However it works more like an "interprator" in that it "interprates" Winderz code into Linux code, and hence works behind the scenes. There isn't a GUI for it. When a Winderz program runs it will run on your Linux desktop, and in many cases you wouldn't know it is actually using Wine to run.

:cool:

---

### Post by frodon on 2007-04-13
If you want a GUI to use wine there's some commercial solutions like crossover which gives excelent results but you have to pay for it.
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)
Wine alone do pretty much the same but often need some tweaking or is in general less user friendly.

---

### Post by JayDeePlus on 2007-04-13
ok so if i wanted to get like plugins for beryl i can just go to synaptic, search for the plugin i'm looking for and wine will automatically install it correctly on my machine? even the .exe files?

will it automatically load and install the .exe and .rar files?

---

### Post by frodon on 2007-04-13
I think you make a confusion, wine is a program which allows you to run windows softwares, it has nothing to do with beryl at all.
If you want beryl plugins you need to install beryl, they are included in.

Now to install beryl it depends of the version of ubuntu you are using.

---

### Post by JayDeePlus on 2007-04-13
ok, but wine is about to install and setup .exe and .rar programs through right?

---

### Post by frodon on 2007-04-13
Wine is useful when you are obligated to run a windows software because there's no linux equivalent, so yes it's made to run .exe files.
You can't run all windows apps with wine but most of them works just great with wine.

---

### Post by AndyCooll on 2007-04-13
> **JayDeePlus said:**
> ok, but wine is about to install and setup .exe and .rar programs through right?

Wine merely acts as "the middleman" so to speak between your Linux operating system and Winderz programs. So, to simplify things, when you click on an exe (for instance) Wine boots into action and translates the exe's Winderz code into Linux code and then vice-versa. The upshot of this is that it means many apps written for Winderz will also run under Linux.

For instance, my Football Manager game will run under Linux even though it is a Winderz only program. This is because everytime I click on the FM icon the game boots up, but also behind the scenes Wine kicks into action too!

:cool:

---

