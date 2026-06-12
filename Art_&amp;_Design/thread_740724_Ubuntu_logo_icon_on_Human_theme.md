---
title: "Ubuntu logo icon on Human theme"
date: 2008-03-31
forum: Art &amp; Design
---

### Post by the yawner on 2008-03-31
I'm not sure if this has been discussed before as I don't really frequent the forums.  Long story short, I don't like the distributor-logo/start-here png icons. 

Dunno bout you guys, but on my 1024x768 desktop, said icons are blurry and casts too much shadow to integrate with the panel. I would have wanted one that looks embossed on the panel regardless of the panel theme but I haven't the time to do this. So what just I did is convert the svg version of the icon to png via GIMP. See below the comparison:

[IMG]http://img.photobucket.com/albums/v90/kiel_008/screenies/ubuntu-logo.png[/IMG]

---

### Post by KingCharles on 2008-03-31
Looks good. I do not know whether you use the [tango style guidelines]("http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines"), but I think it adheres much more to a usable and ergonomics standpoint than the defacto icon. One thing I have always thought about, is the lack of rigorous guidelines regarding design, and implementation over icons, windows, window borders, etc... specially due to the X window server being so inconsistent over the years.

I think you should definately try making the icon being accepted as the default one.

---

### Post by days_of_ruin on 2008-03-31
> **the yawner said:**
> I'm not sure if this has been discussed before as I don't really frequent the forums.  Long story short, I don't like the distributor-logo/start-here png icons. 

Dunno bout you guys, but on my 1024x768 desktop, said icons are blurry and casts too much shadow to integrate with the panel. I would have wanted one that looks embossed on the panel regardless of the panel theme but I haven't the time to do this. So what just I did is convert the svg version of the icon to png via GIMP. See below the comparison:

[IMG]http://img.photobucket.com/albums/v90/kiel_008/screenies/ubuntu-logo.png[/IMG]

Very nice!I don't see why it wouldn't conform to the guidelines its the
same only crisper.

Now how does one change the default one to this?I want to know:guitar:

---

### Post by natehall on 2008-03-31
Mine's blurry too. Its funny so many recommend saving files in svg format. The png is clearly better here.

---

### Post by smartboyathome on 2008-03-31
The PNG is better optimized for this. SVG is good as long as you aren't resizing it to make it too small (like with this).

---

### Post by the yawner on 2008-04-01
Forgot to note that the menu bar screenie on top is what's on a default Ubuntu install (which as of Hardy beta is still the case). The one on bottom is the svg version of the icon that I converted to png and resized to 48x48, 24x24, and 22x22.

@KingCharles
Actually, I've browsed a few reviews of MacOSX versions at ArsTechnica and picked some pointers from there. But I may have read about the Tango guidelines.

> **KingCharles said:**
> 
I was thinking perhaps someone would. LoL.
Anyway, it's just a matter of updating this particular icon. But I'm not sure we could have it ready in Hardy.


[QUOTE=days_of_ruin;4624577]Very nice!I don't see why it wouldn't conform to the guidelines its the
same only crisper.

Now how does one change the default one to this?I want to know:guitar:

It is nice. :)
Comparing the 2 at 48x48:
[IMG]http://img.photobucket.com/albums/v90/kiel_008/ubuntu-logo48.png[/IMG] [IMG]http://img.photobucket.com/albums/v90/kiel_008/start-here48.png[/IMG]

24x24
[IMG]http://img.photobucket.com/albums/v90/kiel_008/start-here24.png[/IMG]

22x22
[IMG]http://img.photobucket.com/albums/v90/kiel_008/start-here22.png[/IMG]

Here are the directories where you'll find the original png icons:
/usr/share/icons/Human/48x48/places
/usr/share/icons/Human/24x24/places
/usr/share/icons/Human/22x22/places

You just need to replace start-here.png with one of the above and it should update all the other icons as they're just symbolic links. I'm not sure about making GNOME recognize these changes immediately. I tried gtk-update-icon-cache but it didn't seem to work. Only after I've rebooted my laptop did the icon update took place.

Cheers. :popcorn:

---

### Post by Crafty Kisses on 2008-04-01
> **the yawner said:**
> I'm not sure if this has been discussed before as I don't really frequent the forums.  Long story short, I don't like the distributor-logo/start-here png icons. 

Dunno bout you guys, but on my 1024x768 desktop, said icons are blurry and casts too much shadow to integrate with the panel. I would have wanted one that looks embossed on the panel regardless of the panel theme but I haven't the time to do this. So what just I did is convert the svg version of the icon to png via GIMP. See below the comparison:

[IMG]http://img.photobucket.com/albums/v90/kiel_008/screenies/ubuntu-logo.png[/IMG]

Looks decent, thanks!

---

### Post by OZFive on 2008-04-02
I was wondering.... how do I go about getting access to the folders to change them over?  I know the folder path... How do I get permision to add the new icons?

---

### Post by the yawner on 2008-04-02
You need to have root access either via terminal or Nautilus. To lessen confusion, just go with the following: Alt+F2 then type gksudo nautilus and enter your password. Just be careful with the files you'll change.

---

### Post by OZFive on 2008-04-03
I did what you said and I was able to add the new icons which after the instructiuons was very easy.  I have restarted the computer a few times since then and the icon will not change?  Any ideas?

---

### Post by anubis3000bc on 2008-04-24
Same here i replaced all the icons and only one icon changed and that is the about ubuntu icon, but the icon in the top left hand corner still didn't change after reboot.

---

### Post by parajuito on 2008-07-28
You need to delete 
icon-theme.cache from /usr/share/icons/Human
then enter this commands in terminal

sudo gtk-update-icon-cache /usr/share/icons/Human/
then:
killall gnome-panel

and then your icon should change

---

