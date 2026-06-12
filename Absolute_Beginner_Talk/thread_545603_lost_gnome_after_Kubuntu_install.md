---
title: "lost gnome after Kubuntu install"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-09-07
I downloaded Kubuntu and lost my Gnome interface.  When I try to boot up in Gnome, I get a blank screen with a white bar at the top and bottom.  I can not boot in fail safe gnome either.  I have no problem using KDE or xsfe4 interface, I only have a problem with Gnome.

Can anyone tell me what to do.  I tried to reinstall Ubuntu from Adept installer but still no good.  

I am running the restricted drivers from the repositories.  The ones that can be turned on in the menu.  Even if I turn those off, I still can not get Gnome to work.



Any suggestions?

---

### Post by rsambuca on 2007-09-07
Try ```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by nynoah on 2007-09-07
tried it.............still a no go.  Any other ideas?

---

### Post by zvacet on 2007-09-07
I don´t know if this will be any help for you,but still

[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by rsambuca on 2007-09-07
What did it say when you tried to run that command?

---

### Post by nynoah on 2007-09-08
It reloaded the ubuntu desktop.  It did not mention anything about broken packages.  It just reloaded it.

Should I do it again and then post the script it gives?

---

### Post by rsambuca on 2007-09-08
Just change your sessions at the login screen back to gnome.

---

### Post by nynoah on 2007-09-08
Its not that easy.  When I restart the computer and go to the log in screen and choose Gnome or Gnome safe mode, it will not work for either.  

When it gets to the Nautalis screen.....it runs through the first 3 icons and then no others load in.  It then goes to a blank screen with a white border both top and bottom where icons should be.  At one time it was a orange in color now it is blue in color.   I am wondering if there is a problem with Nautalis?

Noah

---

### Post by shosta on 2007-10-02
I just got the same problem.
I didn't create another account. I just entered in kde and found all hidden directories in my home directory that were modified since the installation of kde. 
Moved those to a 'new directory' and restarted. 
Gnome entered in my account without problem.
After that I started copying back all moved directories and found that I could move everything back but the things under .gconf/desktop/gnome.
Now it's working fine.!!

Regards
José Miguel

---

