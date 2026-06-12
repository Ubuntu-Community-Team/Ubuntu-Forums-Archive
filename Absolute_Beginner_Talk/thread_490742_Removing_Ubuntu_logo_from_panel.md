---
title: "Removing Ubuntu logo from panel"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-07-02
I would like to remove the Ubuntu logo from the top panel of gnome (left of the Applications button) since it does not match my theme, it is outstanding and the colors don't match. I searched and tried different methods and they didn't work, I restarted X, the computer, and even removed the panel and placed it again. Please help me! [-o<

---

### Post by Seisen on 2007-07-02
Did you right click it and select remove from panel?

---

### Post by amrclutch1 on 2007-07-02
That removes the whole menu, I want to remove just the logo. :)

---

### Post by koshari on 2007-07-02
what you want to do is replace the button with another button .

 Replace the gnome start icon

```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak
sudo cp /your/icon/file.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
killall gnome-panel

```

---

### Post by amrclutch1 on 2007-07-02
How is the little tiny ubuntu logo 48x48?

---

### Post by speaker219 on 2007-07-02
> **amrclutch1 said:**
> How is the little tiny ubuntu logo 48x48?
It....is....
48x48 pixels...

---

### Post by amrclutch1 on 2007-07-02
Ok... i created a 48x48 pixel logo in the gimp and its bigger, but ok... I tried what he said and it didn't work.

This can't be the file

```

/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

```

If it was, when I moved it to a different place, it would show up on the panel, but it remains. Is there a template I can edit and remove the line that calls the image?

---

### Post by LxP on 2007-07-02
To me, the following output suggests that you may have to do a little more research to determine which file you need to replace.  It seems to depend on the current theme and also the height of the panel.

```
/usr/share/icons> find . -name distributor-logo.\*
./gnome/scalable/places/distributor-logo.svg
./gnome/22x22/places/distributor-logo.png
./gnome/16x16/places/distributor-logo.png
./gnome/32x32/places/distributor-logo.png
./gnome/24x24/places/distributor-logo.png
./Tango/scalable/places/distributor-logo.svg
./Human/scalable/places/distributor-logo.svg
./Human/22x22/places/distributor-logo.png
./Human/48x48/places/distributor-logo.png
./Human/24x24/places/distributor-logo.png
./Tangerine/scalable/places/distributor-logo.svg
./Tangerine/22x22/places/distributor-logo.png
./Tangerine/16x16/places/distributor-logo.png
./Tangerine/32x32/places/distributor-logo.png
./Tangerine/24x24/places/distributor-logo.png
./hicolor/48x48/apps/distributor-logo.png
```

---

### Post by testube_babies on 2007-07-02
Yeah, like LxP says, the icon you have to replace is different depending on the theme you are using and the location of that theme.  Use this to locate all of the distributor-logo files across your system:
```
sudo updatedb
locate distributor-logo
```

...And by the way, changing this one little icon can be a real pain.  You'll probably go crazy before you find the right icon to replace.

---

### Post by bodhi.zazen on 2007-07-02
> **testube_babies said:**
> Yeah, like LxP says, the icon you have to replace is different depending on the theme you are using and the location of that theme.  Use this to locate all of the distributor-logo files across your system:
```
sudo updatedb
locate distributor-logo
```

...And by the way, changing this one little icon can be a real pain.  You'll probably go crazy before you find the right icon to replace.

Awwww ....

I was going to post that when I see testtube_babies beat me to the punch ;)

---

### Post by amrclutch1 on 2007-07-02
I assume it won't be anything in the "scalable" folder since I presume it means it fits depending on the size of the parent. I made the panel bigger and it stays the same size, so thanks for the help, and the information on the command, i find the locate command better than the find command. Can you please inform me of what "sudo updatedb" does and also one more question, what the hell is the difference between "su -" and "su"?

;)

Could I possible move all of the distributor-logo.png files with one command to a directory I specify?

---

### Post by amrclutch1 on 2007-07-03
AHHH I AM GOING CRAZY!

```

sudo updatedb
locate *-logo.svg

```

I did that and renamed all of them one by one to .svg.bak.

```

sudo updatedb
locate *-logo.png

```


I did that and renamed all of them one by one to .png.bak

It won't go away!!!!!! I am so frustrated!!!!!!!!! >.<

---

### Post by testube_babies on 2007-07-03
"sudo updatedb" updates the database that the "locate" command searches, so you really don't need to do it very often unless you've installed something recently or moved files around, etc.

Good luck replacing that icon, it can be really annoying.  I got so fed up with it that I started using the Ubuntu System Panel, which lets you choose a custom icon:
[http://ubuntuforums.org/showthread.php?t=365147](http://ubuntuforums.org/showthread.php?t=365147)

---

### Post by chris_c28 on 2008-03-24
Just a heads up in case anyone is wondering.

The distributo-logo.png file you want to change is located under /usr/share/icons/Human/[size]/places
Change in all the relevant sizes, then:
gtk-update-icon-cache /usr/share/icons/Human

This should work.

---

### Post by munkyeetr on 2008-03-24
amrclutch1, what icon theme are you using?

1) **System** -> **Preferences** -> **Appearance**
2) Press the **Customize...** button
3) Click on the **Icons** tab

---

