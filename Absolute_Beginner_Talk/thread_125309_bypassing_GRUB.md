---
title: "bypassing GRUB"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Rorgy on 2006-02-03
is there a way that i can bypass grub so when it boots up it automatically loads ubuntu....or is there at least a way i can make it look all pretty and stuff?.....if there is a way i can make it look all pretty i would rather do that than get rid of it

---

### Post by Stereotypical Rage on 2006-02-03
usplash, is the graphical boot up process (Similar to a Mac bootup.)

For more on usplash: [https://wiki.ubuntu.com/USplash](https://wiki.ubuntu.com/USplash)
Is this what you mean?

---

### Post by Herman on 2006-02-03
> is there a way that i can bypass grub so when it boots up it automatically loads ubuntu....or is there at least a way i can make it look all pretty and stuff?.....if there is a way i can make it look all pretty i would rather do that than get rid of itWell certianly, you can have a lot of fun with customizing your GRUB bootloader, it's wonderful for that! It is quite safe to experiment with it as long as you make a back-up of your menu.lst before you start, with this: ```
sudo cp /boot/grub/menu.lst/boot/grub/menu.lst_backup
```And if you ever want to restore it to the way it was when you made the back-up you just do:```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```
Okay? Here'a an easy beginner's page about it, to get started with, and you can do quite a lot if you try some things given there. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
And here's an excellent page from the official Ubuntu Wiki on it, [https://wiki.ubuntu.com/GrubHowto](https://wiki.ubuntu.com/GrubHowto) I think you will like the part in the middle of that page titled 'Bootsplash', that looks like a really neat idea, I might go and experiment with that one myself! :-D (Herman)

---

### Post by GTvulse on 2006-02-03
[QUOTE=Rorgy]is there a way that i can bypass grub so when it boots up it automatically loads ubuntu....or is there at least a way i can make it look all pretty and stuff?.....if there is a way i can make it look all pretty i would rather do that than get rid of it[/QUOTE]

On making grub look nice, you want a splash image (it has not nothing to do with usplash, FYI). Read the [GRUB Splash Image Howto]("http://ruslug.rutgers.edu/~mcgrof/grub-images/") for the whole 411. You create an XPM image with the specifications described there, make a gzipped version and copy it as "/boot/grub/splash.xpm.gz", then run "sudo update-grub". You'll see the splash next time you boot up.

---

### Post by Herman on 2006-02-03
Thanks dradul, I had success by following your link. Excellent. :D 
How are you doing, there, Rorgy, need any more help?

---

