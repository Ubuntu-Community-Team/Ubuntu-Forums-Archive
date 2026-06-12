---
title: "Gnome windows messed up after Beryl installed"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by reeboblue on 2007-02-08
Hi all,

I recently followed this tutorial to install Beryl+AIGLX on my laptop with Intel GMA 950.  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")

The install went well and I created a separate session for Beryl so that I can use it whenever I want to use it.  The Beryl session seems to work fine after I login.  However, now there is a problem happening when I log in with the Gnome session.  This is hard to explain...but all of the windows that I open in Gnome are now all borderless and they all get "sucked" to the upper-left of the Desktop area.  See screenshot below.  (So I cannot move any windows around and only one window at a time will load (in the upper-left corner).)

[http://i174.photobucket.com/albums/w96/reeboblue/Gnome_Screenshot.png](http://i174.photobucket.com/albums/w96/reeboblue/Gnome_Screenshot.png)

Has anyone had this problem before with Gnome, after installing Beryl+AIGLX?  How did you fix it?  

BTW- I noticed that sometime Beryl doesn't start automatically and I have to click the "Emerald" icon and select Beryl as the window manager instead of Metacity.  Other times, Beryl starts up right away.  Any idea why Beryl would not consistently start up automatically?

Thanks for any help you can provide to these frustrating issues!

Cheers,
-Reebo

---

### Post by Denn1s on 2007-02-08
Im not sure about wath happened to your windows, i think the best way to hav a separate beryl session if thats wath u want may be just to make a new user and add "beryl-manager" to startup. Does running beryl-manager in your gnome session fixes the problem with the windows? Are there any errors in System>Administration>System log? i once found a solution to a problem i had there...

---

### Post by shareMenaPeace on 2007-02-08
Sometimes a reinstall is helpfull aswell (and rather quick.)

[http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl](http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl)

Cheers

---

### Post by nnolan on 2007-02-21
I had the same problem after a failed install of beryl.  All windows opened in the top left of the screen, and had no top bar.  Eventually I had to just create another user, and gnome worked fine there.  I did notice that when I deleted the old "messed up user" /home/username and all, and tried to recreate that user, that the gnome window manager was still funky.  In fact, gnome wouldn't even load for the recreated user.  
I'm still working on what happened because I want my old username back.  It makes a few things with samba on other computers easier.

---

