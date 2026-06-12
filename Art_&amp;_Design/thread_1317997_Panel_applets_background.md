---
title: "Panel applets background"
date: 2009-11-07
forum: Art &amp; Design
---

### Post by VCoolio on 2009-11-07
I've made a theme and can't figure out why some panel applets use the menubar .png file as background. How do I stop that? I can rightclick the panel and choose solid color as background, but that doesn't work for the gnome menu and second I want the theme to behave properly. Help appreciated in advance.

What I mean:
[IMG]http://tinyurl.com/ykes6hu[/IMG]

If you want to test yourself instead of guessing for a solution, [here]("http://www.gnome-look.org/content/show.php?content=114013%22") is the theme (replace the gtkrc with the one below, it has changed a lot).

My gtkrc (panel section at bottom):
```
##############################
# Murrina Elegant by VCoolio #
##############################

############
# CREDITS
############
# Mod of Elegant for Rent by rent0n (hardly noticeable anymore, but credits anyway).

###################
# PROLEGOMENA
###################
# for your information: used color codes: 
# blue 		= #659FDB  <-- the bar below menubar, on top of tabs etc
# dark 		= #000000  <-- the menubar, hovering buttons etc
# light blue	= #EDF3FE  <-- tooltips, sidepane


gtk_color_scheme = "fg_color:#000000\nbg_color:#dddddd\nbase_color:#f6f6f6\ntext_color:#000000\nselected_bg_color:#000\nselected_fg_color:#FFFFFF\ntooltip_bg_color:#EDF3FE\ntooltip_fg_color:#000\ntheme_color:#659FDB"

gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-large-toolbar=24,24"
gtk-button-images = 1
gtk-menu-images = 1
gtk-panel-images = 0

###################
# DEFINE DEFAULTS
###################

style "murrine-default"
{
  GtkWidget::interior_focus		= 2 #was 7
  GtkWidget::focus_padding		= 0
  GtkButton::default_border		= { 0, 0, 0, 0 }
  GtkButton::default_outside_border	= { 0, 0, 0, 0 }
  GtkCheckButton::indicator_size	= 12
  GtkCheckButton::indicator_spacing	= 3
  GtkEntry::honors-transparent-bg-hint	= 1 #to prevent gecko from drawing entry bg
#  GtkExpander    ::expander_size  	= 16
  GtkMenu::horizontal-offset		= 5 #space menu <-> submenu
#  GtkMenu::horizontal-padding   = 3	#set space left and right of menuitems
#  GtkMenu::vertical-padding     = 9	#set space on top and bottom of menu
  GtkMenuBar::internal_padding		= 0
  GtkMenuBar::horizontal-offset		= 5 #was 5
  GtkOptionMenu::indicator_size		= { 15, 8 }
  GtkOptionMenu::indicator_spacing	= { 8, 2, 0, 0 }
  GtkPaned::handle_size			= 6 # invisible atm because null.png
  GtkProgressBar::min-horizontal-bar-height = 10 #default 20
  GtkProgressBar::min-vertical-bar-width = 10
  GtkRange::trough_border		= 0 #set width of troughs scrollbars; 0 gives no ugly border
  GtkRange::slider_width		= 15 #overruled below with scale en scrollbar
  GtkRange::stepper_size		= 15 #length of buttons at end of trough
#  GtkRange::trough-side-details	= 1
  GtkVScale::slider_length 		= 13 # sizes of scale handles

  GtkVScale::slider_width 		= 9 # use odd number to center correctly

  GtkHScale::slider_length 		= 13

  GtkHScale::slider_width 		= 9 # use odd number to center correctly
  GtkScale::trough-side-details  	= 1 # 0=nothing; 1=trough filled 'til slider
  GtkScrollbar::min_slider_length	= 20
  GtkScrollbar::slider_width		= 6 #width of scrollbars
  GtkScrollbar::has-forward-stepper 	= 1
  GtkScrollbar::has-backward-stepper 	= 1
  #GtkScrollbar::has-secondary-backward-stepper = 1
  #GtkScrollbar::has-secondary-forward-stepper = 1
  GtkScrolledWindow::scrollbar_spacing	= 0 #set space scrollbar <-> scrolled element
  GtkSpinButton::shadow_type 		= GTK_SHADOW_NONE
  GtkStatusbar::shadow_type		= GTK_SHADOW_NONE
#  GtkToolbar::shadow-type 		= GTK_SHADOW_NONE
#  GtkToolbar::space-size		= 0 #disable separators on toolbar with this
#  GtkTreeView::horizontal-separator = 1
#  GtkTreeView::vertical-separator = 1
  GtkTreeView::odd_row_color 		= @base_color # 
  GtkTreeView::even_row_color 	= @tooltip_bg_color #"#E4EBF5" # sidepanes bg color

  xthickness            	= 2
  ythickness            	= 2

  fg[NORMAL]       	= @fg_color # Metacity and mouseover, Most text
  fg[ACTIVE]       	= @fg_color
  fg[PRELIGHT]     	= @selected_fg_color #changed after button, MK
  fg[SELECTED]     	= @selected_fg_color
  fg[INSENSITIVE]  	= darker (@bg_color)

  bg[NORMAL]       	= @bg_color # Normal Background was e4e4e4
  bg[ACTIVE]       	= @base_color # Mouseclicking, Tabs, active window list
  bg[PRELIGHT]     	= @selected_bg_color # Expand prelight bg
  bg[SELECTED]     	= @selected_bg_color
  bg[INSENSITIVE]  	= @bg_color

  base[NORMAL]     	= @base_color # Background, most was f5
  base[ACTIVE]     	= @selected_bg_color # Menu active item in inactive window was 757575 MK
  base[PRELIGHT]   	= @base_color
  base[INSENSITIVE]	= shade (0.96, @base_color) # Inactive Entry bg
  base[SELECTED]   	= @selected_bg_color # Menu active item in active window was 757575 MK

  text[NORMAL]	  	= @text_color # Text in window, arrows
  text[INSENSITIVE]	= darker (@bg_color) # Insensitive arrows
  text[SELECTED]   	= @selected_fg_color # Active text in active window
  text[ACTIVE]     	= @selected_fg_color # Active text in inactive window
  text[PRELIGHT]   	= @selected_fg_color # Text on Mouseover

  engine "murrine" 
	{
	animation           = FALSE  # FALSE = disabled, TRUE = enabled
	colorize_scrollbar  = TRUE # FALSE = disabled, TRUE = enabled
	contrast            = 1.0   # 0.8 for less contrast, more than 1.0 for more contrast on borders
	glow_shade          = 1.0   # Enable and set the Glow Shade
        glowstyle           = 0	    # 0 = Top glow, 1 = Bottom glow, 2 = Top and Bottom glow, 3 = Horizontal glow, 4 = Centered glow
	glazestyle          = 0     # 0 = flat highlight, 1 = curved highlight, 2 = concave style, 3 = top curved highlight, 4 = beryl highlight
	gradient_shades     = {0.99,0.98,0.90,0.90}
	gradients           = FALSE  # FALSE = disabled, TRUE = enabled
	highlight_shade     = 1.0  # set highlight amount for buttons or widgets #was highlight_ratio
	lightborder_shade   = 1.0   # sets lightborder amount for buttons or widgets #was lightborder_ratio
	lightborderstyle    = 1     # 0 = lightborder on top side, 1 = lightborder on all sides
	listviewheaderstyle = 0     # 0 = flat, 1 = glassy, 2 = raised
	listviewstyle       = 0     # 0 = nothing, 1 = dotted
	menubaritemstyle    = 1     # 0 = menuitem look, 1 = button look
	menubarstyle        = 0     # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped
	menuitemstyle       = 0     # 0 = flat, 1 = glassy, 2 = striped
	menustyle           = 1     # 0 = no vertical menu stripe, 1 = display vertical menu stripe
	progressbarstyle    = 0     # 0 = flat, 1 = glassy, 2 = gardient, 3 = diagonal stripes
	reliefstyle	    = 0     # 0 = flat, 1 = inset, 2 = shadow
	rgba		    = FALSE  # FALSE = disabled, TRUE = enabled
	roundness           = 2     # 0 = squared, 1 = old default, more will increase roundness
	scrollbarstyle      = 0     # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles
	sliderstyle         = 0     # 0 = nothing added, 1 = handles
	stepperstyle        = 0     # 0 = standard, 1 = integrated stepper handles, 2 = unknown
	toolbarstyle	    = 0     # 0 = flat, 1 = glassy, 2 = gradient
	scrollbar_color	    = @theme_color
	profile             = MURRINE # engine profile options: CANDIDO, CLEARLOOKS, MIST, MURRINE, NODOKA
	}
}

class "GtkWidget"          style "murrine-default"

###################
# MENUBAR 
###################


style "menubar"		
{
  fg[NORMAL] 	= @selected_fg_color
  text[NORMAL]	= @selected_fg_color
  fg[PRELIGHT]	= @selected_fg_color #menubar text color when clicked
  fg[INSENSITIVE] = darker (@selected_fg_color) #"grey"
#  bg[PRELIGHT]  = @theme_color #menubar item bg color when clicked

  font_name = "Bold"
  xthickness	= 2
  ythickness	= 4
	engine "pixmap"
	{
		image
		{
			function	= BOX
			state = NORMAL
			file		= "menubar-black.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = ACTIVE
			file		= "menubar-black.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}

		image
		{
			function	= BOX
			state = INSENSITIVE
			file		= "menubar-black.png"
			border	= { 2, 2, 2, 2 }
			stretch	= TRUE
    		}
 	}
}

##################
# MENU 
##################

style "menu"	= "murrine-default"
{
  bg[NORMAL]	= @base_color #menu background 
  bg[SELECTED]	= @theme_color #vert stripe color if menustyle=1

  xthickness 	= 3 #was 2; space between menu border and menu items
  ythickness	= 1
  engine "murrine"
  {
#	contrast	= 1.8
  }
}

##################
# MENU-ITEM
##################
style "menuitem"	= "murrine-default" 
{
  xthickness		= 1
  bg[NORMAL]       	= "#FFF" #separator color
  bg[SELECTED]     	= @selected_bg_color #selected bg
  fg[NORMAL]       	= @selected_bg_color #"#F6F6F6" #arrow color & smplayer menu text
  fg[PRELIGHT]     	= @selected_fg_color #"#262628" #arrow color prelight & smplayer prelight menu text

  engine "murrine"
  {
	contrast = 0.0
  }
}

##################
# MENU SEPARATOR
##################

# This style is there to modify the separator menu items. The goals are:
# 1. Get a specific height.
# 2. The line should go to the edges (ie. no border at the left/right)
style "separator_menu_item" {
  xthickness = 1
  ythickness = 1

  GtkSeparatorMenuItem::horizontal-padding = 0
  GtkWidget::wide-separators = 1
  GtkWidget::separator-width = 1
  GtkWidget::separator-height = 2

  engine "murrine"
  {
    contrast = 1.0
  }
}



##################
# TOOLBAR 
##################

style "toolbar" = "murrine-default"
{
	engine "pixmap"
	{
		image
		{
			function	= BOX
			file		= "null.png"
			border	= { 4, 4, 4, 4}
			stretch	= TRUE
    		}
 	}
}

##################
# Tabs 
##################

style "notebook"		= "murrine-default"
{
  xthickness = 4 # vertical tabs now have thicker border, but otherwise tabs too small
  ythickness = 4 # smaller blue border

  bg[NORMAL]       	= shade (1.08, @bg_color) #active tab
  bg[ACTIVE]       	= darker (@base_color)	# inactive tab
  bg[SELECTED]     	= @theme_color 	# bg behind text on clicked tab
  fg[PRELIGHT]		= @theme_color	# eg. arrows besides tabs in gedit

  engine "clearlooks"
    {
	radius = 1.0 # sets height of blue border
	style = GUMMY #GUMMY = top border; GLOSSY = gradient
    }

#  engine "murrine"
#    {
#	contrast = 1.3 #1.3
#    }
}

####################
# STATUSBAR 
####################

style "statusbar"		= "murrine-default"
{

#	xthickness = 1
#	ythickness = 1
	
	engine "pixmap" 
	{
	    image
	    {
	     	function		= RESIZE_GRIP
		recolorable	= TRUE
#		state		= NORMAL
		detail		= "statusbar"
		overlay_file	= "resize-grip2.png"
		
		overlay_border	= {0,0,0,0 }
		overlay_stretch	= FALSE
	    }
      }
}


#################
# BUTTONS 
#################

style "button" = "murrine-default"
{
   bg[NORMAL]        = lighter (@base_color)
   bg[PRELIGHT]      = @selected_bg_color
   bg[ACTIVE]        = darker (@bg_color)
   bg[INSENSITIVE]   = shade (0.96, @bg_color)

   xthickness   = 2
   ythickness   = 2

   engine "murrine"
	{
	  contrast  = 1.8
	  gradients = TRUE
	  glow_shade          = 1.2   # Enable and set the Glow Shade
          glowstyle           = 4
	  glazestyle          = 3
	}
}

####################
# TOOLBAR BUTTONS 
####################

style "toolbuttons" = "murrine-default"
{
  bg[ACTIVE]		= darker (@bg_color)
  GtkWidget::focus_padding = 1
}


####################
# CHECK / RADIOBUTTONS
####################

style "checkradiobutton" = "murrine-default"
{
	bg[SELECTED]	= @theme_color 	#color fill inside squares / circles, not the dots / checks
	text[NORMAL]	= @theme_color	#color of dots / checks
	text[PRELIGHT]	= @theme_color	#color of dots / checks
	bg[NORMAL]	= shade (0.96, @bg_color)	#color fill inside when disabled
	bg[PRELIGHT]	= @theme_color	#bg on text prelight
	text[ACTIVE]	= @theme_color	#color of checks when clicked
#	base[NORMAL]	= "red"	#color fill inside when unselected
	
	engine "murrine"
	{
	  contrast = 1.2
	}
}

####################
# CHECK / RADIOBUTTONS IN MENUS
####################

style "menucheckbutton"	= "murrine-default"
	{
	bg[SELECTED]	= @theme_color	#color fill inside + bg behind text prelight
	bg[NORMAL]	= shade (0.96, @bg_color)	#color fill inside when disabled
	text[NORMAL]	= @theme_color	#color of dots / checks
	text[PRELIGHT]	= @theme_color	#color of dots / checks prelight
	text[ACTIVE]	= @theme_color	#color of checks when clicked
#	base[NORMAL]	= "green"	#color fill when unchecked
	}

################
# SPINBUTTONS 
################

style "spinbutton"	= "murrine-default"
{
  bg[SELECTED]	= @theme_color	#border around text when clicked inside entry, requires minimal x3 and y2 thickness
  fg[PRELIGHT]  = @theme_color	#arrow prelight

  xthickness	= 3
  ythickness	= 2
  GtkWidget::interior_focus	= 0

  engine "murrine"
  {
  contrast 	= 0.8
  }
}

#####################
# OPTIONMENU / COMBO 
#####################
# use bg for background; fg for arrows; text for text on button; 
style "optionmenu" = "button"
{
  xthickness = 3 # x/y-thickness >= 3 or button on the right 
  ythickness = 3 # will be bigger than entry
}


################
# ENTRY 
################

style "entry"			= "murrine-default"
{
  bg[SELECTED]	= @theme_color
#  bg[NORMAL]	= "blue"	#border color
  base[NORMAL] = @tooltip_bg_color
  xthickness	= 3
  ythickness	= 2
  GtkWidget::interior_focus	= 0 

  engine "murrine"
  {
	contrast	= 0.8	
  }
}

####################
# LISTHEADERS 
####################

style "list-header"
{
   #Comment out the ythickness setting below for thicker column headers.
   ythickness = 3
#   GtkTreeView::odd_row_color	= "#F0F0F0"
#   GtkTreeView::even_row_color	= "#E4E4E4"

#  text[NORMAL] = "black"	#normal text color
#  text[ACTIVE] = "white"	#selected text color
   fg[NORMAL]		= "black"	#listheader text color
   bg[NORMAL]		= @theme_color #@selected_bg_color 	#listheader bg color
   base[ACTIVE] 	= darker (@bg_color) 	#normal deselected bg color
   base[SELECTED] 	= @selected_bg_color 	#normal selected bg color
}

style "list-headerbold" = "list-header"
{
font_name = "Bold"
}
widget_class "*<GtkTreeView>.<GtkButton>*" style "list-headerbold"
widget_class "*<GtkCTree>.<GtkButton>*" style "list-headerbold"
widget_class "*<GtkList>.<GtkButton>*" style "list-headerbold"
widget_class "*<GtkCList>.<GtkButton>*" style "list-headerbold"
####################
# GtkTree (sidepanes)
####################

style "sidepane"
{
   ythickness = 3
   GtkTreeView::odd_row_color	= @base_color
   GtkTreeView::even_row_color	= @tooltip_bg_color #sidepane color (thunar defined by this setting in default style)

#  text[NORMAL] = "black"	#normal text color
#  text[ACTIVE] = "white"	#selected text color
   fg[NORMAL]	= @selected_fg_color	#listheader text color
   fg[PRELIGHT]	= @theme_color	# arrows in tree and listheader text
   fg[ACTIVE]   = @text_color	# arrows in tree on click

   bg[NORMAL]		= @selected_bg_color 	# listheader bg color
#   bg[ACTIVE]       	= "red"		# listheader on click
#   bg[PRELIGHT]     	= "green"	# listheader prelight

   base[ACTIVE] 	= darker (@bg_color) 	#normal deselected bg color
   base[SELECTED] 	= @theme_color 	#normal selected bg color
#   text[NORMAL]       	= "black" # text color
#   text[ACTIVE]       	= "black"  # text color selected but unfocused
#   text[SELECTED]     	= "white" 
}

#################
# RANGE 
#################

style "range" = "murrine-default"
{
  bg[NORMAL] 	= @selected_bg_color 	#button-color & trough-color normal
  bg[PRELIGHT]	= @theme_color	#button-color prelight
  bg[SELECTED]	= @theme_color	#[trough pressed] and [fill if GtkScale::trough-side-details is set]

  engine "murrine"
  {
    contrast = 0.0
    roundness = 1
  }
}

####################
# SCROLLBAR 
####################

style "scrollbar" = "murrine-default"
{
  bg[NORMAL]		= @selected_bg_color #trough border colors
  bg[INSENSITIVE] 	= @selected_bg_color #stepper color if scrollbar is against it
  fg[NORMAL]		= @selected_fg_color #arrow on stepper
  fg[INSENSITIVE]	= @selected_bg_color #arrow on stepper

  engine "murrine"
  {
    contrast = 0.0
    roundness = 0
  }

}

###################
# PROGRESSBAR
###################

style "progressbar"
{
	bg[SELECTED] = @theme_color #progress color
	fg[PRELIGHT] = @fg_color  #text color covered by progress
	bg[NORMAL]   = @selected_bg_color # in murrine: border color

	engine "murrine" #murrine doesn't listen to bg[NORMAL] 
	{
	  contrast        = 0.0   #we've covered this with bg[NORMAL]
	  roundness	= 1
	  profile 	= CANDIDO
	}
}

##################
# TOOLTIPS
##################
style "tooltips"	= "murrine-default"
{
  bg[NORMAL]		= @tooltip_bg_color #overrides gtk-color on top of this file
}

##################
# RULER 
##################

style "ruler"		= "murrine-default"
{
#  bg[NORMAL]		= "#E4E4E4" # entire background
  bg[PRELIGHT]	= @base_color	# AbiWord background behind numbers
  text[NORMAL]	= @text_color 	# Abiword numbers, stripes
}

##################
# HANDLES 
##################

# null.png = transparant

style "handlebox"	= "murrine-default"
{
  engine "murrine"
  {
    contrast = 0.0 #handle disabled; increase value to enable
  }
}

#######################
# SEPARATORS
#######################
style "separator"
{
#  bg[NORMAL]       	= "#E4E4E4" #color of separators if pixmap below is disabled
#  engine "murrine"
#  {
#    contrast = 0.0
#  }
  engine "pixmap"
  {
    image
    	{
      	function	  = HLINE
      	recolorable = TRUE
      	file	  = "null.png"
     	border	  = { 1, 1, 1, 1 }
      	stretch	  = TRUE
    	}
  	
    image
    	{
      	function	  = VLINE
      	recolorable = TRUE
      	file	  = "null.png"
     	border	  = { 1, 1, 1, 1 }
      	stretch	  = TRUE
    	}
  }
}

#######################
# USEFUL STYLES ???
#######################
style "flat" 		= "murrine-default"
{
  engine "murrine"
  {
#    contrast = 0.0
  }
#  engine "pixmap"
#  {
#    image
#    {
#      function		= SHADOW
#    }
#  }
}

style "layout"	= "murrine-default"
{
}

####################
# INACTIVE TEXT (is this important ???)
####################

style "inactivetext"
{
  engine "mist"
 	{
	}
}

style "inactivetext2"
{
#  fg[NORMAL]		= "#000000"
#  fg[PRELIGHT] 	= "#ffffff"
#  text[PRELIGHT]        = "#ffffff"
   engine "mist"
 	{
	}
}

#####################
# UNSTYLE
#####################
# This prevents Sodipodi from crashing while opening the
# Object-Style dialog.

style "unstyle"
{
  engine ""
  {
  }
}

########################
# SPBUTTON FIX
########################

# recognizable pressed toggle buttons
# SPIcons seem to erase the background first. That's why I can't use
# the button style.

style "SPbutton" = "murrine-default"
{
#  engine "pixmap"
#  {
#    image
#    {
#      function		= BOX
#      shadow		= IN
#      recolorable	= TRUE
#      file			= "Shadows/shadow-out.png"
#      border		= { 2, 2, 2, 2 }
#      stretch		= TRUE
#    }
#    image
#    {
#      function		= BOX
#    }
#  }
}

style "theme-etree" = "list-header"
{
   bg[ACTIVE]          = @selected_bg_color
}

style "gedit-combo" = "murrine-default"
{
   bg[NORMAL]	= lighter (@base_color)
}
##########################################################
##########################################################
## 		WIDGET STYLES				##
## 	     MIND THE HIERARCHIE			##
## http://library.gnome.org/devel/gtk/unstable/ch01.html##
##########################################################
##########################################################
widget_class "*.<GtkLabel>" 	style "inactivetext"
widget_class "*.<GtkCellLayout>" 	style "inactivetext"
#widget_class "*.<Combo>" style "inactivetext"
widget_class "*.<GtkMenuItem>.*" 	style "inactivetext2"
widget_class "*Combo*" 		style "optionmenu"
widget_class "*BonoboDockItem"	style "toolbar"
class "*BonoboDockItem" 		style "toolbar"
widget_class "*HandleBox" 	style "toolbar"
class "*HandleBox" 		style "toolbar"
widget_class "*Toolbar" 		style "toolbar"
class "*Toolbar" 		style "toolbar"
widget_class "*Tool*GtkToggleButton" style "toolbuttons"
widget_class "*Tool*GtkButton" 	style "toolbuttons"
widget_class "*List" 		style "list-header"
widget_class "*GtkTree*" 	style "sidepane"
widget_class "*GtkCList*" 	style "list-header"
class "GtkButton"          	style "button"
class "GtkRadioButton"     	style "checkradiobutton"
class "GtkRadioMenuItem"    	style "menucheckbutton"
class "GtkCheckButton"     	style "checkradiobutton"
class "GtkCheckMenuItem"   	style "menucheckbutton"
class "GtkOptionMenu"		style "optionmenu"
class "GtkCombo*"      		style "optionmenu"
class "*Font*"      		style "optionmenu"
class "GtkEntry"           	style "entry"
class "GtkOldEditable" 		style "entry"
class "GtkSpinButton"   	 	style "spinbutton"
class "GtkRuler"           	style "ruler"
class "GtkScrollbar"       	style "scrollbar"
class "GtkStatusbar"		style "statusbar"
class "GtkProgress"     	style "progressbar"
class "GtkRange"         		style "range"
class "GtkMenu"       		style "menu"
class "GtkMenuBar*" 		style "menubar"
widget_class "*MenuBar.*" 	style "menubar"
widget_class "*.<MenuItem>."	style "menuitem"
class "GtkMenuItem"           	style "menuitem"
class "GtkTearoffMenuItem"	style "menuitem"
class "GtkNotebook"      		style "notebook"
class "GtkToolbar"       		style "flat"
class "GtkHandleBox"    		style "handlebox"
class "GtkEventBox"    		style "flat"
class "GtkPaned"       		style "handlebox"
class "GtkLayout"     		style "layout"
class "SPButton"         		style "SPbutton"
widget "gtk-tooltips"  		style "tooltips"
# prevent Sodipodi from crashing
class "SPColorSlider" 		style "unstyle"
# Evolution fix
widget_class "*.ETree*"   	style "theme-etree"
widget_class "*Separator*"	style "separator"
widget_class "*<GtkSeparatorMenuItem>*" style "separator_menu_item"
widget "*Gedit*Combo*" 		style "gedit-combo"
#class "GtkScrolledWindow" 	style "flat"
#class "GtkBox"			style "flat" #added MK
#class "GtkTextView"		style "flat" #added MK
#widget_class "*Tree*" style "list-header"

##########################################
# PANEL SECTION 
# (untweaked; I don't use gnome-panel or
# xfce-panel; have a look at tint2 )
##########################################

style "panel"
{

xthickness = 0
ythickness = 0

  fg[NORMAL]        = @selected_fg_color
  fg[PRELIGHT]      = @selected_fg_color
  fg[ACTIVE]        = @fg_color
  fg[SELECTED]      = @selected_fg_color
  fg[INSENSITIVE]   = darker (@selected_fg_color)
  
  text[NORMAL]	= @selected_fg_color
 
  bg[NORMAL]	= @selected_bg_color #affects gedit leftpane combobutton
  bg[SELECTED]	= @selected_bg_color
  bg[ACTIVE]	= @selected_bg_color
 
  bg_pixmap[NORMAL] 		= "null.png"
  bg_pixmap[ACTIVE] 		= "null.png"
  bg_pixmap[SELECTED] 		= "null.png"
  bg_pixmap[INSENSITIVE] 	= "null.png"
  bg_pixmap[PRELIGHT] 		= "null.png"
}

#############################################################

style "panelbar" = "panel"
{
  bg[NORMAL]	= @selected_bg_color
  bg[PRELIGHT]	= @selected_bg_color
  bg[SELECTED]	= @selected_bg_color
  bg[INSENSITIVE] = @selected_bg_color

#  bg[ACTIVE]	= "#E4E4E4"
}


#############################################################

style "panelbuttons"
{
  xthickness            			= 2
  ythickness            			= 1
  GtkWidget::focus_padding = 2

  bg[NORMAL]	= @selected_bg_color
  bg[PRELIGHT]	= @selected_bg_color
  bg[SELECTED]	= @selected_bg_color
  bg[INSENSITIVE] = @selected_bg_color
  bg[ACTIVE]	= @bg_color
}

#############################################################

#class "*Mail*" 				style "panel"
class "*notif*" 			style "panel"
class "*Notif*" 			style "panel"
class "*Tray*" 				style "panel"
class "*tray*" 				style "panel"
#widget_class "*Mail*" 			style "panel"
widget_class "*notif*" 			style "panel"
widget_class "*Notif*" 			style "panel"
widget_class "*Tray*" 			style "panel"
widget_class "*tray*" 			style "panel"
#widget "*TrayIcon*" 			style "panel"
class "*Panel*Applet*" 			style "panel"
widget_class "*Panel*GtkToggleButton" 	style "panel"
widget_class "*Panel*GtkButton" 	style "panel"
widget_class "*.Panel*Button*GtkLabel" 	style "panel"
widget_class "*.Panel*GtkLabel" 	style "panel"
widget "*PanelWidget*" 			style "panel"
widget "*PanelApplet*" 			style "panel"
widget_class "*Netstatus*" 		style "panel"
widget_class "*Tomboy*Tray*" 		style "panel"
widget "*fast-user-switch*" 		style "panel"
widget_class "*PanelToplevel*" 		style "panel"
class "Xfce*Panel*" 			style "panel"
widget_class "*Xfce*Panel*" 		style "panel"
widget_class "*PanelApplet*" 		style "panel"
widget_class "*PanelWidget*" 		style "panel"
#widget_class "*Panel*GtkToggleButton" 		style "panelbuttons" #also gedit leftpane togglebuttons
widget "*.tasklist-button" 			style "panelbuttons"
widget_class "*PanelToplevel*Button" 		style "panelbuttons"
widget_class "*Xfce*Panel*.GtkToggleButton" 	style "panelbuttons"
widget_class "*Xfce*NetkTasklist*GtkToggleButton" style "panelbuttons"
widget_class "*Panel*MenuBar*" style "panelbar"

#############################################################
#FIXES THE STANDARD SHUTDOWN-DIALOG ON GNOME
#############################################################

#style "fix"
#{
#xthickness = 0
#ythickness = 0

# bg[NORMAL]		= "#ffffff"
#}

#class "*Panel*" style "fix"

#############################################################
# backup
#  fg[NORMAL]       	= "#000000" # Metacity and mouseover, Most text
#  fg[ACTIVE]       	= "#000000"
#  fg[PRELIGHT]     	= "#ffffff" #changed after button, MK
#  fg[SELECTED]     	= "#FFFFFF"
#  fg[INSENSITIVE]  	= "#757575"

#  bg[NORMAL]       	= "#dddddd" # Normal Background was e4e4e4
#  bg[ACTIVE]       	= "#f6f6f6" # Mouseclicking, Tabs, active window list
#  bg[PRELIGHT]     	= "#262628" # Expand prelight bg
#  bg[SELECTED]     	= "#262628"
#  bg[INSENSITIVE]  	= "#E4E4E4"

#  base[NORMAL]     	= "#f6f6f6" # Background, most was f5
#  base[ACTIVE]     	= "#262628" # Menu active item in inactive window was 757575 MK
#  base[PRELIGHT]   	= "#E4E4E4"
#  base[INSENSITIVE]	= "#E4E4E4" # Inactive Entry bg
#  base[SELECTED]   	= "#262628" # Menu active item in active window was 757575 MK

#  text[NORMAL]	  	= "#000000" # Text in window, arrows
#  text[INSENSITIVE]	= "#000000" # Insensitive arrows
#  text[SELECTED]   	= "#FFFFFF" # Active text in active window
#  text[ACTIVE]     	= "#FFFFFF" # Active text in inactive window
#  text[PRELIGHT]   	= "#ffffff" # Text on Mouseover

```

---

### Post by VCoolio on 2009-11-08
Ok, found it. Had to define murrine engine for panels. Not sure if this is the right thing to do or if it's a bad workaround, but hey, it works. 

Added around line 770; style "panel" now looks like this:

```
style "panel"
{

xthickness = 0
ythickness = 0

  fg[NORMAL]        = @selected_fg_color
  fg[PRELIGHT]      = @selected_fg_color
  fg[ACTIVE]        = @fg_color
  fg[SELECTED]      = @selected_fg_color
  fg[INSENSITIVE]   = darker (@selected_fg_color)
  
  text[NORMAL]	= @selected_fg_color
 
  bg[NORMAL]	= @selected_bg_color #affects gedit leftpane combobutton
  bg[SELECTED]	= @selected_bg_color
  bg[ACTIVE]	= @selected_bg_color
 
  engine "murrine"
  {
  }
}
```

Thanks for reading; marking as solved.

---

