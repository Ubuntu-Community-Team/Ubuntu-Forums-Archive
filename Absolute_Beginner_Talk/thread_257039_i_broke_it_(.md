---
title: "i broke it :("
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Huzudra on 2006-09-13
so i was following the steps here....
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
and after sudo nvidia-glx-config enable it said something about updating the md5 and so i did what was suggested by the terminal,i rebooted it, and now i have a nice blue screen saying failed to start x server.

ugh, after all that typing and work to install just a graphic driver and now its broke!  i want to go back to win2k, atleast with that i could just click away my problems or goto a last known good config and boot or something like that.

---

### Post by Ghozt on 2006-09-14
I know booting into recovery mode, then typing dpkg-reconfigure xserver-xorg should do it, but I'm not sure which one you should select. Try the default suggestion, and hit enter when you don't know the answer to something.

---

### Post by CatKiller on 2006-09-14
FWIW, if you need to run some commands, but you've broken your X server - as you seem to, and as I did the other day, you can press **Ctrl-Alt-F2** to get to a virtual terminal that will let you run commands. **Ctrl-Alt-F7** should be your broken X session, should you wish to go back to it. And when you've reconfigured X so that it isn't broken, **sudo shutdown -r now** should restart your computer for you. **Ctrl-Alt-Backslash** will kill (and hopefully restart) your X session, but I don't know for sure that it will work to restart it after you've reconfigured a broken one, so it's probably best to restart the computer instead.

HTH.

Oh, and the nvidia-glx-config command probably made a backup of your xorg.conf file before it made any changes. I don't know what it would be, since I've made many changes to my X configuration - possibly xorg.conf~ or xorg.conf.backup. So to get your X configuration back the way it was, it might be as simple as (assuming it was xorg.conf.backup) **sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf**. Once you've got to the first /etc/X11/xorg part, you can press Tab twice to get a list of the files whose names start with "xorg" in the /etc/X11/ directory to help you identify what the name of the backup file is.

---

### Post by Huzudra on 2006-09-14
thanks, i'll try some of what i can understand after work today.  then i just need to get the SX4000 working.

---

### Post by xpod on 2006-09-14
>  i want to go back to win2k, atleast with that i could just click away my problems or goto a last known good config and boot or something like that.
Reply With Quote

At least give it a few more posts and trys and reposts and some more trys and if need be............some more posts and some more trys.

And IF you still cant handle the fun and games after you`ve done all that...
Well mabey "clicky clicky" is the best place because your going to have plenty more days when things go wrong.....Or are MADE to go wrong:D 

Thats all part of the fun and it`s the best way to learn.....first you must "break it" to then suss how to"make it"..

GOOD LUCK!!!!..Hope you suss it out

---

### Post by Dinerty on 2006-09-14
> **Huzudra said:**
> so i was following the steps here....
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
and after sudo nvidia-glx-config enable it said something about updating the md5 and so i did what was suggested by the terminal,i rebooted it, and now i have a nice blue screen saying failed to start x server.

ugh, after all that typing and work to install just a graphic driver and now its broke!  i want to go back to win2k, atleast with that i could just click away my problems or goto a last known good config and boot or something like that.

Hey mate check the link in my sig for installing the nvidia driver, I used it many times myself for installing my graphics drivers

---

### Post by Huzudra on 2006-09-14
well the thing with win2k was that it was stupid easy and quick to work with, the pc is just to serve music, movies, and files to the other PC which is chock full of drives and doesnt have the physical room for more storage.

---

### Post by Huzudra on 2006-09-17
alright, i got xubuntu installed...

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
im doing that to install the video driver, method 1 step 6 wont work, i get 
sudo: gedit: command not found.
how do i fix this?  i'd like the correct video drivers so more of the rendering can be handed off to the GPU rather than taxing the CPU.


nevermind, i got it. i had to apt-get install gedit.  driver works fine,  marked difference in performance just moving around and even when veiwing/scrolling a webpage.

---

