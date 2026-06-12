---
title: "Same gtk theme for sudo user"
date: 2006-10-15
forum: Art &amp; Design
---

### Post by Owdy on 2006-10-15
How can i make my theme to use same gtk theme as normal user? Now every thing where i have to give password uses gnome default icon and gtk theme. Example in upgrade app progress bar goes ugly etc.

In human theme this wont happen, but it happends with my own.

Heres my gtk file

```
style "clearlooks-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15
  
  GtkScrollbar   ::min_slider_length = 35
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 31
#  GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
#  GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
#  GtkScrollbar   ::has-secondary-forward-stepper = 1
#  GtkScrollbar   ::has-secondary-backward-stepper = 1

  GtkButton      ::child-displacement-x = 0
  GtkButton      ::child-displacement-y = 0

  xthickness = 1
  ythickness = 1

    fg[NORMAL]        = "#101010"
    fg[PRELIGHT]      = "#000000"
    fg[ACTIVE]        = "#000000"
    fg[SELECTED]      = "#ffffff"
    fg[INSENSITIVE]   = "#b5b3ac"

    bg[NORMAL]        = "#efebe7"
    bg[PRELIGHT]      = "#f5f3f0"
    bg[ACTIVE]        = "#d0c8c1"
    bg[SELECTED]      = "#4f71ae"
    bg[INSENSITIVE]   = "#efebe7"

    base[NORMAL]      = "#ffffff"
    base[PRELIGHT]    = "#617BA3" #617BA3
    base[ACTIVE]      = "#d0c8c1"
    base[SELECTED]    = "#4f71ae" 
    base[INSENSITIVE] = "#efebe7"

    text[NORMAL]      = "#101010"
    text[PRELIGHT]    = "#000000"
    text[ACTIVE]      = "#333333"
    text[SELECTED]    = "#ffffff"
    text[INSENSITIVE] = "#b5b3ac"

  engine "ubuntulooks" 
  {
    menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     = 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle = 1       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  = 1       # 0 = candy bar, 1 = fancy candy bar, 2 = flat
    animation         = FALSE
  }
}


style "clearlooks-wide" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-wider" = "clearlooks-default"
{
  xthickness = 3
  ythickness = 3
}

style "clearlooks-button" = "clearlooks-wider"
{
      bg[NORMAL] = "#f8f5f2" # was #eae4df
      bg[PRELIGHT] = "#fcfaf7"
      bg[INSENSITIVE] = "#efebe7"
  
#  fg[ACTIVE] = "#ffffff"
}

style "clearlooks-notebook" = "clearlooks-wide"
{
      bg[NORMAL] = "#E5E1DD"
      bg[ACTIVE] = "#E5E1DD"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

#menut/alasvetovalikot tausta0000
style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 1
  bg[NORMAL] = "#F7F3EF"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
    fg[PRELIGHT] = "#000000"
}

#valikot
style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  bg[SELECTED] = "#4f71ae" 
  fg[PRELIGHT] = "#ffffff"
  text[PRELIGHT] = "#ffffff"
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
  xthickness = 2
  ythickness = 2
  fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "metacity-frame" = "clearlooks-default"
{
 bg[SELECTED] = "#4f71ae" #"#4f71ae"
}

# Evolution uses bg and fg for its ETree instead of base and text like it should
style "evolution-hack" = "clearlooks-default"
{
  bg[ACTIVE]   = "#9ab4db"
  bg[SELECTED] = "#b8dce8"
  fg[ACTIVE]   = "#000000"
  fg[SELECTED] = "#000000"
}
    

# widget styles
class "GtkWidget" style "clearlooks-default"
class "GtkButton" style "clearlooks-button"
#class "GtkScale"  style "clearlooks-button"
class "GtkCombo"  style "clearlooks-button"
class "GtkRange"  style "clearlooks-wide"
class "GtkFrame"  style "clearlooks-wide"
class "GtkMenu"   style "clearlooks-menu"
class "GtkEntry"  style "clearlooks-wider"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
class "MetaFrames" style "metacity-frame"
 
#class "GtkMenuBar" style "clearlooks-menubar"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
widget_class "*MenuItem.*ProgressBar*" style "clearlooks-default"
#widget_class "*.GtkMenuBar.*MenuItem.*" style "clearlooks-menubar-item"

# combobox stuff
widget_class "*.GtkComboBox.GtkButton" style "clearlooks-combo"
widget_class "*.GtkCombo.GtkButton"    style "clearlooks-combo"
# tooltips stuff
widget_class "*.tooltips.*.GtkToggleButton" style "clearlooks-tasklist"
widget "gtk-tooltips" style "clearlooks-tooltips"

# treeview stuff
widget_class "*.GtkTreeView.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCTree.GtkButton" style "clearlooks-tree"
widget_class "*.GtkList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkCList.GtkButton" style "clearlooks-tree"
widget_class "*.GtkFrame.GtkLabel" style "clearlooks-frame-title"

# notebook stuff
widget_class "*.GtkNotebook.*.GtkEventBox" style "clearlooks-notebook"
widget_class "*.GtkNotebook.*.GtkViewport" style "clearlooks-notebook"

# those should really use base and text colors instead
widget_class "*GtkCTree*" style "evolution-hack"
widget_class "*GtkList*" style "evolution-hack"
widget_class "*GtkCList*" style "evolution-hack"
widget_class "*.ETree.*" style "evolution-hack"
```

---

### Post by HanZo on 2006-10-15
the problem is that when you install a new theme it will be placed in ~/.themes when launching an app as root (sudo) it will look for the same theme as you have set for you user in /usr/share/temesm but fill not find it.
to solve this problem just copy all the themes in /usr/share/themes.
the same for icons btw.

---

### Post by Owdy on 2006-10-15
Thanks! Worked!

---

### Post by djahma on 2012-04-27
my problem is the opposite direction. I've got this dark adwaita theme placed in /usr/share/themes/adwaita and when I select it, some apps work fine on it, but not nautilus when opening it as a user. however, when I do sudo nautilus, the theme works:confused: 
Any idea why some apps use the theme fine as a user and not some other apps which require sudo to use it properly?

---

### Post by Perfect Storm on 2012-04-27
This is almost a 5 years thread you resurrected from the dead. What work back then, doesn't works now.
Please start a new thread.


Thread closed.

---

