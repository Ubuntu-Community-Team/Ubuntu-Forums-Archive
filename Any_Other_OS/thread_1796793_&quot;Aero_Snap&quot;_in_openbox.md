---
title: "&quot;Aero Snap&quot; in openbox"
date: 2011-07-04
forum: Any Other OS
---

### Post by Psyco430404 on 2011-07-04
alright, if this is old new's then i'm sorry, but I've just found out how to set something up in open box that's been driving me insane for a while now. I personally enjoy windows "Aero Snap" features for web work, makes it easier to code and view, heres how to do it in openbox.
Steps

1) launch a terminal and place this code in it

```
(text Editor) ~/.config/openbox/rc.xml
```

2) go down to the end of the key bindings section, right before the mouse binds begin. (this is where were going to declare the binds for the "Snap" feature.

3)paste these binds in after the last key bind, but before the </keyboard> tag.

```

    <keybind key="W-Tab">
        <action name="MoveResizeTo">
		<x>0</x>
		<y>0</y>
		<width>640</width>
		<height>970</height>
        </action>
    </keybind>
    <keybind key="C-Tab">
        <action name="MoveResizeTo">
		<x>640</x>
		<y>0</y>
		<width>640</width>
		<height>970</height>
        </action>
    </keybind>

```

4) Change the widths and heights to the dimensions of your monitor, in addition to that, you'll also need to change the X position. This is currently set up for a 1280x1040 resolution display.





Here is a few common resolutions that I've set up for copy and paste.



800x600
```

    <keybind key="W-Tab">
        <action name="MoveResizeTo">
		<x>0</x>
		<y>0</y>
		<width>300</width>
		<height>600</height>
        </action>
    </keybind>
    <keybind key="C-Tab">
        <action name="MoveResizeTo">
		<x>300</x>
		<y>0</y>
		<width>300</width>
		<height>600</height>
        </action>
    </keybind>

```

1024x768
```

    <keybind key="W-Tab">
        <action name="MoveResizeTo">
		<x>0</x>
		<y>0</y>
		<width>512</width>
		<height>768</height>
        </action>
    </keybind>
    <keybind key="C-Tab">
        <action name="MoveResizeTo">
		<x>512</x>
		<y>0</y>
		<width>512</width>
		<height>768</height>
        </action>
    </keybind>

```

1280x720
```

    <keybind key="W-Tab">
        <action name="MoveResizeTo">
		<x>0</x>
		<y>0</y>
		<width>640</width>
		<height>720</height>
        </action>
    </keybind>
    <keybind key="C-Tab">
        <action name="MoveResizeTo">
		<x>640</x>
		<y>0</y>
		<width>640</width>
		<height>720</height>
        </action>
    </keybind>

```

1280x1040
```

    <keybind key="W-Tab">
        <action name="MoveResizeTo">
		<x>0</x>
		<y>0</y>
		<width>640</width>
		<height>970</height>
        </action>
    </keybind>
    <keybind key="C-Tab">
        <action name="MoveResizeTo">
		<x>640</x>
		<y>0</y>
		<width>640</width>
		<height>970</height>
        </action>
    </keybind>

```



*ill post up more resolutions later if people are interested. Its late here and i need some sleep.*

---

### Post by hasufell on 2011-11-03
sadly this won't save the window-size for later "unsnapping"

is it possible to achieve that with openbox?

---

### Post by Exeleration-G on 2012-01-02
I'm interested in remembering the old sizes as well.

---

### Post by kyruz on 2012-01-13
I  have a laptop with 1920x1200 screen resolution and I use "window tiling" in openbox alot.

Programs remember their last size and position....

Ctrl, Windows, Alt+Arrow keys and Alt+Tab is your friend.

```
#  WINDOWTILING

    <!-- Window pseudotiling -->
    <keybind key="W-Left">		# HalfLeftScreen	
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>955</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="W-Right">		# HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>955</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="W-Up">		                # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>1920</width>
        <height>555</height>
      </action>
    </keybind>
    <keybind key="W-Down">		# HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>1920</width>
        <height>555</height>
      </action>
    </keybind>
    <keybind key="C-Left">		# QuartLowerLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Down">		# QuartLowerRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Up">		                # QuartUpperLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Right">		# QuartUpperRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>955</width>
        <height>560s</height>
      </action>
    </keybind>
    <keybind key="A-Right">		# FullScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>1920</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="A-Left">		                 # MiddelScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>1280</width>
        <height>1150</height>
      </action>
    </keybind>
```/y

---

### Post by ohnonot on 2012-06-02
nice one. respect & credits!

---

### Post by ikem.krueger on 2012-08-20
> **kyruz said:**
> I  have a laptop with 1920x1200 screen resolution and I use "window tiling" in openbox alot.

I replaced the size in pixel with the size in percent:

```
    <!-- Keybindings for window tiling -->
    <keybind key="W-Left">        # HalfLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Up">        # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="C-Left">        # QuartLowerLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="C-Right">        # QuartUpperRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="C-Up">        # QuartUpperLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="C-Down">        # QuartLowerRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="A-Right">        # FullScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>100%</width>
        <height>100%</height>
      </action>
    </keybind>
    <keybind key="A-Left">        # MiddleScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
 
```It works very well, but is not 100% accurate right now.

I think I talk with the developers. Maybe they can help me to fix it.

---

### Post by ikem.krueger on 2012-08-20
I made another batch of keybindings for the keypad:

```
    <!-- Keybindings for window tiling with the keypad -->
    <keybind key="W-KP_Left">        # HalfLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-KP_Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>100%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-KP_Up">        # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_End">        # QuartLowerLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_Prior">        # QuartUpperRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_Home">        # QuartUpperLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_Next">        # QuartLowerRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-KP_Begin">        # MiddleScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>

```The keys are as following:

```
<Win>+<1> Left lower corner
<Win>+<4> Left half
<Win>+<7> Left upper corner
<Win>+<8> Upper half
<Win>+<9> Right upper corner
<Win>+<6> Right half
<Win>+<3> Right lower corner
<Win>+<2> Lower half
<Win>+<5> Center
```They are resembling the positions of the window on the screen.

---

### Post by TeamRocket1233c on 2012-08-22
This possible in Fluxbox, GNOME Shell, GNOME 2, MATE, Cinnamon, LXDE, Xfce, or KDE as well?

---

### Post by ikem.krueger on 2012-08-22
> **TeamRocket1233c said:**
> Is this possible in Fluxbox, Gnome Shell, Gnome 2, MATE, Cinnamon, LXDE, Xfce, or KDE as well?

You need to distinguish between a desktop environment and a window manager.

Desktop environments and it's window managers:

[LIST]
[*]None: Fluxbox
[*]LXDE: Openbox
[*]Xfce: Xfwm
[*]Gnome 2: Metacity
[*]MATE: Mate-Window-Manager (a fork of Metacity)
[*]Gnome Shell: Mutter
[*]Cinnamon: Muffin (a fork of Mutter)
[*]KDE: KWin
[/LIST]
For the desktop environments, either you find out where the window manager configuration files are and how to modify them.

Or, and the by far easier way, you replace the default window manager with Openbox and use the configuration as described here.

Install Openbox:
```
sudo apt-get install openbox openbox-themes obconf
```Replace default window manager:
```
update-alternatives --config x-window-manager
```

---

### Post by chascon on 2012-09-16
> <Win>+<1> Left lower corner
<Win>+<4> Left half
<Win>+<7> Left upper corner
<Win>+<8> Upper half
<Win>+<9> Right upper corner
<Win>+<6> Right half
<Win>+<3> Right lower corner
<Win>+<2> Lower half
<Win>+<5> Center


Those keys are normally assigned to access work-spaces directly.

---

### Post by chascon on 2012-09-16
On a general note. This isn't "aero snapping". It's called tiling, manual at that.

Suggestion to the original poster: Use percents for your values, and you should get a configuration that'll work on any size screen.

I may eventually publish my own setup if I ever get around to it, but for now you can read more on this at:

[http://urukrama.wordpress.com/2011/10/30/manual-tiling-in-openbox/](http://urukrama.wordpress.com/2011/10/30/manual-tiling-in-openbox/)
[http://ubuntuforums.org/showpost.php?p=10515916&postcount=18](http://ubuntuforums.org/showpost.php?p=10515916&postcount=18)
[http://crunchbanglinux.org/forums/topic/21177/openbox-manual-tiling/](http://crunchbanglinux.org/forums/topic/21177/openbox-manual-tiling/)
[http://crunchbanglinux.org/forums/post/58722/#p58722](http://crunchbanglinux.org/forums/post/58722/#p58722)
[http://urukrama.wordpress.com/2011/10/30/manual-tiling-in-openbox/](http://urukrama.wordpress.com/2011/10/30/manual-tiling-in-openbox/)

---

### Post by llaertis on 2012-11-22
Hello,
it's been quite a while but i'm really interested in what you said about programs remembering their last size and position.
How can you get those variables in order to use them ?

ty

> **kyruz said:**
> I  have a laptop with 1920x1200 screen resolution and I use "window tiling" in openbox alot.

Programs remember their last size and position....

Ctrl, Windows, Alt+Arrow keys and Alt+Tab is your friend.

```
#  WINDOWTILING

    <!-- Window pseudotiling -->
    <keybind key="W-Left">		# HalfLeftScreen	
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>955</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="W-Right">		# HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>955</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="W-Up">		                # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>1920</width>
        <height>555</height>
      </action>
    </keybind>
    <keybind key="W-Down">		# HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>1920</width>
        <height>555</height>
      </action>
    </keybind>
    <keybind key="C-Left">		# QuartLowerLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Down">		# QuartLowerRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Up">		                # QuartUpperLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>955</width>
        <height>560</height>
      </action>
    </keybind>
    <keybind key="C-Right">		# QuartUpperRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>955</width>
        <height>560s</height>
      </action>
    </keybind>
    <keybind key="A-Right">		# FullScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>1920</width>
        <height>1150</height>
      </action>
    </keybind>
    <keybind key="A-Left">		                 # MiddelScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>center</x>
        <y>center</y>
        <width>1280</width>
        <height>1150</height>
      </action>
    </keybind>
```/y

---

### Post by lawl0r on 2013-01-18
There's a tool that brings actual aero snapping to openbox. So that the windows tile if you drag them to the edge of the screen. Check out [opensnap]("https://github.com/lawl/opensnap")
Full disclosure: Shameless advertisment, I wrote it.
[]("https://github.com/lawl/opensnap")

---

