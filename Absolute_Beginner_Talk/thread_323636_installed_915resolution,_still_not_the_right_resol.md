---
title: "installed 915resolution, still not the right resolution"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2006-12-22
hi, I've installed 915 resolution and set the 1280-800 resolution (which I believe is the right one) with the 

sudo gedit /etc/default/915resolution

command. However, nothing changed. I am not even sure mine is a "800 or 900 series Intel graphics chipset". I don't know where to look for this info. I am working on a Acer Aspire 3500.

Can anyone help? THANK YOU VERY MUCH!

---

### Post by mat42187 on 2006-12-24
After installing 915resolution,

    * Run the following to see the available modes: (you might need to add sudo in front of them to give them permission to run)

```
915resolution -l
```

    * Choose a resolution you don't need and replace, for example the following changes 1920x1440 to 1920x1200 

```
915resolution 5c 1920 1200
```

    *Then exit the command line and reset your computer, and then reset your display by pressing Ctl+Alt+Backspace after it reboots.

    * This should add the option for that resolution to the "System>Preferences>Screen Resolution" tool.
    * If it works correctly then you can make the change permanent: 

```
sudo gedit /etc/rc.local
```

    * Simply add the command you typed in above before: 

```
exit 0
```

Most of this is from UbuntuGuide.org, which is an excellent site for most anything Ubuntu.
If this still does not work, then you might not have an Intel card. Check your manual or check the Acer website for your computer. If there are anymore problems, post back and we'll take it from there.

---

### Post by diatribe on 2006-12-24
type at command line:

sudo gedit /etc/X11/xorg.conf

look for the section that looks like this:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection


go to your default depth and add "1280x800"

exit and save and it should work when you restart x

---

### Post by Korrontean on 2006-12-26
Now my desktop looks ABSOLUTELY perfect.

Thank you very much.

(proud) Jon

---

