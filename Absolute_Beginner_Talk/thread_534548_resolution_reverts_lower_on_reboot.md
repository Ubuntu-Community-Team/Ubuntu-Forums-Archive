---
title: "resolution reverts lower on reboot"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by txeyedoc on 2007-08-25
Have been trying to solve an annoying problem of my monitor's resolution reverting back to 1024x768 every time I boot.  I use the nvidia-settings tool and can change the resolution up manually to 1280x1024 and apply it and it works fine.  I click the "save to X configuration file" on the nividia-settings and all seems well.  However I can't restart the computer or it reverts lower again, and I have to set it up manually.

My card is Nvidia GeForce 7600gs with feisty fawn.  Samsung SyncMaster monitor.

I've run Easyubuntu and Envy.  Also I can't get the desktop 3d effects to run with beryl.

The first time I installed ubuntu I had no problems with this, with all the same hardware components.  Resolution was stable and 3d effects worked.  I had to reinstall ubuntu and this is coming up.  I'm almost considering completely reinstalling ubuntu again, maybe that's the only way to completely clear out all the x-server and nvidia driver info and start fresh?  Any ideas?

---

### Post by krazytekn0 on 2007-08-25
are you running nvidia-settings as root (you get asked for your password)? Or just as a normal user? You can try running the command:

gksu nvidia-settings

and then save it and see what happens. Or you could just open up a terminal and type

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf

and put in "1280X1024" in all the relevant sections if you are comfortable editing your xorg file. **(NOTE: When editing system files ALWAYS save the original as blah.blah.old BEFORE making any changes! this is what the first line does.)**

---

### Post by txeyedoc on 2007-08-25
Thanks krazytekn0, that worked!  I did the first thing you suggested, running gksu nvidia-settings.  Only difference was it asked me for a password.  Then I saved and it boots into the proper resolution now.  

That simple remedy solved and ended weeks of frustration.  If you're ever in Texas, come by for a free eye exam! ha!

---

