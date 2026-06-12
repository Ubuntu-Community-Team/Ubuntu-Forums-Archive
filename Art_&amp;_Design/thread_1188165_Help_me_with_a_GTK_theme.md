---
title: "Help me with a GTK theme"
date: 2009-06-15
forum: Art &amp; Design
---

### Post by aschwerin.moses on 2009-06-15
[http://gnome-look.org/content/show.php/F6F6F6?content=101200&PHPSESSID=691cc8368236f68021e44d873dddc0ac](http://gnome-look.org/content/show.php/F6F6F6?content=101200&PHPSESSID=691cc8368236f68021e44d873dddc0ac)

This is one of the themes that I did. Infact I did use the Santay_Origianl gtk theme to make this. I would like to know how to get the "select" item field highlighted with a .png rather than just colour.

The below code is the code for menubar, i somehow cannot get a .png for selected items, please help...

```
#--------------------------------------------------------------------------------------
# MENUBAR
#--------------------------------------------------------------------------------------

	style "menubar-panel" = "default" 
	{
	  fg[NORMAL]   = @tooltip_fg_color
#	  bg[NORMAL]   = @tooltip_bg_color
	  xthickness = 3
	}

	style "menubar"="wide"
	{
		xthickness = 5
		
		fg[NORMAL]	 = shade(0.85, @tooltip_fg_color)
		fg[PRELIGHT] = @tooltip_fg_color
		
		bg[NORMAL]   = @tooltip_fg_color
		bg[SELECTED] = @bg_color
		
		engine "pixmap"
	{
		image
		{
		  function			= BOX
		  state				= NORMAL
		  recolorable		= TRUE
		  file				= "ventana/menubar.png"
		  border			= { 1, 1, 1, 1 }
		  stretch			= TRUE
		}
		image
		{
		  function			= BOX
		  state				= PRELIGHT
		  recolorable		= TRUE
		  file				= "ventana/menubarselect.png"
		  border			= { 1, 1, 1, 1 }
		  stretch			= TRUE
		}
    }
	}
```

---

### Post by aschwerin.moses on 2009-06-15
not even a single person????

---

### Post by Giant Speck on 2009-06-15
If I'm assuming correctly, you're trying to set it so that if you hover over one of the menubar options (such as File or Edit, for example), it will show a picture.  You want a mouseover picture, basically.

I'm not sure what you want can be done.  I've tried to do it, and I've looked at dozens of other pixmap themes, and none of them can do it.

---

### Post by aschwerin.moses on 2009-06-15
yes, you are correct.

I found this theme that uses a picture. Tried to look at the code but did not understand.

[http://www.gnome-look.org/content/show.php/Leopardish?content=65299](http://www.gnome-look.org/content/show.php/Leopardish?content=65299)

---

### Post by aschwerin.moses on 2009-06-17
no ones knows it?????.. come on guys

---

### Post by xl_cheese on 2009-06-17
Look at this for an example.

[http://www.gnome-look.org/content/show.php/White%3F!?content=62968](http://www.gnome-look.org/content/show.php/White%3F!?content=62968)

---

### Post by eamon63 on 2009-06-17
Try this out.
I'm using Global Menu. This method removes annoying background of panel applets.  Also gives highlight to bar items when clicked (activates the menubar( and hovered.  Will not show anything when idle even when hovered.  Also works for Open Office apps. 

you need 3 image files.


############ menubar ################

style "menubar"
{
#font_name = "Lucida Grande 8.5"  #OPTIONAL

    fg[PRELIGHT] = "#ffffff"
    fg[ACTIVE]   = "#ffffff"

  bg_pixmap[NORMAL]  = "Menu-Menubar/menubar2.png"  #BAR BACKGROUND

  xthickness = 4
  ythickness = 0
    engine "pixmap"
    {
        image
        {
            function     = BOX
            recolorable     = TRUE
            state         = NORMAL
            file         = "Menu-Menubar/menubar.png"  #TRANSPARENT IMAGE
            border        = { 0, 0, 1,1}            
            stretch     = TRUE
        }
        image
        {
            function = BOX
            recolorable = TRUE
            state = PRELIGHT
            file = "Menu-Menubar/menubar-item.png"  #YOUR PICTURE IMAGE
            stretch = TRUE
        }
     }
}

class "GtkMenuBar"             style "menubar"
widget_class "*MenuBar.*"         style "menubar"

################################3

Looking at your code, the key i think, is to make your bar background a pixmap image rather than just color....

---

