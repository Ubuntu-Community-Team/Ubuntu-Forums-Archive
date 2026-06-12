---
title: "Transparent Panel (Taskbar)"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-30
OK, after setting up everything correctly in the hardware and software side, I am not going through the most fun part of setting up Ubuntu, the visual eye candy.

I made my top GNOME Panel transparent by right clicking it, selecting Properties, Background and selecting a solid white colour and adjusted the slider to my liking. It worked and looks good.

One problem though, minimized windows are not transparent and are just 'stuck' on top. How can I make these transparent too? There is a screenshot below if you have no idea what I'm on about.

[[IMG]http://img155.imageshack.us/img155/3958/screenshoton9.th.png[/IMG]](http://img155.imageshack.us/img155/3958/screenshoton9.png)

---

### Post by emarkd on 2008-01-30
I don't know, but do you really need them up there anyway?  You've got your AWN or whatever it is at the bottom with the same functionality.  Just a thought...

---

### Post by jan quark on 2008-01-30
I know what you mean
but I am not sure if its possible to set transparency to the minimized applications
without installing additional eye-candy stuff
but I am not fond of upgrading the visual appearance of my linux box
so perhaps someone other knows the answer?

---

### Post by spiderbatdad on 2008-01-30
```
Here&#8217;s how to change Gnome&#8217;s taskbar to be transparent, and then change the font colors of the text. This way you can have a dark background and be able to read the text on the taskbar windows.

Right click taskbar -> Properties -> Background

Choose solid color and then set the style to be transparent. You should see that occur directly.

Now, the next step is to create a text file to store the settings that you need. Perform this step as your normal user in his/her own /home directory.

# vim .gtkrc-2.0

style "panel"
{
fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

Now at the command line reset the Gnome panel.

# killall gnome-panel

This will restart the Gnome panel and you should see the white text in the taskbar when you open a window. There are a bunch of other options above, but I have no idea what they do. Play around with them. The important one is this one which is commented out above.

fg[NORMAL] = "#ffffff"

Obviously #ffffff is white, so if you want another color change it.

You can see what it will look like with a dark background by clicking here. This is my taskbar. Who says you can&#8217;t make a server level OS look good with CentOS 5.1?
2008 01 07 Geek Stuff Comments (0) Permalink

```
Of course make the file executable and restart. You can then fool around with the config file's many settings...change font color, active window taskbar window appearance, etc. Works great. If you dont know how to use vim, look at a quick tutorial. Go into insert mode and paste the code...esc to command mode...:wq to save and quit.

[http://www.maxsworld.org/](http://www.maxsworld.org/)

---

### Post by Crumpets and Jam on 2008-01-30
> **spiderbatdad said:**
> ```
Here’s how to change Gnome’s taskbar to be transparent, and then change the font colors of the text. This way you can have a dark background and be able to read the text on the taskbar windows.

Right click taskbar -> Properties -> Background

Choose solid color and then set the style to be transparent. You should see that occur directly.

Now, the next step is to create a text file to store the settings that you need. Perform this step as your normal user in his/her own /home directory.

# vim .gtkrc-2.0

style "panel"
{
fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

Now at the command line reset the Gnome panel.

# killall gnome-panel

This will restart the Gnome panel and you should see the white text in the taskbar when you open a window. There are a bunch of other options above, but I have no idea what they do. Play around with them. The important one is this one which is commented out above.

fg[NORMAL] = "#ffffff"

Obviously #ffffff is white, so if you want another color change it.

You can see what it will look like with a dark background by clicking here. This is my taskbar. Who says you can’t make a server level OS look good with CentOS 5.1?
2008 01 07 Geek Stuff Comments (0) Permalink

```
Of course make the file executable and restart. You can then fool around with the config file's many settings...change font color, active window taskbar window appearance, etc. Works great. If you dont know how to use vim, look at a quick tutorial. Go into insert mode and paste the code...esc to command mode...:wq to save and quit.

[http://www.maxsworld.org/](http://www.maxsworld.org/)

Hey thanks for that. I'll have to check it out in more detail when I get a little time.

---

### Post by spiderbatdad on 2008-01-31
yeah. It doesn't seem to be possible to give transparency to the active window. You can set bg[active] to a value that matches your panel color, and even give that text its own color. 
IDK if this is controlled by gnome-settings-daemon, or GNOME_WindowListApplet...but changing either would be a huge undertaking...whatever it is, I have found no means of configuring the active window state in the window list selector (taskbar), other than changing it's color. Here's a couple of screenies. You can see I was able to change the font color...even of of the clock (upper right), but it the first screenshot I could only change the color of the active window, and its text. In the second, no window is active, so the selector is totally transparent. Hmmm? NM second shot. That window becomes active as screenshot utility closes...you can see the green racing up the edge!

---

### Post by Miroku on 2008-03-14
> **spiderbatdad said:**
> ```
Here’s how to change Gnome’s taskbar to be transparent, and then change the font colors of the text. This way you can have a dark background and be able to read the text on the taskbar windows.

Right click taskbar -> Properties -> Background

Choose solid color and then set the style to be transparent. You should see that occur directly.

Now, the next step is to create a text file to store the settings that you need. Perform this step as your normal user in his/her own /home directory.

# vim .gtkrc-2.0

style "panel"
{
fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

Now at the command line reset the Gnome panel.

# killall gnome-panel

This will restart the Gnome panel and you should see the white text in the taskbar when you open a window. There are a bunch of other options above, but I have no idea what they do. Play around with them. The important one is this one which is commented out above.

fg[NORMAL] = "#ffffff"

Obviously #ffffff is white, so if you want another color change it.

You can see what it will look like with a dark background by clicking here. This is my taskbar. Who says you can’t make a server level OS look good with CentOS 5.1?
2008 01 07 Geek Stuff Comments (0) Permalink

```
Of course make the file executable and restart. You can then fool around with the config file's many settings...change font color, active window taskbar window appearance, etc. Works great. If you dont know how to use vim, look at a quick tutorial. Go into insert mode and paste the code...esc to command mode...:wq to save and quit.

[http://www.maxsworld.org/](http://www.maxsworld.org/)

thx man. i used gedit instead of vim and it worked. i sooo needed this. awesome. just one question, so if i delete that file that i just made, it would go back to default?
take care.

---

