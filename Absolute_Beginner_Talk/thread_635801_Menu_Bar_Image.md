---
title: "Menu Bar Image?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-12-09
Basically I want to change the little icon on the menu bar to something else. I have already downloaded to icons I like, one is gnome and another is a Ubuntu one. They are both .png

I was told to go to alt+F2>gn(something)-Editor>app>panels>objects

then do some other stuff and I did everything to a tee but it did not work and it garbled my whole panel. :confused:

Can someone give detailed instructions on how to do this. All I want to do is change the original Ubuntu looking image next to apps-places and system to a different image I have.


Thanks for the help!

---

### Post by jordanmthomas on 2007-12-09
To do that, you need to find distributor-logo.png for your current icon theme and replace it with the icon you want.

Icons are stored in /usr/share/icons for system-wide installed icons (like Human) and ~/.icons for themes you have installed yourself.

---

### Post by Partyboi2 on 2007-12-09
You will also need to change the name of the icon you want to use to "distributor-logo.png"

---

### Post by GeorgiaBoot on 2007-12-09
Well I went to where you said and the only icon I could find with distributor-logo was under Human.

When I tried to change it it said "do not have permission to change it or parent folder".

next I already have my custom theme not  "Human" but can't find anything in that folder or other folders. Any help is appreciated or other ways to do this.

---

### Post by skrribble on 2007-12-09
your theme should be under /home/yourname/.icons/

take the icon that you want to be by Applications, rename it distributor-logo.png and put it in the /home/yourname/.icons/yourtheme/scalable/places folder and restart your theme by going to the appearance window and changing it to something else then back to your icon theme.

if distributor-logo.png doesn't work, also try naming it start-here.png and putting it in the same place... this worked for me

---

### Post by GeorgiaBoot on 2007-12-09
I went to home>my name> but there was no folder named icons. I have a custom apple theme right now so I thought I should have the icons. I have renamed the icon I have already I just can't find my custom icons!:confused:

---

### Post by skrribble on 2007-12-09
in home/yourname/ there is a hidden folder called .icons .  the period in front of the folder name is very important. hit ctrl+h to see all of the hidden folders.  there will be one called .icons .  in this folder will be your theme and then /scalable/places.... this is where to put distributor-logo.png and/or start-here.png

---

### Post by WinterWeaver on 2007-12-09
Is it not easier to do this via the gnome config editor?

This is where I changed my Icon....

the op mentioned this in the start.

the command is:
Alt+F2
```
gconf-editor
```

---

### Post by skrribble on 2007-12-09
i've not had much success with gconf-editor, but i suppose that is always an option.

i've found it easier to do it this way, and i think that new users would too since it is just copying and pasting and renaming.... that seems easier to me

---

### Post by crimesaucer on 2007-12-09
This is how I did it with my UbuntuStudio icon pack.

Fisrt, I located the start button icons in this folder, it was a .svg image:

/usr/share/icons/UbuntuStudio/scalable/places

Look for the icon called "start-here.svg"

save yourself a copy of it to a different folder. Now while in Root:

put you new "start-here.svg" in that same folder, replacing the old one. Restart. 


(you could also save all of the other "distributor-logo.svg"...and replace them in the same way if you want)

---

### Post by GeorgiaBoot on 2007-12-09
Well I found the hidden files went to where you said found distributor-logo which was an apple and just replaced with the Ubuntu looking one I have but it did not change. I went to themes and changed from one them back to my current them but no go. Any other suggestions?

Also there are some other apple logos in the places folder which have the apple logo but are named
>gnome-main-menu
>start here

---

### Post by crimesaucer on 2007-12-09
> **skrribble said:**
> i've not had much success with gconf-editor, but i suppose that is always an option.

i've found it easier to do it this way, and i think that new users would too since it is just copying and pasting and renaming.... that seems easier to me

Yes, that is the simple way for me. Just make backup copies, and make sure they are the same image type, name, and size....

---

### Post by crimesaucer on 2007-12-09
> **GeorgiaBoot said:**
> Well I found the hidden files went to where you said found distributor-logo which was an apple and just replaced with the Ubuntu looking one I have but it did not change. I went to themes and changed from one them back to my current them but no go. Any other suggestions?

Also there are some other apple logos in the places folder which have the apple logo but are named
>gnome-main-menu
>start here

Like I sad in the above post, you want the start-here.svg


...so you should find a .svg image to replace it with. Check out Gnome-looks.org.

---

### Post by GeorgiaBoot on 2007-12-09
Okay so I changed Start Here and it worked! Now I got the images from gnome-looks but when I applied it and all it was way to small on the menu bar. So I went into gimp and made it larger but when I applied it the applications is farther to the right than normal.


Thanks guys

---

### Post by WinterWeaver on 2007-12-09
> **skrribble said:**
> i've not had much success with gconf-editor, but i suppose that is always an option.

i've found it easier to do it this way, and i think that new users would too since it is just copying and pasting and renaming.... that seems easier to me

Now that I think about it, the method you guys mention here is the better option. Through the editor, you can only change the icon for the current menu-applet you have on the bar at that moment, and if you remove it etc. then you have to make the change again from the start. So in retrospect your method is definitely better.

tbh, I only knew how to do it with the conf editor, but thanks to you guys, I now know of a better method. ^_^

Thanks!

WW

---

### Post by crimesaucer on 2007-12-09
> **GeorgiaBoot said:**
> Okay so I changed Start Here and it worked! Now I got the images from gnome-looks but when I applied it and all it was way to small on the menu bar. So I went into gimp and made it larger but when I applied it the applications is farther to the right than normal.


Thanks guys

Did you make sure that the .svg was the same size image? The start-here.svg should be 48x48 pixels. (in the scalable/place directory).


Inkscape is also a good app to use for Scalable Vector Graphics... (.svg) You can open the .svg image using Inkscape and change the colors of everything. That's what I use to modify icon packs to the colors I like. You can also resize the image among other things.


I did these Black UbuntuStudio icons in Inkscape, I also added them into my default Gnome icons so my Swiftfox 3 prebeta 2 uses them natively in my browser:

Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-5.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-5.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-6.png[/IMG]


Swiftfox 3 Large View: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8.png)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8-3.png[/IMG]

---

