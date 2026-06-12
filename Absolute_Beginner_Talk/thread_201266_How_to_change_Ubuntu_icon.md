---
title: "How to change Ubuntu icon"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by MarkSheely on 2006-06-21
Hi everyone,

I know that if I create an application launcher on a toolbar, I can change the icon for that launcher by right clicking and selecting properties.  But, the Ubuntu icon that launches the menu doesn't seem to work the same way.  Does anyone know how I can change that icon also?  

Thanks,
Mark 
[email]marksheely@gmail.com[/email]

---

### Post by rowanparker on 2006-06-21
I'm not aware you can.

Although wouldn't it be possible to edit the picture file? Not that i know where it is or even if it exists.

Please correct me if i'm wrong?

Rowan.

---

### Post by oscar on 2006-06-21
I found this post which should help you:
[http://ubuntuforums.org/showpost.php?p=381182&postcount=4](http://ubuntuforums.org/showpost.php?p=381182&postcount=4)

---

### Post by rowanparker on 2006-06-21
I stand corrected.

Nice one oscar :D

Rowan.

---

### Post by MarkSheely on 2006-06-21
It doesn't seem to work.  I go to Configuration Editor -> apps -> panel -> default setup ->  objects -> menu bar, and then I check "use custom icon."  Then, I double click on "custom icon" and enter in the following path to the icon where it asks for the Value: "/usr/share/pixmaps/ubuntu.png"  

This should change, the icon, but it does nothing.  I restarted my laptop - no change.  

Not that this is important or anything, I just like to know how to customize everything I can.  

Thanks for all of your help,
Mark

---

### Post by dmizer on 2006-06-21
[QUOTE=rowanparker]I stand corrected.

Nice one oscar :D

Rowan.[/QUOTE]
therein lies the beauty of linux.  even if there doesn't appear to be a way to change something, there's always the ability to look at the source and change it that way provided you have the skill.

Mark,
what path did you enter for your custom icon ... are  you sure you didn't typo?

edit:
wait, you said you entered, "/usr/share/pixmaps/ubuntu.png" ... so your custom icon's name is ubuntu.png, and you're sure it's located in /usr/share/pixmaps?

---

### Post by MarkSheely on 2006-06-22
Hi dmizer,

I double checked, and yes, the icon is named ubuntu.png and it is in /usr/share/pixmaps.  I've toyed around with it a bit more, and still it doesn't change.  I don't understand why not.

Maybe I can try to find the file that has the original icon in it, and replace the icon in that file?  

Thanks again for your help,
Mark
[email]marksheely@gmail.com[/email]

---

### Post by adam.tropics on 2006-06-22
> 
I double checked, and yes, the icon is named ubuntu.png and it is in /usr/share/pixmaps. I've toyed around with it a bit more, and still it doesn't change. I don't understand why not.

I think not. Try /usr/share/icons/hicolor/48x48/apps/distributor-logo.png

---

### Post by Perfex on 2006-06-22
Breezy
[http://doc.gwos.org/index.php/Gnome_Icon](http://doc.gwos.org/index.php/Gnome_Icon)

This worked for me, only problem is you have to kill gnome after, to refresh the bar.

Dapper
[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

I used them both at one time in dapper and I think one changes menu bar, and one changes main menu. if I remember right:confused:

---

### Post by MarkSheely on 2006-06-22
Problem solved - thanks for the help, everyone.  Here's what I did, for anyone who wants to do this in the future:

First, I downloaded the .png icon I wanted to use for the menu icon onto my desktop.  Then, I renamed the icon "distributor-logo.png".  

Next, I opened a terminal, typed "sudo nautilus", entered my password, and navigated to the following folder: 

/usr/share/icons/hicolor/48x48/apps/

Then, I dragged the new icon I want to use from my desktop into the file browser window.  You are asked if you really want to replace the icon that is already in the file; click yes, because of course that's the whole point of doing this.

Close nautilus.

Remove your old menu from the panel, and then add the menu back onto the panel.  Viola!  There's your new icon.  

--Mark

---

### Post by dmizer on 2006-06-24
alternatively, (for future reference) you could have accomplished the same without the danger of having opened nautilus as root. nautilus as root can cause serious damage by an accidental drag or click of the mouse.

just use the mv command like so:
```
sudo mv /where/you/saved/it.png /usr/share/icons/hicolor/48x48/apps/
```
also, just in case you might have wanted to save the old one for later use, you can us the same command.
```
cd /usr/share/icons/hicolor/48x48/apps/
sudo mv distributor-logo.png distributor-logo.old
```
you would of course have to perform the above step before copying in your new logo in order to preserve the ultimate in coolness that is the ubuntu logo ;)

---

### Post by MarkSheely on 2006-06-24
Good advice, thanks!!

--Mark
[email]marksheely@gmail.com[/email]

---

### Post by leeyee on 2006-07-02
[QUOTE=MarkSheely]Problem solved - thanks for the help, everyone.  Here's what I did, for anyone who wants to do this in the future:

First, I downloaded the .png icon I wanted to use for the menu icon onto my desktop.  Then, I renamed the icon "distributor-logo.png".  

Next, I opened a terminal, typed "sudo nautilus", entered my password, and navigated to the following folder: 

/usr/share/icons/hicolor/48x48/apps/

Then, I dragged the new icon I want to use from my desktop into the file browser window.  You are asked if you really want to replace the icon that is already in the file; click yes, because of course that's the whole point of doing this.

Close nautilus.

Remove your old menu from the panel, and then add the menu back onto the panel.  Viola!  There's your new icon.  

--Mark[/QUOTE]
Hi guys!
That's odd, I did it step by step following this, but I could only get the ubuntu logo in the "Add to panel" window changed, after doing this, the ubuntu logo is still in the left of the "Applications".

---

### Post by adam.tropics on 2006-07-02
try entering in a terminal

```
killall gnome-panel
```

That should restart the panel. Failing that, right click and remove the one in the panel, then right click and add to panel the nice shiny new one!

---

### Post by leeyee on 2006-07-03
I'm sorry to tell you that it doesn't work either! That's odd, It has no change even I reboot the X server, anyidea then?

---

### Post by nicjasno on 2006-07-08
I have the same problem. I tried all possible methods i found on the forum, and i still can't change the ubuntu logo with the gnome foot. And i did follow all of the instructions step by step.

---

### Post by wargames on 2006-07-10
> **nicjasno said:**
> I have the same problem. I tried all possible methods i found on the forum, and i still can't change the ubuntu logo with the gnome foot. And i did follow all of the instructions step by step.

Hi, I posted my solution to this problem a few days ago. Maybe it will help you too.

[http://www.ubuntuforums.org/showthread.php?t=208457&highlight=ubuntu+icon](http://www.ubuntuforums.org/showthread.php?t=208457&highlight=ubuntu+icon)

Scroll down to the bottom and try it out. Worked for me.

Let me know how it goes.

---

