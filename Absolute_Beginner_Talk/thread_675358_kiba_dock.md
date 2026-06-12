---
title: "kiba dock"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by boboyo on 2008-01-22
i would like to have kiba-docks.
few weeks ago, i installed it but it said something about a missing plugin or something.
now, when i try to turn it on, i cant but i can open the settings.
does anyone have kiba for 64-bit

---

### Post by ajmorris on 2008-01-22
> **boboyo said:**
> i would like to have kiba-docks.
few weeks ago, i installed it but it said something about a missing plugin or something.
now, when i try to turn it on, i cant but i can open the settings.
does anyone have kiba for 64-bit

Hi there,
im have kiba on my 64bit, however, it doesnt run, when i add launchers to it, it does nothing, and adding a separator to it, gets a segmentation fault. However, kiba does run on 64bit, so we should be able to get yours working,
Could you please open up the CLI (ALT + F2, and then in the dialog box that appears, type gnome-terminal)

Start kiba dock through this terminal, and post any output that appears (start kiba with 'kiba-dock')

---

### Post by boboyo on 2008-01-23
i have a question.
how did u get hardy heron?

---

### Post by Paul820 on 2008-01-23
Hardy heron isn't stable yet, there will be loads of things going wrong with it. It is recommended to only use it for testing and bug reporting. But..if you still want it [http://www.ubuntu.com/testing/hardy/alpha3]("http://www.ubuntu.com/testing/hardy/alpha3")
Don't ask for help here as nobody will have a clue how to help you :)

---

### Post by boboyo on 2008-01-25
when i start kiba trought terminal, this is what is written.

** (kiba-dock:7862): WARNING **: Error (main.c @ line 252):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

---

### Post by dark_harmonics on 2008-01-26
yes same here. it seems that the kiba-plugins dont compile right. i get errors during the make process.

```
launcher.c:41:27: error: kiba-key-file.h: No such file or directory
 
```

---

### Post by boboyo on 2008-01-30
wat should i do?

---

### Post by x1a4 on 2008-01-30
To install Kiba plugins

In a terminal execute: 
```
sudo apt-get install kiba-plugins
```
or
```
sudo aptitude install kiba-plugins
```

Or
Open Synaptic, search for kiba-plugins, select kiba-plugins for installation, press the Install button.

---

### Post by boboyo on 2008-02-02
it dosnt work
here is what is written
E: Couldn't find package kiba-plugins

---

### Post by x1a4 on 2008-02-03
> **boboyo said:**
> it dosnt work
here is what is written
E: Couldn't find package kiba-plugins

Sorry, forgot to tell you to update your repositories first.

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

Append the following to your /etc/apt/sources.list:
```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
Or, if you use Synaptic 
Settings -> Repositories -> Third-Party Software tab -> Add button

Update your package lists by clicking the Reload button, or: 
```
sudo aptitude update
```
Or
```
sudo apt-get update
```

---

