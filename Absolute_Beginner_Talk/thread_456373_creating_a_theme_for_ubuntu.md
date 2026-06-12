---
title: "creating a theme for ubuntu"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-05-27
what is the best and most reliable source for a tutorial on this. i don't want to mess things up.

---

### Post by johnny4north on 2007-05-27
i know of a good theme site for ubuntu. here - [http://www.gnome-look.org/content/show.php/God+is+with+us%21?content=52136](http://www.gnome-look.org/content/show.php/God+is+with+us%21?content=52136)

---

### Post by thesonisshining on 2007-05-27
that's a sweet theme; but i was looking for a tutorial on how to create a theme.

---

### Post by crimesaucer on 2007-05-27
The thing I did, was to pick a theme I liked from my default themes, and then change the colors to figure out where things go, write it down so you now have a list like this one I made for xfce xubuntu themes:

```
#
###### THIS IS NOT AN ACTUAL GTKRC!!!!! THIS IS A CHEAT SHEET FOR LOACTIONS AND EXPLAINATIONS OF WHAT I'VE LEARNED!!!!!!########

gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 10
    GtkButton::focus-line-width       = 1
    GtkButton::focus-padding          = 0
    GtkCheckButton::indicator_size    = 15
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 1
    GtkPaned::handle_size             = 8
    GtkRadioButton::indicator_size    = 15
    GtkRange::slider_width            = 15
    GtkRange::stepper_size            = 15
    GtkRange::stepper_spacing         = 0
    GtkRange::trough_border           = 0
    GtkScrollbar::min_slider_length   = 37  # smallest size of scroll bar slider to match size of buttons (4 X 4), it looks good in User inter Pref.
    GtkToolbar::shadow_type           = out # I changed this from none to out to fix the way it looks in certain apps. There are other ways to draw the shadows with "etched-in" and other ways. Just read other xfce gtkrc files to learn.
    GtkWidget::focus-line-width       = 1
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 1 # I changed this from 2 to 1 to make the dividing lines between icons smaller.
    ythickness = 0 # I changed this from 2 to 0 to make the dividing lines between tool bars disappear.
 
    fg[NORMAL]        = This is the font color in the menu bars in FF and xubuntu, and also the color of the app in the pager that is open on a different Desktop.
    fg[ACTIVE]        = This is the font color of a unopened tab and of the text for a roll-over check box before it is rolled over. Example: like the font for the check boxes for- "Use hinting :"
    fg[PRELIGHT]      = Selected (roll over) font color of check boxes like- "Use hinting :"
    fg[SELECTED]      = The opened app color in the pager for the Desktop you are on, and the font color for the closing dialog boxes font: "End Session" . 
    fg[INSENSITIVE]   = This is for the color of the font that can't be clicked (usually lighter) that is in Your right click menu, and Edit Drop Down Menus. Usually it is used for the "Back" and "Forward" options when you can't go back and forward. This is also the color of the the word "Google" in the search bar before you type anything. Also the arrows of the scroll bars.
 
    bg[NORMAL]        = This is the overall color of the Browser for Firefox, xubuntu/ubuntu, Thunderbird, and all apps. It creates the color that is used for my gradient browser themes. It is also all of the buttons, scroll bar handles, panel handle, Drop down menus (before you roll over them with the mouse tool tip). 
    bg[ACTIVE]        = Scroll bar gradient background color, unopened Tab background color.
    bg[PRELIGHT]      = The color of a Firefox Tab loading, or downloading activity as seen in Firefox Downloading Manager, or GIMP. Also is the selected color of background for check boxes like- "Use hinting" in the User Inter Prefs. And the color of the scroll bar slider when you press it- (basically where the you move a scroll bar at).
    bg[SELECTED]      = End Session bg color and border color for End Session dialog box. Also the filler color of an open app on top of another app in the Desktop you have open in the pager.
    bg[INSENSITIVE]   = Toggle buttons that can't be clicked, regular Menu arrow backgrounds, nonactive check box outlines and nonactive radio button outlines

    text[NORMAL]      = Font color used for Mousepad, Firefox (web pages unless you un-check you "Use System Colors" in Firefox Preferences-->--Content-->--Colors), Url font, Thunar font (not selected), xubuntu menus (not selected). Checks for check boxes, radio dots too. Combobox, ComboBoxEntry, GtkCombo, GtkEntry, and numbers in numberbox.  
    text[ACTIVE]      = The font color in the left side of the Thunar File System- Home, Trash, Desktop, File System, when you are in a different folder like /usr. (mess around with it and you will see)
    text[PRELIGHT]    = Radio/Checks and ComboBox font colors. ComboBox is important to match.
    text[SELECTED]    = Highlighted font color in web pages and mousepad. Selected font color in the Thunar file system, and xubuntu menus like User interface.
    text[INSENSITIVE] = nonactive font in un-clickable Combos and GtkCombos. un-clickable radio/checks.

    base[NORMAL]      = Mousepad background color, Thunar files use this for the background strips on the right side and the background color on the left side, Firefox URL/Search bar backgrounds, ComboBoxEntry bg, GtkEntry bg, GtkCombo bg, Checkbox RadioButton backgrounds, Header and menu bg color for User Interface Preferences.
    base[ACTIVE]      = The bg color for the last folder opened (not selected and current) folder of Thunar or User Interface Pref. If you have Thunar open to File system-->--usr or "/usr", the File system folder (on the left, and any other folder in a different app like User Interface Pref.), will have this bg color while you are in the currently opened /usr folder.
    base[PRELIGHT]    = Background color for radio boxes and check boxes when rolled over (selected).
    base[SELECTED]    = The bg color for the open (selected and current) folder of Thunar User Inter Pref, Also the background color of Highlighted text, and the coloring of the Frame divider, and the strip in the scroll bar slider, basically the part you click onto when moving the scroll bar. 
    base[INSENSITIVE] = ComboBoxEntry bg (Disabled), GtkEntry bg (Disabled), GtkCombo bg (Disabled), Checkbox (Disabled) RadioButton (Disabled) backgrounds.


engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill             # I added a boxfill here to create a gradient in my toolbar. 87 to 83 usually blend into
                            # the color of the Firefox tabs bar so there is no visible line. 97 is a matching color
                            # for it to blend into the shade_end = 0.97 in the: style "menubar" = "colored" boxfill
                            # gradient section. this blends the menubar and the toolbar into a smooth blend.
        {
            fill_style = gradient
            orientation = auto
            shade_start = 0.97
            shade_end = 0.87
        }
    }
} 
widget_class "*" style "default"

``` 

and this part:

```
style "colored" = "default"
{
    xthickness = 4  # this I might not of needed to change from 3. It is for the outline of the Thunar Path box. 
    ythickness = 4  # this I changed from 3 to 4 to make the Thunar Path Box taller. These two settings might effect other spots to make the same boxes bigger.

    bg[ACTIVE]        = Active button on panel handle, selected background color when clicking any app button, (not Firefox), ComboBox Drop down menu arrow button bg.
    bg[PRELIGHT]      = Rollover background color (hover) on all buttons and drop down menus.

    fg[ACTIVE]        = Font for active button, ComboBoxEntry drop down foreground arrow.
    fg[PRELIGHT]      = Font color for all selected buttons (roll over) except ComboBox and ComboBoxEntry (only arrows), Also font color for all rollover drop down menus.

    text[ACTIVE]      = Old highlighted font (like if you highlight text, and then click on a different window, the text color and bg color will change. This is for the text foreground font color for the base[active] background color. (basically, "active" is like a folder that is opened before opening the next folder which is base[selected] and text[selected] ) 
    text[PRELIGHT]    = ComboBox and ComboBoxEntry font color.

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient     # this I changed from a fill_style = plain, to gradient so I could have gradient roll-
            orientation = vertical    # over, drop down menus in Firefox, and other menus. I chose orientation = vertical
            shade_start = 1.24        # to force the menus to match the tool bars. try "auto" and see if you like it.   
            shade_end = 0.83          # it will draw the gradient sideways. Also mess with the percentage numbers for
	}                             # your own style.
    }
}

widget_class "*List*"              style "colored"
class "*List*"                     style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"

```

Then, you can learn things about your widgets, and you get to know how to make a theme.

I've learned a few more things that I've basically memorized that aren't on these pieces of my list, but I haven't wrote a new how to with more detail because I didn't get much feedback on the first one I wrote for xubuntu and the engines "xfce" theme engine. My new theme styles use a: shade_end = 1.00 for the default so that the toolbar has a gradient blend into the rest of the app like in Thunar. Then I fix the tab-bar in Firefox with userChrome.css to make it look better for Firefox, because having the shade_end = 1.00 will make all Linux apps look really good. 


Just copy your theme so you have a back-up of the original and so you can compare the 2 to see what you have changed and if you like it better.

---

### Post by qamelian on 2007-05-27
> **thesonisshining said:**
> that's a sweet theme; but i was looking for a tutorial on how to create a theme.

Check here ([http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)) for information on creating Gnome themes.

---

### Post by johnny4north on 2007-05-27
here is a great how-to link - [http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)   :)

---

### Post by crimesaucer on 2007-05-27
Also, install the app called: thewidgetfactory 

then run this in your Terminal:

```
twf
```

Now you can see what widgets you change, and what colors and styles you need to change to match.

This is the widget factory and my latest theme:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71-1.png[/IMG]
LARGE VIEW: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71.png)

---

### Post by thesonisshining on 2007-05-27
thanks that a lot of info.....so......that's probably going to be enough for a few weeks. so thank all of you.;)

---

### Post by coffeecat on 2007-05-27
> **crimesaucer said:**
>                  We are the music-makers, and we are the dreamers of dreams- Willy Wonka.

**crimesaucer**, thanks for the info on thewidgetfactory.

Sorry to go OT, but I noticed your sig. I'm afraid Willy Wonka pinched that line from an altogether more illustrious poet. :wink:

We are the music makers,
And we are the dreamers of dreams,
Wandr'ing by lone sea-breakers
And sitting by desolate streams;
World losers and world foresakers,
On whom the pale moon gleams:
Yet we are the movers and shakers
Of the world for ever, it seems.

Arthur O'Shaughnessy 1844-1881

I thought it was worth quoting at length, except that's just the first verse!

Note the 'movers and shakers' - the origin of this phrase. O'Shaughnessy means poets and artists, not self-serving politicians, industrialists and entrepreneurs. 

OK. You can go on talking about theming Ubuntu now.  :)

---

### Post by crimesaucer on 2007-05-27
Yes, I knew that, most of that movie has samples of other's works. I just really liked that part in the movie (I actually love that whole movie), so I quoted Willy Wonka for when he had said it in the movie.

Here is a cool page about Willy Wonka: [http://home.att.net/~tom.brodhead/wonka.htm](http://home.att.net/~tom.brodhead/wonka.htm)

---

### Post by coffeecat on 2007-05-27
That's a good link. I'll bookmark it. Thanks for that.

I see it gives three verses of the O'Shaughnessy poem. But there's more.... :D

---

