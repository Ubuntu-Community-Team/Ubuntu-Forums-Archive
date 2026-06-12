---
title: "[SOLVED] &amp;quot;use resolution for default&amp;quot; not applying to screen size of logon screen."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2008-01-21
The logon screen size seems to be stuck at around 1600x1200 (or so) which I don't much care for, mainly because I don't like putting my monitor through the additional resolution adjustments every time I logon.  My desktop is set to 1152x864 and I'd like to apply that to the logon screen as well.  However, I've already ticked the check box in "Screen Resolution" which *says* it will be set as the default setting, but that doesn't appear to be the case.

How can I fix this? :)

---

### Post by xdarkxanarchyx on 2008-01-21
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
and this will allow you to reconfigure Xorg with your old copy backed up.
Or you could just edit it and take out the higher resolutions that you don't want.

---

### Post by toastysquirrel on 2008-01-21
> **xdarkxanarchyx said:**
> ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
and this will allow you to reconfigure Xorg with your old copy backed up.
Or you could just edit it and take out the higher resolutions that you don't want.

What does this command do?

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by emarkd on 2008-01-21
sudo - switches you to root (administrator)
dpkg-reconfigure - reconfigures an existing package
xserver-xorg - the package that contains the xserver (graphics system)

make sure you run the 'cp' command given.  this will back up your existing configuration in case something goes wrong.

i'll make another suggestion that may be worth trying:  First, do the backup:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then run: sudo gedit /etc/X11/xorg.conf

When your editor pops up, look through it and remove any mention of the 1600x1200 resolution.  This will essentially remove the information that xorg needs to draw a 1600x1200 screen.  Save the file, logout and then at the login screen press <ctrl><alt><backspace>.  This will restart the xserver using the edited file.

---

### Post by spiderbatdad on 2008-01-21
can you set that resolution in /etc/usplash.conf?

---

### Post by cdtech on 2008-01-21
Just change your x and y res to what you want. I just set mine to match my screen res, it was set to 1920x1440, I just set it to 1440x900.

---

### Post by sirgogo on 2008-01-21
> **xdarkxanarchyx said:**
> ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
and this will allow you to reconfigure Xorg with your old copy backed up.
Or you could just edit it and take out the higher resolutions that you don't want.

That would be painful!!!

There is a easy way to do this.

**Step 1: Open up a terminal Window**
This is by far the easiest way to do it, because you don't have to log out or change any other settings.

**Step 2: Edit xorg file as root**
```
sudo nano /etc/X11/xorg.conf
```
sudo allows you to have "root" access.

**Step 3: Editing the Screen section**
Now, you are going to want to scroll down and find the section that looks something like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
               [COLOR="Red"] Virtual 1680    1050[/COLOR]
                [COLOR="Blue"]Modes            "1680x1050@60[/COLOR]"  "800x600@75"   "800x600@60"  
        EndSubSection
        Option          "AddARGBGLXVisuals"     "True"
EndSection

```

First, please make sure that your monitor can handle the settings you add in.

The code labeled in [COLOR="Blue"]blue[/COLOR] is what will affect your resolution once you log in. The first entry in that row is the default.

The code labeled in [COLOR="Red"]red[/COLOR] is what will affect your login screen. Just set it to whatever you want. Remember for all resolutions, width then height.

**Step 4: Saving and Resetting**
Just hit "Control+X" and when it prompts, type "Y", and "Enter" to completely save this file.

Now you just have to restart the X. You have two options, its really your choice and doesn't make a difference.

"Control+Alt+Backspace"

OR, type in the terminal:
```
sudo /etc/init.d/gdm restart
```

**Step 5: Check and Enjoy!**

Once the X is successfully restarted, you should probably check the setting by going to System-->Administration-->Screen and Graphics, and make sure that all your old settings are the same. Sometimes, *just sometimes* by editing your xorg file, you might have screwed something up. So, just be careful what you type when your editing that file (Step 3).

Hope it works, it did for me.
Let me know how it goes!

---

### Post by xdarkxanarchyx on 2008-01-21
> **sirgogo said:**
> That would be painful!!!

There is a easy way to do this.....

You're a bit more professional than me. You're making me look bad! lol In the future I'll try to explain things more completely like you. :)

---

### Post by skip579 on 2008-01-21
Do those steps listed above apply to 7.04?  The resolutions show up as "1024x768", w/out the "@75" ending.

Btw I just tried this and now my resolution is 1024x768, whereas it was 1280x720 before.  I'm shooting for 1680x1050.

---

### Post by xdarkxanarchyx on 2008-01-21
It shouldn't matter what release or distro you're using. Unless it's really old maybe.... You're just editing Xorg.
What driver are you using? Video card?
Open up the terminal.
 ```
 cat /etc/X11/xorg.conf 
``` This will show you your Xorg.conf file and display all the information.
```
 lspci 
``` will show you what you have plugged in to the PCI slots.

---

### Post by otherush on 2008-01-21
Check out this link for a solution that helped me:  [http://ubuntuforums.org/showpost.php?p=3667699&postcount=20]("http://ubuntuforums.org/showpost.php?p=3667699&postcount=20")

---

### Post by smilingfrog on 2008-01-22
I am having a similar problem.
I had resolution problems when logged in- these have been fixed now.

However, I am still having problems with the login screen. The resolution is fine, it just leaves a black margin of about 10% of the screen on the left side. When I login, this disappears, and the window fills the screen.

Nothing suggested in this thread or previous ones has worked.

I have edited /etc/X11/xorg.conf under the monitor section to include PreferedModes statements, HorizSync and VertRefresh    statements. Neither have changed the output.

sudo dpkg-reconfigure -phigh xserver-xorg replaces the xorg.conf file, but still no change in the login page.

Worst, this was not a problem in Feisty, and it's driving me crazy because I can figure it out.  Any offers of help are appreciated.

G

---

