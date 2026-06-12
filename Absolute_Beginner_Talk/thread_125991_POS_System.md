---
title: "POS System"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Screwworkn on 2006-02-05
Preamble:
I'm very new to the linux world.  I am very good at the dos world.  I have gotten my dos application working in dosbox.  From everything I've read I need to run it in dosemu for printers to work the way I need.

Questions:

1. I can run dosemu w/o loading up xwindows,  correct?
2. How can I have ubuntu boot to the command line directly?
3. Is ubuntu the best linux distro when all I want to do is have the system boot up, detect network card & dhcp and start a dosemu session?

Thanks
Chris

---

### Post by bartbes on 2006-02-05
why would you want to run linux to run dos? what's the point? why not just install dos then?

---

### Post by Screwworkn on 2006-02-05
I want to have some internet capabilities on the system.  Mostly for ftp, but also remote access.  

Chris

---

### Post by bartbes on 2006-02-05
and that isn't possible on dos??

But I think if you're using linux why not getting used to the LINUX KERNEL instead of dos

and to get back to question 2:
Just don't install a GUI (GNOME/KDE) or remove it, it will only save space if you don't use it

---

### Post by Screwworkn on 2006-02-05
Once you load up everything you need to run tcp/ip on a dos system, you don't have any more memory to run my pos system and you can't file share directly in a dos system.

My pos system will not run in dos, so if you mean get use to the linux kernal, I can't recompile the program to run in linux. 

About #2, In dos I have an autoexec.bat file that I can edit what happens when the system starts up.  I don't mind have a gui on the system, since it'd be nice to load up when I want to browse the web for something.  But I'd like to be able to boot to the command prompt and then only go into the gui when I type startx.  what file do you edit to change the load up sequence ala autoexec.bat?

Thanks
Chris

---

### Post by bartbes on 2006-02-05
You can download sysv-rc-conf ```
sudo apt-get install sysv-rc-conf
``` to edit the runlevels just type ```
sudo sysv-rc-conf
``` and put out the crosses by gdm and/or kdm and when you want to start the GUI type ```
sudo /etc/init.d/gdm
or
/etc/init.d/kdm
```

GDM is standard for Ubuntu (GNOME) and KDM is standard for Kubuntu (KDE)

EDIT:

alternatively you can use KSysV (standard included with Kubuntu (KDE))```
sudo apt-get install ksysv
```

---

### Post by Screwworkn on 2006-02-05
When I do "suso apt-get install sysv-rc-conf" I get an error message saying:

E: Package suso apt-get install sysv-rc-conf has no installation candidate

Note:  I am doing this from a terminal inside of gnome.

Chris

---

### Post by Screwworkn on 2006-02-05
Ok, I figured it out.  I had to enable universal repository.  

Chris

---

### Post by twotonz on 2006-05-29
Hi,
 I was very interested in your post, I am tring to do something simular here. What would really interest me, on your pos, do you have also reciept printer, barcode scanner, pos-display attached? I also have an old dos-box that works extremly well and dumps the inventory file as dbase.
 With regards to memory, same problem here, either the pos software wants all the mem, or the tcp stack (there is a small memory tcp available for about €20 I think). My plan is somehow to connect the dbase file with an sql server, that can then serve to a workstation, or answer enquires from customers using the web-shop.
 Perhaps you could add me to your buddy list, and every once in a while we could exchange experiences etc. What do you think?

Love & Peace to all
anthony

---

