---
title: "Where Can I Get The Linux Mint Menu?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-11-23
I stumbled upon a thread a few days ago and the link lead to a web site where you could install deb. packages from linux mint, in particular, the linux mint menu , but of course I cant find it now that I want it, anyone know? Thanks

---

### Post by corncob on 2007-11-23
Do you mean [HTML]http://www.linuxmint.com/software/[/HTML] ?

---

### Post by spiderbatdad on 2007-11-23
idk if you can get it in synaptic by adding the appropriate repository to /etc/apt/sources.list

## +++ Daryna (Linux Mint 4.0) +++
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna main upstream import
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna community
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna backport

for example if you are using Gutsy. Then sudo apt-get update and look through synaptic?
I tried Mint for a few days. It was "elegant" and the menu was nice, but I found it a little buggy, so I came back to Gutsy. Basically Mint is tagging along with Ubuntu developers. Mints next distro upgrade will be based on Ubuntu's next distro upgrade.

---

### Post by spiderbatdad on 2007-11-23
yup it's there. follow the link you can find it without adding the repo to your sources list.

---

### Post by prodigalson666 on 2007-11-23
Thanks alot for the help.

---

### Post by spiderbatdad on 2007-11-23
I just installed it. Thanks for the idea. I loved that menu. After unpacking it, I right clicked on the panel I wanted to put it on, chose add to panel, and it was there. After it's in the panel, I right click on the icon and gconf-editor opens. There I removed the word "Daryna" when I restarted, I just had the icon, so cool. Thanks again for the idea.

---

### Post by natehatewindows on 2007-11-23
how about a screen shot? i have never seen it and maybe i want it too :)

---

### Post by spiderbatdad on 2007-11-23
[http://www.linuxmint.com/screenshots.php](http://www.linuxmint.com/screenshots.php)

menu is like the ninth one over.

Here's mine:

---

### Post by natehatewindows on 2007-11-23
what file am i looking for?
to download it i mean

---

### Post by prodigalson666 on 2007-11-23
> **spiderbatdad said:**
> I just installed it. Thanks for the idea. I loved that menu. After unpacking it, I right clicked on the panel I wanted to put it on, chose add to panel, and it was there. After it's in the panel, I right click on the icon and gconf-editor opens. There I removed the word "Daryna" when I restarted, I just had the icon, so cool. Thanks again for the idea.

Thats a great tip, thanks again!

---

### Post by natehatewindows on 2007-11-23
are you guys talking about the grub menu?

---

### Post by prodigalson666 on 2007-11-23
Spiderbatdad, any idea on how to change the menu icon?

---

### Post by spiderbatdad on 2007-11-23
I edited my post with a screenshot of my desktop. If you follow this link:[http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) 
then scroll down till you see linux mint menu.deb, you'll get the package we are talking about.

---

### Post by spiderbatdad on 2007-11-23
> **prodigalson666 said:**
> Spiderbatdad, any idea on how to change the menu icon?
If you right click and choose preferences, you can look at it in gconf-editor. I would imagine you would have to have the icon you wanted in a file somewhere and then change the path to the icon to the file of the icon you wanted...I'm getting a little over my head here.

---

### Post by prodigalson666 on 2007-11-23
Thanks, I checked the editor but there isnt an entry for the icon picture, I'll keep searching.

---

### Post by irielion on 2007-12-03
Hi, I patched up the menu to fit into Ubuntu more nicely. Here is the deb.

---

### Post by shafin on 2007-12-04
is there any x64 version?

---

### Post by PeterDenStore on 2007-12-04
Hello,

Is there anyway to change the text on the Software Portal button? I changed the install_software_cmd key(preferences>mintMenu>plugins>system-management) to /usr/bin/gnome-app-install, so now I get the add/remove app instead of nothing. But I would like to change the button text to Add/Remove instead of Software Portal. Just wondering if anyway knows if this is possible and how to do it.

Thanks,
Pete

---

### Post by irielion on 2007-12-14
First i dont think you need x64 version cuz it is all written in python.
IF you want to change anything, look into the code.. In the deb i sent, i also took out some stuff it is not that hard

---

### Post by Sn3ipen on 2007-12-18
@irielion: I tied your patch but the Mint Menu still lokks the same.

Edit: Figured it out now. It just took some time before it showed up in "add to panel" or whatever it is called. Thanks. Works great:)

---

### Post by Sn3ipen on 2007-12-18
I noticed that the Mint Menu have a bug. If i have the resolution on the Bar bigger than standard. The menu wont fitt. Looks like the icon dont support resising or something like that.

[[IMG]http://img213.imageshack.us/img213/7853/mintmenuey7.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=mintmenuey7.jpg)

---

### Post by prodigalson666 on 2007-12-18
Wow! why are you using a pixel that high on  your task bar? It's not a bug, it's not meant to be distorted so much, dont forget its not native to the ubuntu desktop.

---

### Post by el_pombo on 2007-12-27
I installed this in AMD64 by typing "sudo dpkg -i --force-architecture mintmenu_3.0_i386.deb", it's working fine.

---

### Post by Sn3ipen on 2007-12-28
> **prodigalson666 said:**
> Wow! why are you using a pixel that high on  your task bar? It's not a bug, it's not meant to be distorted so much, dont forget its not native to the ubuntu desktop.

It is because i always have lots of windows open all the time and for me it is bether so i can sort the open windows in two rows. Just a habit i have. But it don't bother me that much.. The Ubuntu Menu don't have this behavior because the button can be resized. Anyway, I love the Mint Menu :)

Sorry for my late reply but i been busy in the holidays.

---

### Post by MangasColoradas on 2007-12-29
WOW!

Very cool! I have installed it and changed the text from 'Daryana' to 'Gutsy'. ;)

I am going to delete the top panel now, but before I do can someone tell me how to get it back please?


Nevermind I found the answer here.

[http://ubuntuforums.org/showthread.php?t=602205](http://ubuntuforums.org/showthread.php?t=602205)

---

### Post by Mular on 2008-01-03
Using the mint menu do you still get menu oddities <sp lol> 

I find in gnome that sometimes when I remove a program it doesn't go away. I looked up help on this and I am able to edit the menu but its glitchy sometimes I find all sorts of odd things in the other folder. Like for instance Wine I removed it from the menu by mistake when I uninstalled it, then when I reinstalled it - it never came back. So I made my own entry, and then installed games and they generated there own menu like normal. But every now and then if I edit the menu via the gnome menu editor, sometimes it glitches and moves things to the other folder =/

I really like the mint menu - does it do this as well? How is it generated and all that jazz?

---

### Post by cyberbuff on 2008-01-07
wow! great one!

---

### Post by erginemr on 2008-01-07
I also liked Mint menu a lot, reminds me of SuSE SLED menu. But apparently, two things are missing from the Mint menu: "Recent Documents" and "Search for Files", that keeps me stick to the original Gnome menu.

EDIT: And one more showstopper: It takes a whopping 15-20 MB of memory (shows up as Python inside Gnome system monitor) to run.

---

