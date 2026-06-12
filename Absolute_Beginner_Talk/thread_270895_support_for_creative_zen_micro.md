---
title: "support for creative zen micro"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-10-03
i have a creative zen micro and i was wondering if there is any program out there that will allow me to detect the player and add content as well as change it.

it does have play for sure firmware on it and i have a feeling that will make things alot harder. thanks alot.

---

### Post by comppsyco on 2006-10-03
If someone has an answer, that would be great! It's one of my blocks to moving to full time ubuntu.

---

### Post by Marsolin on 2006-10-03
[KZenExplorer]("http://linuxappfinder.com/package/kzenexplorer") supports the Creative Zen Micro.

---

### Post by comppsyco on 2006-10-03
I realize that this is a basic question, but I've never needed to do this before: How do I run a Qt app in Gnome?

---

### Post by drr422 on 2006-10-03
you could also try gnomad2 as well, it worked for me. Follow this guide:
[http://ubuntuforums.org/showthread.php?t=199250&highlight=micro+zen+mtp](http://ubuntuforums.org/showthread.php?t=199250&highlight=micro+zen+mtp)

It may be frustrating and irritating, but searching intensively throughout the forums will usually produce a solution to your problem.  Just remember, since your joining this great big ol' community, there are many people who have probably done exactly what your trying to do.  

Dustin

---

### Post by Hranj on 2006-10-03
yeah. ive had nothing but problems trying to do things on ubuntu. but its free and its got a great community thats willing to help out. ill try both of those soon. as for now i dont feel like throwing a fit while most of my family is sleeping.

---

### Post by Marsolin on 2006-10-04
> **comppsyco said:**
> I realize that this is a basic question, but I've never needed to do this before: How do I run a Qt app in Gnome?

There's nothing special to it. If you install the program through Synaptic or Add/Remove Programs then any extra files you need will be automatically taken care of. At that it's run just like any other program.

---

### Post by werewolf on 2006-10-31
I've installed gnomad2 and it dependencies, all that stuff.  Device manager recognizes that I have a creative player on the USB, but it thinks it's a camera.  The import photos window even pops up and wants to import all the .mp3 files, but gnomad2 doesn't see it.

---

### Post by drr422 on 2006-11-12
The same thing happened to me after I installed edgy, but gnomad2 works for me in dapper though.  Its kind of interesting though, cause i think i was able to actually transfer songs from the creative zen micro to my desktop, just not the other way around yet.

---

### Post by cutlerite on 2006-12-10
> **Marsolin said:**
> [KZenExplorer]("http://linuxappfinder.com/package/kzenexplorer") supports the Creative Zen Micro.

I installed this through synaptic package manager, and I can't find the program to actually use it.  I have no idea where it installed to.

I'm using edgy.

---

### Post by zekopeko on 2006-12-10
open synaptic and search for the package that you installed (in this case KZenExplorer) then right click on the package > Properties.

look for Installed Files tab and under there look for something like :

/usr/share/bin/<name of package/command>

the part after /bin is probably the name of the command used too run the app.

this is how I do it when the program doesn't get in the applications menu.

---

### Post by Marsolin on 2006-12-10
It has a menu entry, but it might not have refreshed yet. Go ahead and press ALT+F2 and type kzenexplorer to run the program.

---

