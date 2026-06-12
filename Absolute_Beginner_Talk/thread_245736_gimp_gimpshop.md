---
title: "gimp/ gimpshop?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by xprlt on 2006-08-28
hi, Im a noob.
so I wanted gimpshop, and I was searching for a deb. package, and I found one of some chinese site.
then I figured, first uninstall gimp. so I did.
then I downloaded that chinese gimpshop, and it seemed to install properly.
but then I didnt see it in my applications menu.
so then I thought maybe I need to install gimp again, who knows, Im a total noob to linux , I basically havent gota clue.
so I did, and it was in the app. menu, but then when I click it, it sais:

Your GIMP installation is incomplete:

Failed to open file '/home/suramya/Temp/GimpShop/gimpshop//share/gimp/2.0/menus/toolbox-menu.xml': No such file or directory

Plase make sure the menu XML files are correctly installed.


so, it doesnt work anymore. in symnaptic package manager I found all kinds of XML stuff , so I installed that, but that didnt help eighter. it probebly has nothing to do with it anyway.

so after all that I tried to reinstall that gimpshop again, but that gives an error too.

maybe someone here can help me out, please? Im pretty much confused.

---

### Post by jcrnan on 2006-08-28
I dont know the answer sorry, but this gimpshop seems rather interesting. Two questions:

1. does it support keyboard shortcuts?

2. Is it a free english version anywhere? Preferably as a debfile so I know how to use it ^^

---

### Post by janbockaert on 2006-08-28
sometimes trial and error is not a good idea ;)

That u don't find gimpshop in your menu is not because it isn't installed Try to run gimpshop in a terminal. If it is installed it should run (but maybe you broke it with installing the gimp over it?) if it isn't installed as it should, you will see what is wrong with it in your terminal.

if gimpshop works, go to the alacarte menu editor (if u use gnome) and ad a new menu entry manually in the editor. (file > ad menu just type gimpshop somewhere in the entry field)

However, if you are not very experienced with photoshop, there is no good reason to use gimpshop over gimp. Gimp is supported by ubuntu, so you will always have a up-to-date and stable version, working in ubuntu. Gimpshop is not supported, and is not installed with a repositorie. Maybe (if you are a noob) working with repositories may be a little confusing,(it was in my early linux-days) but in linux, if you can install it from a repositorie, you better do it. Whatever version of gimpshop u use, gimp will always be more up to date and more stable.

If you think gimp is to hard to learn (it did take me some time and a lot of reading to master it a little bit). you should try fspot as an easy to use alternative. 

i work with gimp and fspot, and i m very happy with them.:D

---

### Post by jcrnan on 2006-08-28
janbockaert: I actually am rahter experienced in PS and gimp really doesnt live up to my standards :p

---

### Post by takayuki on 2006-08-28
here's a link with instructions to install gimpshop via a deb package...

[http://ubuntuforums.org/showthread.php?t=239277&highlight=gimpshop+.deb](http://ubuntuforums.org/showthread.php?t=239277&highlight=gimpshop+.deb)

another good image editor is pixel.  

[http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)

it's very promising.  i use photoshop on my mac, but pixel in linux is very, very similar to photoshop.  pixel isn't quite ready for prime time yet, but it gets better and better with each update.

---

### Post by bruce89 on 2006-08-28
Gimpshop is just the same as the GIMP, but with different menu layouts.

---

### Post by xprlt on 2006-08-28
> **janbockaert said:**
> sometimes trial and error is not a good idea ;)

That u don't find gimpshop in your menu is not because it isn't installed Try to run gimpshop in a terminal. If it is installed it should run (but maybe you broke it with installing the gimp over it?) if it isn't installed as it should, you will see what is wrong with it in your terminal.

if gimpshop works, go to the alacarte menu editor (if u use gnome) and ad a new menu entry manually in the editor. (file > ad menu just type gimpshop somewhere in the entry field)

However, if you are not very experienced with photoshop, there is no good reason to use gimpshop over gimp. Gimp is supported by ubuntu, so you will always have a up-to-date and stable version, working in ubuntu. Gimpshop is not supported, and is not installed with a repositorie. Maybe (if you are a noob) working with repositories may be a little confusing,(it was in my early linux-days) but in linux, if you can install it from a repositorie, you better do it. Whatever version of gimpshop u use, gimp will always be more up to date and more stable.

If you think gimp is to hard to learn (it did take me some time and a lot of reading to master it a little bit). you should try fspot as an easy to use alternative. 

i work with gimp and fspot, and i m very happy with them.:D
if I run gimpshop in terminal, it sais command not found. thats all. so that means that its not installed? when I try gimp in terminal, it starts, as I described in my first post, but breaks off, and a window sais:> " Failed to open file '/home/suramya/Temp/GimpShop/gimpshop//share/gimp/2.0/menus/toolbox-menu.xml': No such file or directory "
so neighter work, gimp seems to be in conflict with some gimpshop files. 

what I really want right now, is to get rid of all the gimpshop files I installed, sothat I can run gimp again, but I dont know how...Ill look at fspot, thanks.

---

### Post by deadgobby on 2006-08-28
I tried to load up gimpshop with gimp. They do not like each other at all. So you most like need to go into Synaptic and remove gimpshop. Reinstall Gimp through Synaptic. 
Gobby

---

### Post by xprlt on 2006-08-28
oh and I allso cant remove GIMP with add/remove, it sais one ofr more applications depend on it..

---

### Post by xprlt on 2006-08-28
> **deadgobby said:**
> I tried to load up gimpshop with gimp. They do not like each other at all. So you most like need to go into Synaptic and remove gimpshop. Reinstall Gimp through Synaptic. 
Gobbythat was helpfiull, thanks. Ive uninstalled gimpshop. next thing that comes to mind, is, how do I remove all gimpshop files from my pc, allso out of this synaptic list? (edit: nevermind, Ive completely removed it..) 
it seems that gimp is starting up again, now, but it crashed when I wanted to quit...:(

---

### Post by jcrnan on 2006-08-28
o, is it unadvisable to install gimpshop? does it kill my gimp? Anyone know if it allows for shortcuts to be used?

---

### Post by janbockaert on 2006-08-28
if gimp does not live up to your standards, gimpshop won't also. It is basically the same program with different menu entries. And it is not supported by ubuntu. If you want to use PS in ubuntu, best thing you can do is buy crossover office and install PS ([http://www.codeweavers.com/](http://www.codeweavers.com/)) 

I believe freespire has gimpshop instead of gimp in its installation. So i guess it is possible to download freespire and play with the life cd so you can see for yourself if gimpshop is a ps killer.

i didn't install gimpshop in linux, so i don't know if it kills gimp, but after reading this thread, i guess it does.

---

### Post by janbockaert on 2006-08-28
oops, not freespire (lphoto) but Dreamlinux has gimpshop in its installation: ([http://www.dreamlinux.com.br/english/imagens/Tela5.jpg](http://www.dreamlinux.com.br/english/imagens/Tela5.jpg)) hope you didn't start downloading. I m also not sure if dreamlinux has a life cd, so that makes my last post rather useless. sorry for that.:oops:

---

