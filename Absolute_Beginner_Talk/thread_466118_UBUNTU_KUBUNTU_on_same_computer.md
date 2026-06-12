---
title: "UBUNTU KUBUNTU on same computer"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by psanu on 2007-06-06
Hi,

I am relatively new to linux and i have successfully installed Feisty on my Intel Core 2 Duo Laptop. Now i wanted to try Kubuntu too. I tried to create a new partition on my harddisk and tried to doa manual format and repartition. I got an error . Don't remember the exact text but it was some thing like new removable disk discovered !!! Repartition is terminated. After that i cancelled the installation .

After that My machine won't boot. The error was GRUB Error 15. Which i now understand is for Menu.lst file missing. I reinstalled and everything is fine now.
Just wondering did any body got something like this before?

Can't i run Both Ubuntu and Kubuntu Together?

Thanks

---

### Post by Zzl1xndd on 2007-06-06
Yep you can just do into synaptic, Search for the KDE desktop and Install it, then on your sign in screen just pick KDE, or Gnome no need to install another copy.

---

### Post by Outrunner on 2007-06-06
You really don't need to do a dual-boot. Just install the kubuntu metapackage

```
sudo aptitude install kubuntu-desktop
```

and you can type

```
sudo aptitude remove kubuntu-desktop
```

if you want to get rid of it.

---

### Post by pbw on 2007-06-06
Sure you can, but no need for a dual boot. ubuntu and kubuntu are basically just packages from the same distribution. If you've installed ubuntu then enter in temrinal sudo apt-get install kubuntu-desktop. And vise versa if you're running kubuntu. you'll have a choice at login on which desktop to run (gnome or kde)

edit: i'm slow lol, but there you go. Not bad at all, 3 answers telling you the same thing within a minute of you posting.

---

### Post by carlosfocker on 2007-06-06
Their shouldn't be a problem dual booting the two OS's.  Not sure what exactly happened on you install but you might want to install Ubuntu on a partition that doesn't use the full drive(maybe half).  Then allow KUBUNTU to create a partition on the remaining space.

The above suggestions are better tho.

---

### Post by psanu on 2007-06-07
Thans a lot to all of you for replies. 

Since i just want the look and feel of KDE i think i will install only the desktop.That should serve my purpose.

Thanks 

Psanu

---

### Post by CheeseEatingBulldog on 2007-06-07
I think you are missing the point by saying 'I will just install the desktop to get a look and feel'. You see ubuntu is the base engine which can fit either, ubuntu, kubuntu or xubuntu. You can install all three and switch between them by logging out and selecting a different setting. They are each to their own the whole version, just using a common base system and simply using different window environments. You can even run kubuntu applications whilst in ubuntu, after installing the kubuntu-dektop package of course.

This way you can grab apps from each *buntu version and simply chose your favourite one to work in.

---

### Post by psanu on 2007-06-08
Hi,

Yes i think i got the point. Now that i know i want to use ubuntu there is a choice of different window environments. 

Thanka s lot for all your responses.

Psanu

---

### Post by dptxp on 2007-06-08
I have installed kde-core.
What extra does a bigger package kubuntu desktop give ?

---

### Post by ubromtoo on 2007-06-10
Just installed Kubuntu-Desktop yesterday , and the items under "system menu"

 don't work at all. I get error messages such as 

    Malformed url
 
 and 

    KDEInit could not launch '/home/richard'.

             So it won't let me access any files such as /home/myname etc !

     After uninstalling and reinstalling it, there has been no change.

    Also, when I try to see what is in the Trash bin, it won't let me look :

            "Malformed URL trash/. "

although it will let me empty the trash.

     Have searched the KDE forum threads, found nothing.

             asking for help :o

---

### Post by ThinkBuntu on 2007-06-10
Kubunu may have some extra frontends, but to get your feet wet with KDE without hogging your diskspace and completely cluttering your apps menu, install just the kde-base metapackage. This will give you a working KD desktop with the minimum in applications, so you can decide if you like it. Just select KDE under Sessions when logging in.

---

### Post by ubromtoo on 2007-06-17
tried making KDM the default desktop, but that did not help the situation.

Have searched the KDE-forum.org threads, no luck there. Posted a request for help there, no

response at all.

    It's been over a week now, and the KDE forum is as silent as this one  :(

 No less a personage than Linus Torvalds has said that KDE is better than Gnome ;

however, it don't work on my desktop.

---

### Post by ubromtoo on 2007-07-16
Regarding my post of June 10th to this thread :   Problem Solved !!!

        Askreiger at Kubuntu Forums . org  suggested that something was damaged

in my  /home/username/.kde  folder ; he said to try simply renaming that  folder

to  /home/username/.kde_bad  and then the system would reconstruct an entirely

new .kde folder , which hopefully would contain no damaged files.

        Did what Askreiger suggested , and it worked like a charm !!

   Many thanks to Askreiger  :):)

---

