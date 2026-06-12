---
title: "Help with a gtkrc file (desktop), pleeze?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-10
Hi all,

Update: I fixed this, but since it didn't generate much interest (Zero reply!  Yeah!), I won't go into details...if you got here from a search, reply to this post.  I'll likely see it, and help best I can.

--------------------------------------------------------------------------------------------------------

I hope this is the right board; I'm caught between being new to Ubuntu and Desktop fiddling.  Let me apologize in advance to the admin who may or may not move this.

So, yeah, I've got a variant of the Bubble desktop going, and I'm quite pleased with it.  There are a few things I'd like to fix, if it's possible (my hair is gone from pulling, having read through the developer.gnome.org and art.gnome.org documents).  The issues are these:

1. The clock applet runs great, but I can't see the days of the month at hand (please see screenshot).  I should mention too that Evolution won't display those either.

2. When near radio boxes, check boxes, and so on, I can't see the, uh, words next to the box (please see screenshot).

3. Drop-down menus are also blank, until, of course, I mouse over or select the long, black menu.

Something's clearly wrong with the fg and bg I stipulated in the gtkrc file.  Can you tell me what?  I'll love you.  A lot.  All night long.

The Code (thanks to the creators of Smokey-Blue and Bubble!)
```
style "default"{

  fg[NORMAL]                      = "#ffffff"
  fg[ACTIVE]                      = "#000000"
  fg[INSENSITIVE]                 = "#292929"
  fg[PRELIGHT]                    = "#ffffff"
  fg[SELECTED]                    = "#ffffff"

  bg[ACTIVE]                      = "#ffffff"
  bg[NORMAL]                      = "#000000"
  bg[INSENSITIVE]                 = "#292929"
  bg[PRELIGHT]                    = "#000000"
  bg[SELECTED]                    = "#000000"

  base[NORMAL]                    = "#ffffff"
  base[ACTIVE]                    = "#000000"
  base[INSENSITIVE]               = "#292929"
  base[PRELIGHT]          	  = "#ffffff"
  base[SELECTED]          	  = "#000000"
        
  text[NORMAL]            	  = "#000000"
  text[ACTIVE]            	  = "#ffffff"
  text[PRELIGHT]  		  = "#000000"
  text[SELECTED]  		  = "#ffffff"
  text[INSENSITIVE] 		  = "#292929"

}


style "button" = "default"
{
  engine "pixmap" {

    image 
      {
        function        = CHECK
	recolorable     = TRUE
	shadow          = OUT
	overlay_file    = "check1.png"
	overlay_stretch = FALSE
      }
    image 
      {
        function        = CHECK
	recolorable     = TRUE
	shadow          = IN
	overlay_file    = "check2.png"
	overlay_stretch = FALSE
      }

    image 
      {
        function        = OPTION
	recolorable     = TRUE
	shadow          = OUT
	overlay_file    = "option1.png"
	overlay_border  = { 0, 0, 0, 0 }
	overlay_stretch = FALSE
      }
    image 
      {
        function        = OPTION
	recolorable     = TRUE
	shadow          = IN
	overlay_file    = "option2.png"
	overlay_border  = { 0, 0, 0, 0 }
	overlay_stretch = FALSE
      }

    image {
        function        = BOX
	file            = "bubble-grey.png"
	state		= NORMAL
	border          = {10,5,5,10}
	stretch         = TRUE
    }
    image {
        function        = BOX
	file            = "bubble-grey.png"
	state		= INSENSITIVE
	border          = {10,5,5,10}
	stretch         = TRUE
    }
    image {
        function        = BOX
	file            = "bubble-blue-prelight.png"
	state		= PRELIGHT
	border          = {10,5,5,10}
	stretch         = TRUE
    }
    image {
        function        = BOX
	file            = "bubble-blue-pressed.png"
	state		= ACTIVE
	border          = {10,5,5,10}
	stretch         = TRUE
    }
  }
}

style "range" = "default"
{
  GtkRange::slider_width = 14
  GtkRange::stepper_size = 14
  engine "pixmap" {
    image {
	function        = BOX
	file            = "bubble-grey.png"
	detail		= "trough"
	border          = {8,8,8,8}
	stretch         = TRUE
    }
    image {
	function        = BOX
	file            = "bubble-blue.png"
	state		= NORMAL
	border          = {8,8,8,8}
	stretch         = TRUE
    }
    image {
	function	= BOX
	file		= "bubble-grey.png"
	state		= INSENSITIVE
	border		= {8,8,8,8}
	stretch		= TRUE
    }
    image {
	function	= BOX
	file		= "bubble-blue-prelight.png"
	state		= PRELIGHT
	border		= {8,8,8,8}
	stretch		= TRUE
    }
    image {
	function	= BOX
	file		= "bubble-blue-pressed.png"
	state		= ACTIVE
	border		= {8,8,8,8}
	stretch		= TRUE
    }
    image {
	function        = SLIDER
	file            = "bubble-blue.png"
	border          = {2,2,5,5}
	state		= NORMAL
	stretch         = TRUE
	orientation	= VERTICAL
    }

    image {
	function        = SLIDER
	file            = "bubble-blue-prelight.png"
	state		= PRELIGHT
	border          = {2,2,5,5}
	stretch         = TRUE
	orientation	= VERTICAL
    }
    image {
	function        = SLIDER
	file            = "bubble-blue.png"
	border          = {5,5,2,2}
	state		= NORMAL
	stretch         = TRUE

    }
    image {
	function        = SLIDER
	file            = "bubble-blue-prelight.png"
	state		= PRELIGHT
	border          = {5,5,2,2}
	stretch         = TRUE
	orientation	= HORIZONTAL
    }
  }
}


style "notebook" = "default"
{
  engine "pixmap" {
    image {
        function        = EXTENSION
        state           = ACTIVE
        file            = "halfbubble-top-grey1.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = BOTTOM
    }
    image {
        function        = EXTENSION
        state           = ACTIVE
        file            = "halfbubble-bottom-grey.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = TOP
    }
    image {
        function        = EXTENSION
        state           = ACTIVE
        file            = "halfbubble-right-grey.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = RIGHT
    }
    image {
        function        = EXTENSION
        state           = ACTIVE
        file            = "halfbubble-left-grey.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = LEFT
    }
    image {
        function        = EXTENSION
        file            = "halfbubble-top-blue1.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = BOTTOM
    }
    image {
        function        = EXTENSION
        file            = "halfbubble-bottom-blue.png"
        border          = {2,1,1,2}
        stretch         = TRUE
        gap_side        = TOP
    }
    image {
        function        = EXTENSION
        file            = "halfbubble-right-blue.png"
        border          = {3,3,3,3}
        stretch         = TRUE
        gap_side        = RIGHT
    }
    image {
        function        = EXTENSION
        file            = "halfbubble-left-blue.png"
        border          = {3,3,3,3}
        stretch         = TRUE
        gap_side        = LEFT
    }

    image {
        function        = BOX
        file            = "bubble-grey.png"
        border          = {4,3,3,4}
        stretch         = TRUE
        gap_side        = TOP
    }
  }
}

style "menuitem" = "default"
{
  engine "pixmap" {
    image {
        function        = BOX
	file            = "bubble-blue.png"
	border          = {8,8,8,8}
	stretch         = TRUE
    }
  }
}



class "GtkWidget" 	style "default"
class "GtkButton" 	style "button"
class "GtkNotebook" 	style "notebook"
class "GtkMenuItem" 	style "menuitem"
class "GtkRange" 	style "range"

```

Thanks guys!

therunnyman

---

