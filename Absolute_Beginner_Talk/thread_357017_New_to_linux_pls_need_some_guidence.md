---
title: "New to linux pls need some guidence"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by khelu on 2007-02-09
GOt nvidia 7660gt and Lg L194WT 19inch wide screen display monitor, but i just the resolution  up to 1024 where as i need to get 1440 resolution. Please need some help,
thanx a lot in advance

---

### Post by DSn0wMan on 2007-02-09
Are you using the OSS driver, or the nVidia binary driver?

---

### Post by slimdog360 on 2007-02-09
A link to getting the latest beta drivers for your Nvidia card working [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29")

and quick copy and paste (with a couple of mods) from this thread [http://www.ubuntuforums.org/showthread.php?t=356985&page=2]("http://www.ubuntuforums.org/showthread.php?t=356985&page=2") in order to get your monitor at the right resolution. 

write this one down peoples
```
sudo dpkg-reconfigure xserver-xorg
```

open a terminal and copy that into it. Follow the prompts, if you are unsure about something just keep pressing enter. Finally you will get to a bit about your monitor, there should be three options, simple, medium and advanced. Go advanced and here are the specs you want to enter (just as the numbers (and the dash) are written

for the horizontal         30-83
for the vertical              56-76

It will ask you if you want to write the changes to you xorg.conf file, thats a big yes-a-roony right there.

After thats done and finished press ctrl+alt+backspace together.

Before that though here is how to make a backup just incase (so do this first). Again copy this command into a terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
that makes a backup

write this one down for later
```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
you may need this incase you get some big black screen after you press ctrl+alt+backspace. All you will need to do is enter you name and password then type in the above code (the third one) and press ctrl+alt+backspace once again.

---

### Post by khelu on 2007-02-09
> **DSn0wMan said:**
> Are you using the OSS driver, or the nVidia binary driver?

I havent installed any driver from nvidia so i guess im still using the oss driver. If some one could just guide me step by step that will be really helpful thanx.

---

### Post by slimdog360 on 2007-02-09
move you eyes up about three inches.

---

### Post by DSn0wMan on 2007-02-09
At 1024 resolution it's probably more than 3 inches up. lol
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

sudo dpkg-reconfigure xserver-xorg

```

---

