---
title: "[SOLVED] Not able to change wallpaper"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by spai on 2007-12-07
Hello everyone,
If I try to change the wallpaper of my GNOME desktop(I just installed gutsy and am almost new to linux), it does not change, but keeps the old wallpaper. While trying different tricks to change wallpaper,sometime I had got a message saying ´[some path]´ is actually a read-only file. 

Please help...

Also I wanted to know if there is a way to briefly be root while you are logged in as user(to do some tasks) and then remove root status.This way probably i could have changed the wallpaper and is also useful in plenty of occasions.

---

### Post by llamakc on 2007-12-07
The root question is unrelated to your wallpaper issue.

Find and download an image to your Desktop. Try setting that as your Wallpaper.

---

### Post by awthomp on 2007-12-07
Whoops... looks like llamakc and I said the same thing... at the same time.

---

### Post by spai on 2007-12-07
Well I had already tried what you said... but the problem is something else...

I get the following error message if i try to change the wallpaper...
¨The application "Eye of GNOME" attempted to change an aspect of your configuration that your system administrator or operating system vendor does not allow you to change. Some of the settings you have selected may not take effect, or may not be restored next time you use the application.¨

I was experimenting with ¨yelp¨(i think) and somewhere i tried a command that sets configuration files for desktop. Now i am lost and dont know how to reverse it.

P.S:It could not be related to the root question. So please treat that as a separate question :)

---

### Post by awthomp on 2007-12-07
Are you trying to change your wallpaper through Eye of Gnome or by right clicking on the desktop and changing the wallpaper from there?

---

### Post by spai on 2007-12-07
Tried both.... both dont work
If i simply right click and try to change it does not change...
So i was trying other methods.

---

### Post by awthomp on 2007-12-07
The only thing I can think of other than what I've suggested is to make sure the extension of the picture is right.

If that doesn't work, someone else may want to pick this thread up!

---

### Post by spai on 2007-12-07
What are the supported extensions?
I thought .png, .jpeg should work.If these are not supported what is??

---

### Post by spai on 2007-12-07
In fact I was reading yelp and tried the ¨setting look and feel¨ preferences using **gconf**
I tried this
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string \
  --set /desktop/gnome/background/picture_filename filename.png
```
Is this not allowing me to right-click and change the wallpaper??

---

### Post by Ptero-4 on 2007-12-08
You can try perhaps checking if pessulus (the gnome lockdown stuff) is active. Maybe you or someone else in your family activated it and now don't remember it.

---

### Post by nikoPSK on 2007-12-08
have you maybe told nautilus to stop drawing the desktop somehow?

---

### Post by spai on 2007-12-08
> **Ptero-4 said:**
> You can try perhaps checking if pessulus (the gnome lockdown stuff) is active. Maybe you or someone else in your family activated it and now don't remember it.

If i type pessulus in terminal,it says pessulus is not active(and asks me if i want to install it).

[QUOTE=nikoPSK]have you maybe told nautilus to stop drawing the desktop somehow?[/QUOTE]
Well I  have tried everything in ¨Appearance¨ tab, right click setting and so on, nothing works. Probably without realising i could have asked nautilus to do so... but I am not sure how. I have never explicitly set any nautilus settings. 


Anyway,
I am almost sure it has got to do with this code I was experimenting with
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults \
  --type string \
  --set /desktop/gnome/background/picture_filename filename.png
```
The above code set my desktop wallpaper.
Does anyone know how I could restore GNOME defaults??
That is probably the only way i can solve my problem :(

---

### Post by spai on 2007-12-08
Does mandatory image setting got to do anything with it??
```
gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.[COLOR="DarkOrange"]mandatory[/COLOR] \
  --type string \
  --set /desktop/gnome/background/picture_filename filename.png
```
Can I reverse the process or get default settings??

---

### Post by spai on 2007-12-08
Bump :(

Here is an update on the error: (It looks more detailed)
```
Can't overwrite existing read-only value: Can't overwrite existing read-only value:
Value for `/desktop/gnome/background/picture_filename' set in a [COLOR="Magenta"]read-only[/COLOR] 
source at the front of your configuration path

```
So guys, does anyone know how to change the readonly setting of the filename??

And by the way resetting GNOME defaults doesnt work!
I tried 
```

gconftool-2 --direct \
  --config-source user-configuration-source \
  --recursive-unset
```
But in vain :(

Please help,
Thanks :)

---

### Post by CatKiller on 2007-12-08
It does look like somehow you've set the "this is the only background allowed on this computer" setting with something that you've fiddled with. I don't really know how any of that works though.

You could maybe have a look at (and check the permissions of) your ~/.gconf/desktop/gnome/background/%gconf.xml.

For information on temporarily becoming root, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spai on 2007-12-08
[QUOTE=CatKiller]You could maybe have a look at (and check the permissions of) your ~/.gconf/desktop/gnome/background/%gconf.xml.[/QUOTE]

I have read and write permissions for %gconf.xml file. Yet it does not listen to me :(
I am curious to know why I cant change a setting when I have read write permissions.
Also I tried sudo <gnome-command> and that also does not work.


The following is my %gconf.xml file and I cant change the wall paper if I change the ¨picture_filename¨ string.

```
<?xml version="1.0"?>
<gconf>
        <entry name="picture_opacity" mtime="1196741496" type="int" value="100">
        </entry>
        <entry name="draw_background" mtime="1197107793" type="bool" value="true">
        </entry>
        <entry name="primary_color" mtime="1197107793" type="string">
                <stringvalue>#000000</stringvalue>
        </entry>
        <entry name="secondary_color" mtime="1196740200" type="string">
                <stringvalue>#5b2e0f</stringvalue>
        </entry>
        <entry name="picture_filename" mtime="1196741496" type="string">
                <stringvalue>/home/my/Desktop/naruto/bg.jpg</stringvalue>
        </entry>
        <entry name="color_shading_type" mtime="1197138888" type="string">
                <stringvalue>solid</stringvalue>
        </entry>
        <entry name="picture_options" mtime="1197138888" type="string">
                <stringvalue>stretched</stringvalue>
        </entry>
</gconf>
```

---

### Post by CatKiller on 2007-12-08
Well, as a quick-and-dirty method that might not work, you could try ```
mv -r .gconf .gconf.backup
``` and log out and log back in. That will reset **all** your GConf settings back to the defaults.

---

### Post by spai on 2007-12-08
> **CatKiller said:**
> Well, as a quick-and-dirty method that might not work, you could try ```
mv -r .gconf .gconf.backup
``` and log out and log back in. That will reset **all** your GConf settings back to the defaults.

I did what you said.
It reset all except the wallpaper. And I still cant change the wallpaper.](*,)
Probably I am stuck with that wallpaper forever.


Anyway thanks for helping me, **Catkiller** :)
Learnt quite a few things.

---

### Post by CatKiller on 2007-12-08
> **spai said:**
> It reset all except the wallpaper. And I still cant change the wallpaper.](*,)
Probably I am stuck with that wallpaper forever.

:???:

You'll just have to read back over what you've done and look for stuff to set system-wide settings. I know it's possible to force every user to have the same Desktop wallpaper and settings and whatnot - for Internet cafes and corporate settings and the like - but I don't know how it's done because it's not anything that I've wanted to do myself.

Sorry.

Edit: Oh, and if you want your old settings back, switch the .gconf and .gconf.backup around to copy your backup over the new file.

---

### Post by CatKiller on 2007-12-08
I've had a bit of a play, and by running ```
gksudo gconf-editor
``` I get the option to open a "Mandatory Window". Mine doesn't have anything in because there are no mandatory settings on my computer, but perhaps yours now does? You could try deleting any keys that you find in there and see if it helps.

---

### Post by spai on 2007-12-08
Aaahh! Finally that worked \\:D/

Learnt a few things. Now I know how to revert back if I fiddle more :)

Thanks **CatKiller**

---

### Post by CatKiller on 2007-12-08
> **spai said:**
> Now I know how to revert back if I fiddle more :)

Always an essential skill. Glad you've got it sorted.

---

### Post by jadacyrus on 2008-03-05
Im having the same problem only there is nothing in my mandatory window settings.

---

