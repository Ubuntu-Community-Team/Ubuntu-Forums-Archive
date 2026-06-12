---
title: "GTK Separator Menu Item over Pixmap"
date: 2009-08-16
forum: Art &amp; Design
---

### Post by Exodist on 2009-08-16
Hope someone can help me with this. 
I have been spending all weekend working on a hybrid theme using Clearlooks and Pixmap engins. Everything is comming together but I have stumbled on a bug with the Menu Sepators.

[IMG]http://picasaweb.google.com/exodist2009/GTKBug#[/IMG][IMG]http://picasaweb.google.com/exodist2009/GTKBug#[/IMG]
[http://picasaweb.google.com/exodist2009/GTKBug#](http://picasaweb.google.com/exodist2009/GTKBug#)

Seems to keep leaving a gap and I cant figure out why.

I tried the base code thats in the basic Clearlooks GTK2 theme.

> #style "separator_menu_item" 
#{
#    xthickness = 1
#    ythickness = 1
#
#    GtkSeparatorMenuItem::horizontal-padding = 2
#    GtkWidget::wide-separators = 2
#    GtkWidget::separator-width = 2
#    GtkWidget::separator-height = 2
#}I even removed it as you can see and created one using pixmap

> style "pixmap-menu-separator"
{

engine "pixmap"
{
    image
    {
        function    = VLINE
        recolorable    = TRUE
        file        = "/menu/line-v.png"
        border        = {0,0,0,0}
        stretch        = TRUE
        }

    image
    {
        function    = HLINE
        recolorable    = TRUE
        file        = "/menu/line-h.png"
        border        = {0,0,0,0}
        stretch        = TRUE
    }
}    
}I did specify the styles at the bottom of the GTKRC file BTW.

Any suggestions on how to get it to render the vertical menu seperator?

Thanks,
Exo

---

### Post by days_of_ruin on 2009-08-16
I need to see the whole gtkrc file.

---

### Post by Exodist on 2009-08-16
Appreciate it, here we go:

> # ADD COMMENTS HERE


####### INCLUDE PANEL RC HERE ################################################################
include "panel.rc"






######## CLEAR LOOKS CODE ON TOP #############################################################

# Please keep this gtkrc in sync with the other ones from Clearlooks based themes.

gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#86ABD9\nselected_fg_color:#ffffff\ntext_color:#1A1A1A\nbg_color:#EDECEB\ntooltip_bg_color:#F5F5B5"

style "default" {
    xthickness = 1
    ythickness = 1

######## Styles hacked for pixmap use #############################

    


######## Original Clearlooks Styles #################################
    #######################
    # Style Properties
    #######################
    GtkButton::child-displacement-x = 1
    GtkButton::child-displacement-y = 1
    GtkButton::default-border = { 0, 0, 0, 0 }

    GtkCheckButton::indicator-size = 14

    GtkPaned::handle-size = 6

    GtkRange::trough-border = 0
    GtkRange::slider-width = 16
    GtkRange::stepper-size = 15

    GtkScale::slider-length = 23
    GtkScale::trough-side-details = 1

    GtkScrollbar::min-slider-length = 30
    GtkMenuBar::internal-padding = 0
    GtkExpander::expander-size = 16
    GtkToolbar::internal-padding = 2
    GtkTreeView::expander-size = 14
    GtkTreeView::vertical-separator = 0

    GtkMenu::horizontal-padding = 0
    GtkMenu::vertical-padding = 0

    WnckTasklist::fade-overlay-rect = 0
    # The following line hints to gecko (and possibly other appliations)
    # that the entry should be drawn transparently on the canvas.
    # Without this, gecko will fill in the background of the entry.
    GtkEntry::honors-transparent-bg-hint = 1

    GtkEntry::progress-border = { 2, 2, 2, 2 }

    ####################
    # Color Definitions
    ####################
      fg[NORMAL]        = "#000000" # Black
      fg[PRELIGHT]      = "#000000" # Black
      fg[ACTIVE]        = "#000000" # Black
      fg[SELECTED]      = "#FFFFFF" # White
      fg[INSENSITIVE]   = "#9e907d" # Warm Tan 9e907d

      bg[NORMAL]        = "#e7dbca" # Light Tan e8e4d8
      bg[PRELIGHT]      = "#FFFFFF" # White
      bg[ACTIVE]        = "#c9bfb0" # Medium Tan Unfocused TABS
      bg[SELECTED]      = "#0b6f96" # Blue 0b6f96
      bg[INSENSITIVE]   = "#c9bfb0" # Medium Tan
    
      base[NORMAL]      = "#FFFFFF" # white
      base[PRELIGHT]    = "#0b6f96" # Blue 0b6f96
      base[ACTIVE]      = "#0b6f96" # Blue 0b6f96
      base[SELECTED]    = "#0b6f96" # Blue 0b6f96
      base[INSENSITIVE] = "#FFFFFF" # white
    
      text[NORMAL]      = "#000000" # black
      #text[PRELIGHT]    = "#000000" # black #Remarked Out, not using with pixmap
      #text[ACTIVE]      = "#FFFFFF" # white #Remarked Out, not using with pixmap
      text[SELECTED]    = "#FFFFFF" # white
      text[INSENSITIVE] = "#202020" # Charcoal Grey


    engine "clearlooks" {
        colorize_scrollbar = FALSE #if you want the scroll bar blue set to TRUE
        reliefstyle = 1
        menubarstyle = 2   # 0 = flat, 1 = sunken, 2 = flat gradien
        toolbarstyle = 1   # 0 = flat, 1 = enable effects
        animation = TRUE
        radius = 3.0
        style = GLOSSY     #GUMMY

        # Set a hint to disable backward compatibility fallbacks.
        hint = "use-hints"
    }
}

style "wide" {
    xthickness = 2
    ythickness = 2
}

style "wider" {
    xthickness = 3
    ythickness = 3
}

style "entry" {
    xthickness = 3
    ythickness = 3

    bg[SELECTED]      = "#0b6f96" # Blue
    fg[SELECTED]      = "#FFFFFF" # White

    engine "clearlooks" {
        focus_color = shade (0.65, @selected_bg_color)
    }
}

style "spinbutton" {

    engine "clearlooks" {
        hint = "spinbutton"
    }
}

style "scale" {
    xthickness = 2
    ythickness = 2

    engine "clearlooks" {
        hint = "scale"
    }
}

style "vscale" {

    engine "clearlooks" {
        hint = "vscale"
    }
}

style "hscale" {

    engine "clearlooks" {
        hint = "hscale"
    }
}

style "scrollbar" {
    xthickness = 2
    ythickness = 2

    engine "clearlooks" {
        hint = "scrollbar"
    }
}

style "hscrollbar" {

    engine "clearlooks" {
        hint = "hscrollbar"
    }
}

style "vscrollbar" {

    engine "clearlooks" {
        hint = "vscrollbar"
    }
}

style "notebook_bg" {

    bg[NORMAL]        = shade (1.02, @bg_color)
}

style "button" {
    xthickness = 3
    ythickness = 3

    bg[NORMAL]        = "#e8e4d8"
    bg[PRELIGHT]      = "#ffffff"
    bg[ACTIVE]        = "#c9bfb0"              
}

# The color is changed by the notebook_bg style, this style
# changes the x/ythickness
style "notebook" {
    xthickness = 3
    ythickness = 3
}

style "statusbar" {

    engine "clearlooks" {
        hint = "statusbar"
    }
}

style "comboboxentry" {

    engine "clearlooks" {
        # Note:
        # If you set the appears-as-list option on comboboxes in the theme,
        # then you should set this hint on the combobox instead.
        hint = "comboboxentry"
    }
}

###################  REMARKED THIS OUT SINCE WHERE USING PIXMAP ########################
#style "menubar" {
#
#    engine "clearlooks" {
#        hint = "menubar"
#    }
#}


#style "menu" {
#    xthickness = 0
#    ythickness = 0
#
#    bg[NORMAL]        = shade (1.08, @bg_color)
#
#    engine "clearlooks" {
#        radius = 0.0
#    }
#}
##########################################################################################



style "menu_item" ######## IF YOUR BASHING YOUR SKULL-IN TRYING TO CHANGE DROP DOWN MENU TXT            ######## COLOR, ITS HERE WERE YOU ADJUST IT! NOT IN MENU ITS SELF!!  
{   
    xthickness = 2
    ythickness = 3

    fg[NORMAL] = "#d7d7d7"         
    fg[PRELIGHT] = "#FFFFFF"
    fg[ACTIVE] = "#FFFFFF"
    fg[SELECTED] = "#FFFFFF"
    fg[INSENSITIVE] = "#505050" #6b6b6b"

    bg[NORMAL] = "#9e907d"   #d7d7d7"
    bg[SELECTED] = "#3d3d3d" #000000"

    base[NORMAL] = "#FFFFFF"
    base[PRELIGHT] = "#FFFFFF"

    text[NORMAL] = "#FFFFFF"
    text[PRELIGHT] = "#FFFFFF"
    text [ACTIVE] = "#FFFFFF"    
    
}
##############################################################################################

# This style is there to modify the separator menu items. The goals are:
# 1. Get a specific height.
# 2. The line should go to the edges (ie. no border at the left/right)
#style "separator_menu_item" 
#{
#    xthickness = 1
#    ythickness = 1
#
#    GtkSeparatorMenuItem::horizontal-padding = 2
#    GtkWidget::wide-separators = 2
#    GtkWidget::separator-width = 2
#    GtkWidget::separator-height = 2
#}

style "frame_title" {

    fg[NORMAL]        = lighter (@fg_color)
}

style "treeview" {

    engine "clearlooks" {
        hint = "treeview"
    }
}

# The almost useless progress bar style
style "progressbar" {
    xthickness = 1
    ythickness = 1

    fg[PRELIGHT]      = @selected_fg_color

    engine "clearlooks" {
        # Explicitly set the radius for the progress bars inside menu items.
        radius = 3.0

        hint = "progressbar"
    }
}

# This style is based on the default style, so that the colors from the button
# style are overriden again.
style "treeview_header" = "default" {
    xthickness = 2
    ythickness = 1

    engine "clearlooks" {
        hint = "treeview-header"
    }
}

style "tooltips" {
    xthickness = 4
    ythickness = 4

    bg[NORMAL]        = "#e7dbca"
    fg[NORMAL]        = "#000000"
}

style "nautilus_location" {

    bg[NORMAL]        = mix (0.60, shade (1.05, @bg_color), @selected_bg_color)
}


# Workaround style for places where the text color is used instead of the fg color.##############
style "text_is_fg_color_workaround" {

    text[NORMAL]      = @fg_color
    text[PRELIGHT]    = @fg_color
    text[SELECTED]    = @selected_fg_color
    text[ACTIVE]      = @fg_color
    text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for menus where the text color is used instead of the fg color.###############
style "menuitem_text_is_fg_color_workaround" {

    text[NORMAL]      = @selected_fg_color #fg_color / The change fixes GIMP DDLB's
    text[PRELIGHT]    = @selected_fg_color
    text[SELECTED]    = @selected_fg_color
    text[ACTIVE]      = @selected_fg_color #fg_color / The change fixes GIMP DDLB's
    text[INSENSITIVE] = darker (@bg_color)
}

# Workaround style for places where the fg color is used instead of the text color.##############
style "fg_is_text_color_workaround" {

    fg[NORMAL]        = @text_color
    fg[PRELIGHT]      = @text_color
    fg[SELECTED]      = @selected_fg_color
    fg[ACTIVE]        = @selected_fg_color
    fg[INSENSITIVE]   = darker (@bg_color)
}


# Style to set the toolbar to use a flat style. This is because the "New" button in
# Evolution is not drawn transparent. So if there is a gradient in the background it will
# look really wrong.
# See [http://bugzilla.gnome.org/show_bug.cgi?id=446953](http://bugzilla.gnome.org/show_bug.cgi?id=446953).
style "evo_new_button_workaround" {

    engine "clearlooks" {
        toolbarstyle = 0
    }
}

#################################################################################
############# PIXMAP CODE #######################################################


############################### FILE MENU BAR ###################################
style "pixmap-menubar"        
{
engine "pixmap"
{    
image
{
    function        = BOX
    file            = "/menu/menubar.png"
       border            = { 0, 0, 0, 0 }
    stretch            = TRUE
}
}
}

############################# DROP DOWN MENUS #################################


style "pixmap-menu"
{


xthickness = 2
ythickness = 2

fg[NORMAL]        = "#FFFFFF" 
fg[PRELIGHT]      = "#FFFFFF" 
fg[ACTIVE]        = "#FFFFFF" 
fg[SELECTED]      = "#FFFFFF" 
fg[INSENSITIVE]   = "#FFFFFF" 

bg[NORMAL] = "#FFFFFF"
bg[PRELIGHT] = "#FFFFFF"
bg[SELECTED] = "#FFFFFF"

text[NORMAL] = "#FFFFFF"
text[PRELIGHT] = "#FFFFFF"
text[ACTIVE] = "#FFFFFF"


bg_pixmap[NORMAL] = "/menu/menu-bg.png"




engine "pixmap"
{

    image
    {
        function    = BOX
        recolorable    = TRUE
        detail        = "menu"
        file        = "/menu/menu.png"
        border        = { 2 ,2 , 2 ,2}
        stretch        = TRUE
    }

    image
    {
        function    = VLINE
        recolorable    = TRUE
        file        = "/menu/line-v.png"
        border        = {0,0,0,0}
        stretch        = TRUE
        }

    image
    {
        function    = HLINE
        recolorable    = TRUE
        file        = "/menu/line-h.png"
        border        = {0,0,0,0}
        stretch        = TRUE
        }


}
}
###########################################################################

style "pixmap-menu-separator"
{

engine "pixmap"
{
    image
    {
        function    = VLINE
        recolorable    = TRUE
        file        = "/menu/line-v.png"
        border        = {0,0,0,0}
        stretch        = TRUE
        }

    image
    {
        function    = HLINE
        recolorable    = TRUE
        file        = "/menu/line-h.png"
        border        = {0,0,0,0}
        stretch        = TRUE
    }    
}
}


######## ADD CLASSES ASSOCIATED WITH PIXMAPING ################################

class "GtkMenuBar"           style "pixmap-menubar"
class "GtkMenu"                style "pixmap-menu"
class "GtkSeparatorMenuItem"    style "pixmap-menu-separator"


###############################################################################
# The following part of the gtkrc applies the different styles to the widgets.
###############################################################################

# The default style is applied to every widget
class "GtkWidget" style "default"

class "GtkSeparator" style "wide"
class "GtkFrame" style "wide"
class "GtkCalendar" style "wide"
class "GtkEntry" style "entry"

class "GtkSpinButton" style "spinbutton"
class "GtkScale" style "scale"
class "GtkVScale" style "vscale"
class "GtkHScale" style "hscale"
class "GtkScrollbar" style "scrollbar"
class "GtkHScrollbar" style "hscrollbar"
class "GtkVScrollbar" style "vscrollbar"

# General matching follows. The order is choosen so that the right styles override
# each other. EG. progressbar needs to be more important than the menu match.
widget_class "*<GtkNotebook>" style "notebook_bg"
# This is not perfect, it could be done better.
# (That is modify *every* widget in the notebook, and change those back that
# we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkLayout>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkViewport>" style "notebook_bg"
widget_class "*<GtkNotebook>*<GtkScrolledWindow>" style "notebook_bg"

widget_class "*<GtkButton>" style "button"
widget_class "*<GtkNotebook>" style "notebook"
widget_class "*<GtkStatusbar>*" style "statusbar"

widget_class "*<GtkComboBoxEntry>*" style "comboboxentry"
widget_class "*<GtkCombo>*" style "comboboxentry"

#widget_class "*<GtkMenuBar>*" style "menubar"  # Remarked out, using Pixmap #
#widget_class "*<GtkMenu>*" style "menu"        # Remarked out, using Pixmap #
widget_class "*<GtkMenuItem>*" style "menu_item"
#widget_class "*<GtkSeparatorMenuItem>*" style "separator_menu_item"##################

widget_class "*.<GtkFrame>.<GtkLabel>" style "frame_title"
widget_class "*.<GtkTreeView>*" style "treeview"

widget_class "*<GtkProgress>" style "progressbar"

# Treeview headers (and similar stock GTK+ widgets)
widget_class "*.<GtkTreeView>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCTree>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkList>.<GtkButton>" style "treeview_header"
widget_class "*.<GtkCList>.<GtkButton>" style "treeview_header"

# The window of the tooltip is called "gtk-tooltip"
##################################################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
##################################################################
widget "gtk-tooltip*" style "tooltips"

##########################################################################
# Following are special cases and workarounds for issues in applications.
##########################################################################

# Workaround for the evolution ETable (bug #527532)
widget_class "*.ETable.ECanvas" style "treeview_header"

# Workaround for the evolution ETree
widget_class "*.ETree.ECanvas" style "treeview_header"

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "nautilus_location"

# Work around for [http://bugzilla.gnome.org/show_bug.cgi?id=382646](http://bugzilla.gnome.org/show_bug.cgi?id=382646)
# Note that this work around assumes that the combobox is _not_ in appears-as-list mode.
widget_class "*.<GtkComboBox>.<GtkCellView>" style "text_is_fg_color_workaround"

# This is the part of the workaround that fixes the menus
widget "*.gtk-combobox-popup-menu.*" style "menuitem_text_is_fg_color_workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the base color.
widget_class "*<GtkListItem>*" style "fg_is_text_color_workaround"

# GtkCList also uses the fg color to draw text on top of the base colors.
widget_class "*<GtkCList>" style "fg_is_text_color_workaround"

# Nautilus when renaming files, and maybe other places.
widget_class "*<EelEditableLabel>" style "fg_is_text_color_workaround"

# See the documentation of the style.
widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "evo_new_button_workaround"






---

### Post by days_of_ruin on 2009-08-16
Err you should have just attached the file.
Isn't the problem in the panel.rc?

---

### Post by eamon63 on 2009-08-17
agree with days_of_ruin above.  what are the contents of panel.rc.
using pixmap, maybe create a transparent image for your panel handles/separators?....

---

### Post by Exodist on 2009-08-17
Well It "should" I agree, but I borrowed the panel.rc from the Slickness theme since it had ton of other bug fixes and it works on the Slickness theme, so my conclusion is its not really in the panel.rc file. I even copy and pasted the file its self over to my theme since I hadnt changed it and same result. I do indeed see where the panel.rc has a blank graphic defined in the style. So what I belive is I gota conflict with panel.rc and my gtkrc. But where is kicking me in the but. 
The Separator applet/widget thing is the on you can add via the add-to-panel option. 
I checked my old DigitalDark pixmap themes and I dont have it definded anywhere in the file.
So I am at a loss atm. I appreciate you all taking time to help me on this.

Cheers,
Exo

---

### Post by days_of_ruin on 2009-08-17
The panel.rc requires images, we'll need those too.

EDIT: Just attach the whole theme.

---

### Post by eamon63 on 2009-08-17
my initial impression...
what happens when you remove the entire separator thing altogether from gtkrc? just let panel.rc define everything in the panel, as it already has class/widget definitions?

and use gtkmenuitem/menuitem to define the usual horizontal menu separators
and use  a separate item for your usual vertical separators/handles

---

### Post by Exodist on 2009-08-17
> my initial impression...
what happens when you remove the entire separator thing...Cant remember if I tried that all together or not. I think I did Rmk it out and theme crashed.. not sure.. Will try again.


> The panel.rc requires images, we'll need those too.

EDIT: Just attach the whole theme.     Will do, I really appreciate the help.

---

### Post by Exodist on 2009-08-17
> **eamon63 said:**
> my initial impression...
what happens when you remove the entire separator thing altogether from gtkrc? just let panel.rc define everything in the panel, as it already has class/widget definitions?

and use gtkmenuitem/menuitem to define the usual horizontal menu separators
and use  a separate item for your usual vertical separators/handles

Removed them and havent noticed any change. Even restarted gnome just in case it was some quirky render bug that may have got hung in the theme engine.

---

### Post by Exodist on 2009-08-17
OK, I got the vertical lines showing for the Notification Drawer now. /puts band-aid on forehead..
But the actual Icon/Widget Separator is still a no go.  Its progress I guess :-)

---

### Post by Exodist on 2009-08-18
I appreciate the help everyone. I decided to quit cutting corners and just use my pixmap theme instead of making a hybrid theme and currently I have no noticed bugs in my theme. So now I can focus on the graphics and make minor changes to my code if necessary :-)

Exo

---

