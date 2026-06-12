---
title: "please help! urgent! installed package and now ubuntu won't boot"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by le garcon solitair on 2007-07-24
I've had ubuntu fiesty 64-bit for about a month now and, though i'm a bit new to linux, i love it but....

i've been attempting to imitate mac and i found a package to install the mac-style menu bar  ([here]("http://ubuntuforums.org/showpost.php?p=3024481&postcount=697")) so i downloaded it and used

> sudo dpkg --install --force-architecture libgtk2.0-0_2.10.11+macmenu_i386.deb

to install it and nothing happened so i attempted to log on and off, but after i logged off it never came to the login screen. so i restarted my computer and it said a few things and "no resume image, doing normal boot..." and i'm brought to just a command line interface.

i'm a bit new and i just don't know what to do. i suppose i would need to uninstall the package in the command line interface but i don't know how, so if anyone would be kind enough to write a command for me i would greatly appeciate it!

---

### Post by nichipet on 2007-07-24
You can try the same line you used before, but remove --force-architecture and replace --install with -r

I'm just taking this from a page on how to use dpkg. Here is the page: 
[http://rhadimas.wordpress.com/2006/10/13/install-dan-uninstall-paket-ubuntu/](http://rhadimas.wordpress.com/2006/10/13/install-dan-uninstall-paket-ubuntu/)

---

### Post by le garcon solitair on 2007-07-24
thanks so much for the response. i used

> sudo dpkg -r libgtk2.0-0_2.10.11+macmenu_i386.deb

and it said

> dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

---

### Post by le garcon solitair on 2007-07-24
after looking at the link you gave me, and then realizing that the command line was speaking to me in plain english, i realized i need the actual package name, not the file name, but i don't know that. how could i find it?

---

### Post by nichipet on 2007-07-24
Try

```
sudo dpkg --search macmenu
```

See what happens. --search is a dpkg option, but I'm not certain if the results of the search will be what -r wants.

---

### Post by le garcon solitair on 2007-07-24
i tried searching macmenu, but it found nothing. i don't know what else to search for.

---

### Post by anewguy on 2007-07-24
In your terminal just type in the following:

sudo dpkg -r libgtk2.0-0_2.10.11+macmenu_i386

See if that works - I think you have to leave the ".deb" off the end to have the package.

Let us know if it works or not.:)

---

### Post by le garcon solitair on 2007-07-24
tried that, and it says ignoring request to remove sudo libgtk2.0-0_2.10.11+macmenu_i386 because it isn't installed.

i'm assuming that means that's not the package name. plus, since it has macmenu in it, if it were the package name, it would have shown up in the search.

---

### Post by anewguy on 2007-07-24
Give me a few minutes - I'm going to shutdow Windows and boot Linux, then I'll see if I can duplicate your problem and if I can figure out how to remove it.:)

---

### Post by RomeReactor on 2007-07-24
Hi. I just downloaded the package and the library that gets installed is **libgtk2.0-0**; so you could try this:
```
sudo apt-get remove --purge libgtk2.0-0
```
then
```
sudo apt-get update
```
and finally
```
sudo apt-get install libgtk2.0-0
```
which will install **libgtk2.0-0** for x86-64, your architecture.

Here are screens of Gdebi with the package ready for installation:

---

### Post by le garcon solitair on 2007-07-24
THANK YOU SO MUCH ROME REACTOR!!!!!!!!!!

and everyone else as well =D

---

### Post by anewguy on 2007-07-24
Okay, I've downloaded and checked the package in archive manager and it puts a lot of stuff in your PC that I don't know what they are.  Some, like a new GTK may require some type of replacement.  I think the reason it can't be removed the way we have been trying is that I'm not sure it really became a package name (if that makes any sense,  SO--

YOU MORE EXPERIENCED PEOPLE OUT THERE:  COULD YOU CHECK THE .DEB "PACKAGE" FILE (i HAD TO THE LINK MENTIONED TO ACTUALLY GET THE FILE, AND THEN GIVE SOME INSTRUCTIONS ON WHAT TO DO TO REMOVE AND RECOVER FROM THIS?

THANKS!!:)

---

