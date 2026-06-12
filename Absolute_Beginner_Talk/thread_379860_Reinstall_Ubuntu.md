---
title: "Reinstall Ubuntu?"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by mulkwolf on 2007-03-08
Ok... I think I have no good idea of how to fix the initial install of ubuntu.  worked fine for a week.  I must of tried to install a program that caused problems.  When ubuntu loads all looks fine until it attempts to bring up the login screen.  Cursor appears on a blank screen.

So how can I reinstall the system.  Have a satelite toshiba laptop with hard drive divided between  windows and linux.  
When the live cd is loaded and I choose install it looks like the only option is to delete the entire hard drive.

Any help would be deeply appreciated.  Reallly hope to make this work.  I'm looking to start a computer tutor program for low income youth using linux systems.

Trying hard to figure out this system...  because its the right thing to do.

Thanks

---

### Post by o_fortuna on 2007-03-08
Using the install CD, you should be able to enter manual partitioning. If you can't do it from the installer, open up GParted (should be under System--Administration, but if not, you can still install it with synaptic even in the live CD). Either way, you end up with the same kind of screen. Find your big EXT3 partition -- that's Ubuntu. Right click the partition and delete it. Then right click the newly freed space and tell it to format as EXT3. Press next and make sure that your new partition is marked as /.

Install as normal, and you should boot into a fresh ubuntu system.

By the way, it's a good idea to have backed up super important stuff just in case. I've never heard of something happening; still, there's that 1 in 1,000,000,000,000 (1 trillion -- it's a scientific number ;)) chance that something could happen.

---

### Post by halitech on 2007-03-08
what exactly do you see when it stops?

---

### Post by mulkwolf on 2007-03-09
the load goes through until the login screen should appear.  the cursor spinning dial is present on a completely dark screen.

Im able to get into terminal by ctrl alt... I think it was F3 and enter my login name and password.  So I'm guessing the system is still present but am unable to get the screen to function.


Perhaps a way to find what is not functioning?

Thanks

---

### Post by halitech on 2007-03-09
ok, if  you can get into the terminal then you should be able to get it to start and "shouldn't" need to reinstall. might just need to reconfigure your x-server settings

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by mulkwolf on 2007-03-09
OK I'll just type in the command above... does that reconfigure or is the something else that might have to be done.

thanks so much for this.... everything is a good learning opportunity!

---

### Post by halitech on 2007-03-09
you'll get asked different questions, just try accepting the defaults and see what happens. should then be able to startx and get the gui back

---

### Post by mulkwolf on 2007-03-09
Ok off to try..

thanks

---

### Post by mulkwolf on 2007-03-09
OK  used the defaults and it seemed nothing happened... Do I need to do something to cause it to be applied .  the reconfig displays the prompt after completion.  I'm not real certain if I'm loging out correct.  I simply logout which returns me to the login prompt in terminal, then I'm powering off 

thanks

---

### Post by mulkwolf on 2007-03-09
Last update.... I wound up reinstalling... Thanks for all the support... Look forward to continue learning.

---

### Post by STREETURCHINE on 2007-03-09
hi after many reinstalls i have learnt to backup as soon as it is installed and updated


 to backup in terminal type or copy and paste these commands

   ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

 then to recover the backup when and if you break it
 go into recovery mode and type or copy and paste

   ```
sudo cp /etc/X11/xorg.conf.backup /etc/x11/xorg.conf
```


  then 

  ```
sudo apt-get update
```

then restartx
    ```
startx
```  

and it is all good again

i find this is easier than reinstalling again..

---

