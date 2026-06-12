---
title: "wget a folder?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-09-05
I want to wget a whole folder with the files in it.

This site gives away free Mp3 downloads, and I like it all. So I found there index map and im ready to go.
[http://www.hodie-world.com/media_files_wma_v/](http://www.hodie-world.com/media_files_wma_v/)

But how do I download it all, without having to click in to each folder, and download each file manually. Is it possible with wget?

I tryid 2 firefox extentions, flashgot and another one (cant remember the name), but didnt like them.

Can wget do this? and how?

---

### Post by tkjacobsen on 2006-09-05
wget -r -np -A wma -l 2 [http://www.hodie-world.com/media_files_wma_v/](http://www.hodie-world.com/media_files_wma_v/)

-r stands for recursivly
-l 2 is for two levels of recursion (this is to avoid to download too much, since wget recurces through links..)
-np no parent folders
-A wma only wma files

---

### Post by aktiwers on 2006-09-05
> **tkjacobsen said:**
> wget -r [http://www.hodie-world.com/media_files_wma_v/](http://www.hodie-world.com/media_files_wma_v/)

-r stands for recursivly

Nice thanks a lot Tkjacobsen

Eller tak ;)

---

### Post by tkjacobsen on 2006-09-06
Jeg er ked af jeg fik lavet rod i den.. Det virkede bare for mig sidst, men jeg har sikkert været heldig med siden... Har ændret i options, så skulle den kun downloade wma filer..


Just explaining why i messed up.. Have correted the command now

---

### Post by aktiwers on 2006-09-06
> **tkjacobsen said:**
> Jeg er ked af jeg fik lavet rod i den.. Det virkede bare for mig sidst, men jeg har sikkert været heldig med siden... Har ændret i options, så skulle den kun downloade wma filer..


Just explaining why i messed up.. Have correted the command now

Hehe du har skam ikke messed up..  It worked! 
Der står "Eller tak" (ikke sarkastisk) istedet for thanks, da jeg lige så du var fra Danmark og København. Ligesom mig ;)

---

### Post by tkjacobsen on 2006-09-06
Jeg prøvede bare lige selv. Så downloadede den bare hele siden inkl alt den linkede til... Men fint at det virkede.

---

