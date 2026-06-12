---
title: "Change Resolution"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by samith on 2007-06-25
guys good morning...  i need a knw, how can i change my resolution in to 1024x768.. i can only get 800x600" "640x480".. please help...

;);););)

---

### Post by isaacj87 on 2007-06-25
What type of video card or chipset do you have?

---

### Post by cogadh on 2007-06-25
You may just have your xorg.conf file configured incorrectly. Post the Device, Monitor and Screen sections from the xorg.conf file so we can review it. the file is found in the /etc/X11 directory.

---

### Post by proplaya23 on 2007-06-25
Hi there i need help with the same problem..... i am Trying to boot Ubuntu and it just gives me a Blank screen I think i have to change my resolution....as i had to do it from the live CD by pressing the "VGA F4" button to boot up properly.

Im a Total Linux NumNUB.... So please if i said something completely Stupid Forgive ME :)

---

### Post by cogadh on 2007-06-25
> **proplaya23 said:**
> Hi there i need help with the same problem..... i am Trying to boot Ubuntu and it just gives me a Blank screen I think i have to change my resolution....as i had to do it from the live CD by pressing the "VGA F4" button to boot up properly.

Im a Total Linux NumNUB.... So please if i said something completely Stupid Forgive ME :)
Search the forums for this problem, if you don't find any similar issue (believe me, you will), then create a new thread for it. The blank screen issue is not a resolution problem.

---

### Post by proplaya23 on 2007-06-25
Thx

---

### Post by samith on 2007-06-25
> **cogadh said:**
> You may just have your xorg.conf file configured incorrectly. Post the Device, Monitor and Screen sections from the xorg.conf file so we can review it. the file is found in the /etc/X11 directory.

Device : 

Identifier "Videocard0"
Driver "sis"
VendorName "Videocard vendor"
BoardName "Silicon Integrated System {sis} 300/305 PCI/AGP VGA Display Adapter"

Monitor :

Identifier "Monitor0"
VendorName "Monitor  vendor"
ModleName "Hp5500"
displaysize 280 210

Horizsync 30.0 - 54.0
vertrefresh 50.0 - 120.0
Option "dpms"


Screen 

Identifier "Screen0"
Device 'videocard0"
Monitor "monitor0"
DefaultDepth 24
SubSection "Display"
viewport 0 0
Depth 16
modes 800x600  640x480

subsection "Display"Viewport 0 0
Depth 24
modes 800x600  640x480

---

### Post by Gigzaholic on 2007-06-26
> **samith said:**
> Device : 

Identifier "Videocard0"
Driver "sis"
VendorName "Videocard vendor"
BoardName "Silicon Integrated System {sis} 300/305 PCI/AGP VGA Display Adapter"

Monitor :

Identifier "Monitor0"
VendorName "Monitor  vendor"
ModleName "Hp5500"
displaysize 280 210

Horizsync 30.0 - 54.0
vertrefresh 50.0 - 120.0
Option "dpms"


Screen 

Identifier "Screen0"
Device 'videocard0"
Monitor "monitor0"
DefaultDepth 24
SubSection "Display"
viewport 0 0
Depth 16
modes [COLOR="Red"]1024x768[/COLOR] 800x600  640x480

subsection "Display"Viewport 0 0
Depth 24
modes [COLOR="Red"]1024x768[/COLOR] 800x600  640x480

Just add what I put in red to your xorg file.

Oh and before you do that, create a backup of your xorg file by doing this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

In case something goes wrong and you have to restore your xorg file, do this:

```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by cogadh on 2007-06-26
Changing the xorg.conf file as Gigxaholic describes should work, but considering you are using a 15 inch monitor and a 8 year old video card, you might be better off keeping that 800x600 resolution. Both the card and monitor max out at 1024x768, which means it is not necessarily the best resolution to use. Also, are you trying to use Ubuntu on this PC or are you using Xubuntu, which is much more friendly to low-end PCs?

---

### Post by samith on 2007-06-26
> **Gigzaholic said:**
> Just add what I put in red to your xorg file.

Oh and before you do that, create a backup of your xorg file by doing this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

In case something goes wrong and you have to restore your xorg file, do this:

```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```


heyyyy Thanx guys.... its worked....  Thanx Gigzaholic... i nevr knew how much fun this was untill now...

Thanx bro..:D:D:D:D:D:D

---

