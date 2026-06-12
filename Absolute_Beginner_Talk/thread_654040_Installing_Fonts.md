---
title: "Installing Fonts"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by thecrimsonalchemist42 on 2007-12-30
I have yet another beginner's question. I was wondering how do I install new fonts? On Fedora you just stick them in the hidden .font folder, but how do I in Ubuntu? I'd also like to thank everyone for the good and speedy help :).

---

### Post by Bachstelze on 2007-12-30
Same thing.

```
mv /path/to/my/font.ttf ~/.fonts
```

You will have to create the directory if it does not exist :

```
mkdir ~/.fonts
```

---

### Post by gn2 on 2007-12-30
Or use Synaptic Package Manager and search for and install fonts, or in a terminal run

```
 sudo apt-get install ubuntu-restricted-extras 
```

Which will install a whole bunch of useful stuff including microsoft core fonts.

---

### Post by thecrimsonalchemist42 on 2007-12-30
> **gn2 said:**
> Or use Synaptic Package Manager and search for and install fonts, or in a terminal run

```
 sudo apt-get install ubuntu-restricted-extras 
```

Which will install a whole bunch of useful stuff including microsoft core fonts.

Last time I tried installing that it made my Add/Remove programs thing stop working completely  which forced me to reinstall Ubuntu completely.

So let me get this straight guys... I don't understand Linux code too well, do I just go to the home directory and create a .font folder?

---

### Post by frenchsquared on 2007-12-30
I have questions about same thing

my .font folder is already made but how do I acces it

I ran sudo apt-get install ubuntu-restricted-extras but no idea what it did

---

### Post by autocrosser on 2007-12-30
In Nautilus you goto the preferences & Tic the "show hidden and backup files" checkbox.  File Browser>Edit>Preferences>Views

You will then be able to see all your .files

---

### Post by jordanmthomas on 2007-12-30
> **frenchsquared said:**
> I have questions about same thing

my .font folder is already made but how do I acces it


Please note that the folder is .fonts and not .font
After putting files in your .fonts folder, run this:
```
sudo fc-cache -f
```
to regenerate the font cache.

---

### Post by frenchsquared on 2007-12-30
what is nautilus?

---

### Post by gn2 on 2007-12-30
> **frenchsquared said:**
> what is nautilus?

It's the default file browser in Ubuntu.

---

### Post by ragadanga63 on 2008-01-08
> **jordanmthomas said:**
> Please note that the folder is .fonts and not .font
After putting files in your .fonts folder, run this:
```
sudo fc-cache -f
```
to regenerate the font cache.

The correct command should be "sudo fc-cache -fv"

---

### Post by ragadanga63 on 2008-01-08
Nautilus is the default file manager of Ubuntu-much like Windows Explorer.

---

### Post by jordanmthomas on 2008-01-08
> **ragadanga63 said:**
> The correct command should be "sudo fc-cache -fv"

This does the exact same thing as my command, except it prints out what it is doing.  My command was correct as well.

---

