---
title: "Dual Installation: Desktop and Server"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by dboyer02 on 2006-10-10
I've always had an interest in Linux. Back in June I downloaded and tried out a live cd version of Ubuntu 6.06 LTS (Dapper Drake) and loved it. My plan was, after removing all my iTunes music to a newer family computer was to turn my older computer, (PII, 256K RAM, 3HDs: 14GB, 80GB, and 24 GB all now formatted in EXT3) that was a Windows XP box, into a linux box. My desires were incresaingly fueled, after moving a company website to a PHP/MySQL server, to learn even more and, after picking up a PHP/MySQL book at Barnes & Nobles last weekend, I desired to install a LAMP server on this box also (the intent of the server, at least at first, is to learn PHP and MySQL locally without exposing it to the internet. 

So, as you can see I'm a newbie with great aspirations. As of right now I have a perfectlky operating and updated version of Ubuntu 6.06 operating on this computer and have the Ubuntu Server 6.06 burned to CD. 

After reading about both the desktop and server versions, I'm still confused as to whether they are two different programs,the same, or if there's just minor differences between the two.

After my copiuosexplanation, a few short questions:

- Can I/should I install both desktop and server on this computer? (I'm thinking at first that I'd like to have a GUI for access to the server) 

- Should I use seperate hard drives? 

- Will this be a dual-boot situation or simply a matter of turning the server on and off. 

Thanks so much for any assistance you can provide.

Looking forward to many years of Ubuntu use!

---

### Post by Minyaliel on 2006-10-10
I honestly don't see why you'd want to dual- boot like that... but alright, that's not a decision I need to make. I've earlier installed both the server version and the desktop version of Ubuntu (not both at the same time, though). As you probably know, the server version is just the core system, with no GUI or anything, you will have to do everything by means of command- line. The desktop has a GUI and lots of fancy apps that you won't find on a server install. Now, if you want to use your computer as a server that'd mean you'd have to let the Ubuntu server run all the time, because if you switch to desktop (which would have to be on a different partition altogether) you'd shut down the server and it'd go offline. It'd be a totally normal dual- boot. I don't know about separate hard drives, so that's something someone else will have to answer. I guess you could boot into the server partition from the desktop partition, but honestly, I don't see why you'd want to bother.

---

### Post by dboyer02 on 2006-10-10
> I honestly don't see why you'd want to dual- boot like that...
Maybe I should not have used the term dual-boot. My desire would be to use them independently, exclusively of one another, either the desktop OR the server, but not both at the same time, unless that was somehow mandated by an installation.

---

### Post by Minyaliel on 2006-10-10
Well, if you only want to use it to learn PHP/ MySQL, I'd say install the desktop version and Apache, because until this day I have not found a way to install a GUI to the server version so that you can see what you're actually doing :P

---

### Post by dboyer02 on 2006-10-10
>  because until this day I have not found a way to install a GUI to the server version so that you can see what you're actually doing 
As a newbie I certainly can't vouche for this info, but it was written for newbies- and has a suggestion for a server GUIs: (and I've seen others I believe)
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

### Post by taurus on 2006-10-10
If you want to install Gnome, KDE, or XFce4, then run

```

sudo aptitude update
sudo aptitude install ubuntu-desktop <-- for Gnome
sudo aptitude install kubuntu-desktop <-- for KDE
sudo aptitude install xubuntu-desktop <-- for XFce4

```

---

### Post by dboyer02 on 2006-10-10
> If you want to install Gnome, KDE, or XFce4, then runSorry, but I am a newbie- what does this do? Install a GUI to the server version?

---

### Post by Medieval_Creations on 2006-10-10
If you're just interested in learning PHP & MySql you should only need to install desktop version... you can do any testing and development there and then move it to a server (if you have one)... that's what I do.

Given the specs of the PC you plan on using I would suggest running xubuntu, since it's less demanding on resources...

there are only a few packages that you would need to install to get LAMP going...

```
sudo apt-get install mysql-server apache2 php5
```

and you should be good to go from there...

---

### Post by dboyer02 on 2006-10-10
> If you're just interested in learning PHP & MySql you should only need to install desktop version... you can do any testing and development there and then move it to a server (if you have one)... that's what I do.Super!

> Given the specs of the PC you plan on using I would suggest running xubuntu, since it's less demanding on resources...Great suggestion, if I do decide to use that one, how do I install it? Do I have to uninstall Ubuntu?

> there are only a few packages that you would need to install to get LAMP going...Gosh that's easy! I'm assuming I do the same thing with Ubuntu first to see if my computer will handle it?

---

### Post by Medieval_Creations on 2006-10-10
yea... you can do the apt-get in Ubuntu too... MySql & Apache aren't very resource intesive unless they are on a server getting hits from a number of users...

Running them on your desktop with you being the only real person that hits them your system shouldn't have a problem... the only thing you might notice is that Ubuntu starts up a little slower because it has to start the MySql & Apache daemon...

If you already have Ubuntu installed, no need to reinstall unless you're really not happy with your PCs performance... If everything runs and you have no problems stick with Ubuntu...

---

### Post by Minyaliel on 2006-10-10
No need to uninstall anything, type sudo apt-get install xubuntu-desktop in your terminal if you've got Ubuntu already installed.

---

