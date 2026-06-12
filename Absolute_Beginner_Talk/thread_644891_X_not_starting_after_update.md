---
title: "X not starting after update"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Tteddo on 2007-12-19
Today (12/19/07) I installed all the updates available on one of my machines (which included the Linux headers). Since I am running the beta 169.04 nVidia driver due to the freezing issues, I reran the setup after rebooting after X wouldn't start. After rebooting again, I end up at the console login screen. X still wasn't starting. 
I checked out the Xorg.0.log and I see no errors.
Upon further investigation, if I try to start gdm (/etc/init.d/gdm start) it says fail. But gdm's log isn't being updated as far as I can see.
So my question is what would the next step be?

---

### Post by rickycodie on 2007-12-19
the next step is to try this out

sudo dpkg-reconfigure xserver-xorg

that will recinfigure the xserver and will probably help.

(let me know if the code doesn't run i am useing my memory :)

---

### Post by Hospadar on 2007-12-19
there was a kernel update today, so the drivers need to be re-built (re-installed) before they will work properly.  first you'll need to uninstall them.  I forget if that nvidia installer script provides uninstall functionality, if not, you can use the envy scripts.

This is all going to be from a command line, so get to a text terminal with ctrl-alt-F1 after X fails to start.  And before you do anything, kill your X server with "sudo /etc/init.d/gdm stop"

since you have no gui, you can either - download the envy script from the envy page [here]("http://albertomilone.com/nvidia_scripts1.html"), and put it on a thumb drive or cdr, or you could wget it directly from your machine - ```
wget http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb
```OR, if you're feeling really intrepid, you could use lynx, the command-line web browser ```
sudo apt-get install lynx
lynx
```Anyway you get it, make sure you download the nvidia drivers too unless you still have their install script laying around.  If you are going to use envy to uninstall, find the .deb you downloaded (It'll be in /media/<something> if you used a thumb drive or cdr, or if you used wget or lynx it'll be in whatever folder you ran wget or lynx from) and run ```
dpkg -i <the name of the deb>.deb
envy -t
``` use the "uninstall" and "clean" options to clear out the old drivers (but don't install from here unless you are OK with the nvidia drivers in the ubuntu repositories), then find the nvidia drivers (however you got them) and install them as per nvidia's instructions.

Hope this does it for ya

A couple notes: After you uninstall and clean with envy, I think it will set you back to a stock setup and your graphics should work, you can do ctrl-alt-F7 to get to your graphical shell, and if it's not there, try a "sudo /etc/init.d/gdm restart" to start up your X server, howver, you'll need to go back to the text terminal, and use "sudo/etc/init.d/gdm stop" to kill your X server to install the nvidia drivers.

---

### Post by Tteddo on 2007-12-19
I tried sudo dpkg-reconfigure xserver-xorg with both the nv (which borked all screens?) and nvidia which seemed the same as it was. I have envy installed already due to my previous problems but did not know about console option, that will save time.
I tried envy and got the error that build of the nvidia-new-kernel-source failed.
So now I am doing apt-get install linux-source-2.6.22. It's going to be about an hour. Is this the correct thing to do? I am assuming the kernel update today would not have updated the source.
Or maybe I am way off base....

---

### Post by Tteddo on 2007-12-19
Ok. that didn't work :(
What could I be missing to install the driver with Envy? I still get the the error that build of the nvidia-new-kernel-source failed.

---

### Post by Tteddo on 2007-12-20
I installed linux-source, and the newest envy as you suggested (I had an old one). If I try to install the nvidia driver with envy I still get the error that build of the nvidia-new-kernel-source failed. Looking in the log all I see is that the log started and that's it. If I run the nvidia script to install the 169.04 driver that was working before the update, it appears to install correctly, and there is no error in the Xorg.0.log. But if I do startx I see the nvidia logo, and the grey screen with the cursor, then it bails on me.

---

### Post by Tteddo on 2007-12-20
Well, I got it to work. Hope this helps someone who is in the same boat.
For a summary, my situation is I am using the nVidia 169.04 beta driver as the regular one causes hard lockups with my video card (GeForce 7300 GS). After the update yesterday it wouldn't go into X. So I figured just reinstall the video driver and it should work. Nope. Well it did actually, I finally figured out that gdm wasn't working. 
After wracking my brains and posting here, I found on another forum that maybe I needed to reconfigure gdm. So I ran:
> sudo dpkg-reconfigure gdm
and that failed, saying it couldn't find file libgmodule-2.0.so.0.
Upon further research I found that that is a hard link to the file libgmodule-2.0.so.0.1400.1 which resides in the same directory (/usr/lib). So I copied that file from another machine and made a new link to it. Then reconfigured gdm and it went through. It wouldn't start right then because X wasn't running.
Then I reinstalled the nVidia driver and everything works.

Could someone explain to me exactly how this happens to fix it? Or where that file went to?

---

