---
title: "A Beginner &quot;How To&quot; for gtkrc themes."
date: 2007-03-06
forum: Art &amp; Design
---

### Post by crimesaucer on 2007-03-06
!!!!!!!**********EDITED June18th,2007************!!!!!!!!!!!! (This Thread is very old and out of date, consider it closed - Nov.24,2009)


#### This is a short story about my beginner experiences with gtkrc themes and other things having to do with being a beginner on xubuntu/ubuntu.####





I AM A BEGINNER, SO DON'T BE RUDE IF I DID SOMETHING THE WRONG WAY, JUST POST THE PROPER WAY AND IT WILL HELP EVERYONE TO LEARN.





When I first started to look into re-writing my themes, I opened up my /usr/share/themes/Xfce-winter/gtk-2.0 directory, which was the gtk-2.0 theme that I wanted to modify. 

I then opened up that gtk-2.0 folder to read the gtkrc file inside of it, to see if I could change some of the basic colors of that theme on my own. 

When I first looked at the gtkrc for Xfce-winter, the only thing that I could understand was the hex-code colors (#C0C0C0 is gray). Even then I wasn't sure of which color was for what location in my theme. 

So, through trial and error, I ended up modifying the Xfce-winter gtkrc into one of my first themes that I called Xfce-rusted. 

I had successfully changed all of the colors but nothing else. I was very proud of it, and it even worked in Firefox and Thunderbird. Every detail that I had modified with my new colors had made my xubuntu theme more enjoyable then most of my installed default themes, and I had been able to match my new desktop OS theme to my wallpaper's colors exactly.

Well, it's funny how you can be proud of something, and then keep improving on it, then look back at your first attempts, and feel that they all look so lame now. I'll try to show what I mean with a few screenshots. 




....This was maybe my 5th or 6th theme attempt, pretty much just Xfce-winter with different colors called Xfce-rusted....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-8-11.png[/IMG]


.... My next attempt with a gradient....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-9-11.png[/IMG]


.... Then with a different gradient....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-10-10.png[/IMG]


.... Then with no dividing lines....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-11-6.png[/IMG]


.... And a newer style....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-12-7.png[/IMG]


....the newest way I made it look with a Firefox fix on the tab bar so the theme would look better in xubuntu....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-14-8.png[/IMG]


....another way to make it look...

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-15-12.png[/IMG]



This "How To" guide is not from an expert, but rather a list of tips that I have self taught myself through many hours of trial and error. I had searched for guides to explain the different theme engines and could not find any that fully explained every detail that I wanted to know, and after learning a few things on my own, I thought I might help other beginners that might want to start making their own themes by sharing a few things I had learned.

I hope that anybody that has something to add, or any corrections or tips to help out with, will post on this thread. Let's make this an ongoing thread for those of us that enjoy themes, and sharing themes with others. Any shared tips and bits of code to help better each others themes will be appreciated. Always give credit where credit is due, and try to share as many links as you can that have any info on theme development. 

And if you have a nice Emerald theme to share, then post a link too.  


***LONG BORING STORY IS OVER, NOW FOR THE LIST: 

**PLEASE DO NOT INSTALL THE LIST.** THIS IS NOT THE GTKRC. **

# xfce-rusty_newb, my modification of xfce-winter
# This is a modification of the gtk-2.0-engines-xfce theme called Xfce-winter. I have changed a lot of settings
# and I have tried to explain things that I did. These are my default settings for most all of my themes now. The
# only thing I need to change usually is the gradient percentages to work with the colors I have chosen. What I don't know
# I usually leave alone because I am happy with the way the theme works. 
#
#
# WARNING!!!! WARNING!!!! WARNING!!!! WARNING!!!! WARNING!!!! WARNING!!!!!!!#######
#
#   DO NOT INSTALL THIS.
#
#
###### THIS IS NOT AN ACTUAL GTKRC!!!!! THIS IS A CHEAT SHEET FOR LOACTIONS AND EXPLAINATIONS OF WHAT I'VE LEARNED!!!!!!########

gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0} # a border around the close button
    GtkButton::default_spacing        = 10 
    GtkButton::focus-line-width       = 1
    GtkButton::focus-padding          = 0
    GtkCheckButton::indicator_size    = 15 #size of the indicator for the roll over
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 1
    GtkPaned::handle_size             = 8 # this is for the movable divider in Thunar between the folders of the leftside and rightside
    GtkRadioButton::indicator_size    = 15 #size of the indicator for the roll over
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

    xthickness = 0 # I changed this from 2 to 0 to make the dividing lines between icons disappear, it makes my Orage calendar look better.
    ythickness = 0 # I changed this from 2 to 0 to make the dividing lines between tool bars disappear.
 
    fg[NORMAL]        = This is the font color in the menu bars in FF and xubuntu, and also the color of the app in the pager that is open on a different Desktop.
    fg[ACTIVE]        = This is the font color of a unopened tab and of the text for a roll-over check box before it is rolled over. Example: like the font for the check boxes for- "Use hinting :" in User Interface Pref 
    fg[PRELIGHT]      = Selected (roll over) font color of check boxes like- "Use hinting :"
    fg[SELECTED]      = The opened app color in the pager for the Desktop you are on.
    fg[INSENSITIVE]   = This is for the color of the font that can't be clicked (usually lighter) that is in drop down menus, also the Firefox right click menu for the "Back" and "Forward" options for when you can't go back or forward. This is also the color of the the word "Google" in the search bar before you type anything. Also the arrows of the scroll bars.
 
    bg[NORMAL]        = This is the overall color of the Browser for Firefox, xubuntu/ubuntu, Thunderbird, and all apps. It creates the color that is used for my gradient browser themes. It is also all of the buttons, scroll bar handles, panel handle, Drop down menus (before you roll over them with the mouse tool tip). 
    bg[ACTIVE]        = Scroll bar gradient background color, unopened Tab background color.
    bg[PRELIGHT]      = The color of a loading process bar (Firefox tabs), or the downloading process bar as seen in Firefox Downloading Manager , or apps loading like the GIMP. Also is the selected color of background for check boxes like- "Use hinting" in the User Inter Prefs. And the color of the scroll bar slider when you press it- (basically where the you move a scroll bar at).
    bg[SELECTED]      = End Session border color for the End Session dialog box. Also the filler color of an open app on top of another app in the Desktop you have open in the pager.
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
	boxfill             # I added a boxfill here to create a gradient in my toolbar. 
                              # I use shade_start = 0.90 to start the gradient darker at the top of the tool bar
                              # I use shade_start = 1.10 to start the gradient lighter at the top of the tool bar
                              # I use shade_end = 1.00 to end the gradient at a 100% fill of the bg[NORMAL] color, this way the color blends perfectly into the app.
                            # NOW........if you don't want to use a Firefox userChrome.css to fix the tab-bar...you can do it my old way of fading into the Firefox
                            # default gradient used....it's usually near shade_end = 0.87 and just match the shade_start in the same way, so that it matches the shade_end of the menu bar.
                            
        {
            fill_style = gradient
            orientation = auto
            shade_start = 0.90
            shade_end = 1.00
        }
    }
} 
widget_class "*" style "default"

#/***** OK, I'll try to explain this, but remember, I am a beginner and am totally self taught since I can't find any
#      documentation, or "How To's" on gtkrc modification. So this might be wrong, and if you know how to explain it
#      better, please write it down so I can learn it and so others can learn it. I will edit this, or just post a new guide.  
#
#  This is where the next styles start. 

style "colored" = "default"
{
    xthickness = 4  # Play around with this for your own preference.
    ythickness = 4  # this I changed from 3 to 4 to make the Thunar Path Box taller. Play around with this for your own preference.

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

# And now a new style starts for menubar


style "menubar" = "colored"
{
    xthickness = 0  # I changed this from 2 to 0 to change size of the dividing lines between the icons on the menu bar. Play around with this for your own preference.
    ythickness = 0  # I changed this from 2 to 0 to erase the dividing line between the menu bar and the tool bar. Play around with this for your own preference.

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient  # I changed the fill style to gradient and added the percentages.
            orientation = auto
          shade_start = 0.80  # This is the very top of your menubar, 0.80 is a darker gradient, 1.20 is a lighter gradient   
            shade_end = 0.90  # This is the bottom of the menubar, 0.90 is the exact color of the top of the toolbar...also 1.10 would be the same if you made it lighter...
        }
    }
}

widget_class "*BonoboDockItem"     style "menubar"
class "*BonoboDockItem"            style "menubar"
widget_class "*HandleBox"          style "menubar"
class "*HandleBox"                 style "menubar"
widget_class "*ToolBar"            style "menubar"
class "*ToolBar"                   style "menubar"
widget_class "*MenuBar"            style "menubar"
class "*MenuBar"                   style "menubar"

style "menuitem" = "colored"
{
    xthickness = 2 # Play around with this for your own preference.
    ythickness = 2 # Play around with this for your own preference.

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
             fill_style = gradient
            orientation = auto
            shade_start = 1.73  # I have changed the percentage and flipped it to create a different look in the drop down menus. Play around with this for your own preference.
            shade_end = 0.83    # I have changed the percentage and flipped it to create a different look in the drop down menus. Play around with this for your own preference.
        }
    }
}

widget_class "*MenuItem*"          style "menuitem"
class "*MenuItem*"                 style "menuitem"

style "scrollbar" = "default"
{
    xthickness = 0   # I changed this from 2 to 0 to change the space divider between the scroll bar slider, and the scroll arrows. 0 is no space. Play around with this for your own preference.
    ythickness = 1   # I changed this from 2 to 1 to change the way the progress looks in the Firefox tabs. It's wider. Play around with this for your own preference.
    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 1.73   # I have changed the percentage and flipped it to create a different "bubbled out" look in the scroll bar. Play around with this for your own preference.
            shade_end = 0.60     # I have changed the percentage and flipped it to create a different "bubbled out" look in the scroll bar. Play around with this for your own preference.
        }
    }
}
widget_class "*Scrollbar*"         style "scrollbar"
class "*Scrollbar*"                style "scrollbar"
widget_class "*GtkProgress*"       style "scrollbar" 
class "*GtkProgress*"              style "scrollbar" 

style "button" = "colored"
{
    xthickness = 4  # I changed this from 3 to 4 to make my buttons wider
    ythickness = 4  # I changed this from 3 to 4 to make my buttons longer.

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.92   # I have changed the percentage and flipped it to create a different "bubbled out" look
            shade_end = 0.82     # I have changed the percentage and flipped it to create a different "bubbled out" look
        }
    }
}
widget_class "*Button*"            style "button" 
class "*Button*"                   style "button" 
widget_class "*button*"            style "button" 
class "*button*"                   style "button" 
widget_class "*Togglebutton*"      style "button" 
class "*Togglebutton*"             style "button" 
widget_class "*togglebutton*"      style "button" 
class "*togglebutton*"             style "button" 
widget_class "*OptionMenu*"        style "button" 
class "*OptionMenu*"               style "button" 
widget_class "*Tree*"              style "button" 
class "*Tree*"                     style "button" 
widget_class "*GtkScale*"          style "button" 
class "*GtkScale*"                 style "button" 

widget_class "*CheckButton*"       style "default"
class "*CheckButton*"              style "default"
widget_class "*RadioButton*"       style "default"
class "*RadioButton*"              style "default"

# OK I removed the rox filer part since I don't have it installed.

# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar" = "default"
{
    bg[SELECTED]      = color for opened window frame (window in front of windows)
    fg[SELECTED]      =  color of titlebar text on open frame (window in front of windows)
    bg[INSENSITIVE]   = color for non-opened window frame (windows behind the open window)
    fg[INSENSITIVE]   = color of titlebar text on non-open frame (windows behind the open window)
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 

# I removed this part so it doesn't use the rodent yellow "X" close button and menu icons: (include "/usr/share/icons/Rodent/iconrc-png")
That way it uses all of the icons from my different icon packs for the close buttons...and other buttons.


...ALSO, FEEL FREE TO POST YOUR OWN LISTS OF EXPLANATIONS FOR OTHER THEMES, AND ANY THING THAT MY LIST FOR THE XFCE-ENGINE LEFT OUT. ALSO BE SURE TO POST YOUR SCREENSHOTS AND YOUR GTKRC THAT YOU WANT TO SHARE WITH OTHERS.

---

### Post by crimesaucer on 2007-03-06
I EDITED this part since I change the post above.

---

### Post by crimesaucer on 2007-03-06
Here are two links for my Emerald themes if anybody would like them:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/TheHULK-38.png[/IMG]
[http://themes.beryl-project.org/theme_details.php?id=81](http://themes.beryl-project.org/theme_details.php?id=81)


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-69b.png[/IMG]
[http://themes.beryl-project.org/theme_details.php?id=58](http://themes.beryl-project.org/theme_details.php?id=58)

---

### Post by ffxr on 2007-03-07
excellent work, crimesaucer & many thanks.. 

ll have a good go at customising a theme, when i get a chance.. later in the week..

i do like your dark emerald one, can you post your latest gtkrc for it pls..?

---

### Post by crimesaucer on 2007-03-07
old theme Edited....

---

### Post by scigirl on 2007-03-10
Hi,
This is a great little "how to"!
I have one problem though - when creating the theme, somehow it applies itself not only to windows, dialogs, menus, toolbars and stuff, but somehow manages to apply itself to the buttons and text fields in firefox. This causes a problem because if you choose a dark theme with white font (like the moonglow one above), all the buttons and text fields look out of place, and if the website overwrites one color (say the bg color of text fields like this forum does), then the text still stays white and I can't see what I'm typing. Has anyone found a solution around that? I know Firefox somehow uses GTK, but how? Is the only solution to get a different web browser? If so, which one? Any help would be appreciated. Thanks a bunch!

---

### Post by crimesaucer on 2007-03-10
Go to Firefox-->--Edit-->--Preferences-->--Content-->--Colors-->-- and then "un-check" the box that says "Use System Color"

Try that.

Usually that fixes it everywhere to the font colors you have selected in Firefox. Black with White background.

It also changes the screen color to blank white page instead of a dark one.

I should maybe re-do the "How To" and explain that part better.

---

### Post by scigirl on 2007-03-10
Actually, I believe I didn't quite state the problem correctly. The solution you gave works, but only if you choose to not allow pages select their own colors. I guess my problem is that I'd like to let pages select their own color, I don't want to overwrite them with mine, so that for example gmail is nicely colored  as it is meant to be rather them just plain 4-colored scheme. So if i choose to check the option of allowing pages to select their own colors, everything works well except for buttons and text fields. So for example if I go to [www.google.com](www.google.com), it appears white as it should but the area where I must enter the search as well as the two submit buttons are dark with white font as my theme suggests. Would you happen to know of a way to let pages choose their color, and not use system color for buttons (the "use system colors" button is already un-cheked in my preferences). Thanks a bunch :)

---

### Post by crimesaucer on 2007-03-10
I know what you mean, all though if you uncheck it for "to not allow pages select their own colors", then sites get ugly fast.

Ubuntu is the only site that writes in a light unreadable text in the text box and I can't figure out why. My Berly forum doesn't do this, and neither does the Stumbleupon text areas.

I'm sure there are other sites with the text area done in a light font, but I haven't found one yet.

I'll try to fix this, but it is the reason I changed my style to a Dark Charcoal with black text and why I also have the other Black theme that makes mousepad use a white back ground so it has black text.

But then you lose the Black strips on the folder, and I like that part..

Would you like my other dark version gtkrc that has the white and green folder area in Thunar. It has readable text basically everywhere if you keep the "Use System Color" box unchecked. It is the one pictured above the all black theme that looks the same except the white/green parts.

---

### Post by crimesaucer on 2007-03-10
old theme Edited...

---

### Post by scigirl on 2007-03-10
Thanks for the quick replies - I really appreaciate your help :)
I see what you are suggesting here, but I guess I was looking for something that would actually keep my white on dark theme :\
I actually took your moonglow theme and modified it a bit to make it all dark without any green, and I love it because in general white on dark is much easier on my eyes (and it goes great with my desktop picture). I could try something else with a black font, but it just wouldn't be the same I guess. I really appreaciate your help though, I couldn't have done it so quickly and easily without your how-to :)
Here is what my firefox ends up looking as though:
[IMG]http://i95.photobucket.com/albums/l143/scigirl77/contrast.png[/IMG]
You can see how I made the theme up on top - it's all dark gray with white font. What bugs me are those dark text fields and buttons - they just look horrible on the white background. I guess this happens because firefox uses GTK buttons and text fields somehow, so I guess one of solution would be to find a different browser that doesn't do that. I'll post back if I figure it out :)

---

### Post by crimesaucer on 2007-03-11
Yeah, I see what you mean.

I always like the different color buttons and text boxes for google just because they match the url text boxes of my browser and the rest of my OS.

I just hate when I can't view the text when typing in a text area like this reply box for Ubuntu I'm typing in right now.

It's funny, your theme and the theme I just posted are like yin and yang. 

If I learn a new tip about being able to fix the text areas, I'll post it.

---

### Post by EML910 on 2007-03-13
Crimesaucer awesome themes. I to am new to Xubuntu and learned a lot from your posts. Do you know a code for blue text?

---

### Post by crimesaucer on 2007-03-14
Thank you, do you mean text for the mousepad, like for anything you type? 

I'll try to help if you explain what area you want to customize color-wise.

---

### Post by EML910 on 2007-03-15
I was thinking for anything that I typed.

---

### Post by ComplexNumber on 2007-03-15
> **scigirl said:**
> Thanks for the quick replies - I really appreaciate your help :)
I see what you are suggesting here, but I guess I was looking for something that would actually keep my white on dark theme :\
I actually took your moonglow theme and modified it a bit to make it all dark without any green, and I love it because in general white on dark is much easier on my eyes (and it goes great with my desktop picture). I could try something else with a black font, but it just wouldn't be the same I guess. I really appreaciate your help though, I couldn't have done it so quickly and easily without your how-to :)
Here is what my firefox ends up looking as though:
[IMG]http://i95.photobucket.com/albums/l143/scigirl77/contrast.png[/IMG]
You can see how I made the theme up on top - it's all dark gray with white font. What bugs me are those dark text fields and buttons - they just look horrible on the white background. I guess this happens because firefox uses GTK buttons and text fields somehow, so I guess one of solution would be to find a different browser that doesn't do that. I'll post back if I figure it out :)
don't make the base[NORMAL] so dark. another thing to remember with dark themes is NEVER have any font as  pure white. make it light grey instead. you will find that when you use firefox, some (white) fonts won't show up on the white background.




> **EML910 said:**
> Crimesaucer awesome themes. I to am new to Xubuntu and learned a lot from your posts. Do you know a code for blue text?
depends what shade of blue. if you use any application where there is the colour picker widget, that will tell you the code. personally, i use an application called gcolor.

---

### Post by crimesaucer on 2007-03-15
When writing it for the gtkrc for the xfce-engine, this would be the place for all "written" text:

text[NORMAL]      = Font color used for Mousepad, Firefox (web pages unless you un-check you "Use System Colors" in Firefox Preferences-->--Content-->--Colors), Url font, Thunar font (not selected), xubuntu menus (not selected). Checks for check boxes, radio dots too. Combobox, ComboBoxEntry, GtkCombo, GtkEntry, and numbers in numberbox.


Then if you want the Firefox Browser's menubar to have blue text, like where it says File, Edit, View...then this is where to put your blue text:


fg[NORMAL]        = This is the font color in the menu bars in FF and xubuntu, and also the color of the app in the pager that is open on a different Desktop.


As for the Dark background themes:

I noticed that as long as you have your, Firefox-->--Edit-->--Pref.-->--Content-->--Color-->--"Use System Color" un-checked....that you won't have white text in most pages (like Beryl forum). The exception is this Ubuntu Forum's text boxes, and maybe other Forum Text areas that are similar to this one. Then it gets really difficult to see. 

So using a light gray or off-white, or some other lighter color like my light green, is a good idea so if you run into one of those pages where it doesn't work, then at least you can still see the light text a little bit.

But this is one of the reasons, that after the Black and Green one, that I mostly do themes that use #000000 for the text[normal], like the last gtkrc I posted called Xfce-rusty_milk.

I spend too much time on this Ubuntu forum to be squinting at light text like the black and green one.

And for anybody else that's interested in any of my gtkrc themes, I have 6 of them posted in the Ubuntu Gallery and also at Deviant Art in the XFce section and the Firefox section. They all have the gtkrc posted with the screenshot.

---

### Post by theadventuresofanidealist on 2007-04-20
i have a question: where can i find the font in the xfce-rustsy_milk theme, the window title font?

---

### Post by crimesaucer on 2007-04-21
I had originally gotten it from here: [http://www.dafont.com/sg06.font](http://www.dafont.com/sg06.font)

but I also saw it here: [http://www.urbanfonts.com/fonts/SHAKAGRAPHICS_06.htm](http://www.urbanfonts.com/fonts/SHAKAGRAPHICS_06.htm)

---

### Post by AJB2K3 on 2007-04-22
If anyones interested i started several GTK theme pages on wikipedia based on 1.0>1.5 gimp and with most of it still usable im looking for contribitors to make it better.

---

### Post by crimesaucer on 2007-04-22
Do you have a link to it?

---

### Post by theadventuresofanidealist on 2007-04-23
thank you beryl much!

---

### Post by twodogs on 2007-04-24
this is an awesome find!!  i can't wait to start creating.   i just installed xubuntu and cant wait to wreck it...lol.  i will post any thing i create that is good.  just wondering, is it possible to use images for backgrounds in the menus, buttons, etc?

crimesaucer you rock!

TwoDogS out!

---

### Post by crimesaucer on 2007-04-24
Yes it's possible for certain engines (I'm not sure if xfce-engines can use images?), I just haven't tried yet. I've seen themes use custom buttons and panels that way.

I've looked for details on how to do it and haven't found any yet. If you learn how or find a guide on how to do it, please post it here.


Also, if you go to gnome-looks.org or xfce-looks.org, and look for certain themes that use images for buttons and panels, then you can download the theme, and see where and how they wrote the theme's gtkrc to include images.

The  theme's gtk-2.0 folder will come with the images it uses, and when you look at the files that come with it, you can search for every image that was included and find out where it was written in the file to see where they used it and how.

Then you can download a few more themes and compare them to learn.

---

### Post by crimesaucer on 2007-04-27
(Edit- this theme below uses my newest theme style like my edited post in the top thread)

This is my latest theme that I wrote. I basically changed the gradients of one of my earlier ones so it would look better in the file system and synaptic, and then I also wrote a Firefox userChrome.css to make it look correct in Firefox and I made an image for a new tabbar to be used.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-33-7.png[/IMG]

This is xubuntu Feisty running Firefox 2.0.0.3, Thunderbird 2.0, Synaptic, and Thunar.

Firefox and Thunderbird are set to default classic (no used theme) so they are using my gtkrc theme and a tabbar from my userChrome.css file.

---

### Post by crimesaucer on 2007-04-28
This is a link to my newest theme at xfce-look.org: [http://www.xfce-look.org/content/show.php/Xfce-milk?content=57138](http://www.xfce-look.org/content/show.php/Xfce-milk?content=57138)

It includes the Emerald theme, and a userChrome.css for Firefox to look good.

---

### Post by crimesaucer on 2007-05-04
Another updated version of the my newer style-

This is Firefox and Thunderbird 2 using the default themes that use my gtkrc theme, all that's needed is a simple userChrome.css with a small image for the tab-bar:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64-3.png[/IMG]

Exaile! and Thunar:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-66-3.png[/IMG]

---

### Post by eladner on 2007-06-13
"gtkrc" question for somebody out there.  It's driving me crazy.

On a gtkrc theme I've got - it's a darker theme - the inactive menu items and text in inactive windows seem to have a white drop shadow offset 1 pixel in x and 1 pixel in y that makes the text look really bad.  The normal menu items are around #808080 and the inactive menu items are around #303030 and with that white offset behind them, they look really funky.

Here's an image as an example...

[IMG]http://www.goldinc.com/~eladner/example.png[/IMG]

Any ideas on how to tweak that?

---

### Post by leibowitz on 2007-06-15
Maybe it's in the theme engine code, hard coded. Or maybe you can switch that in the gtkrc

But we need to know which theme are you using ?

Paste the gtkrc aswell if possible

---

### Post by crimesaucer on 2007-06-15
That's a difficult one, I know that the font is fg[INSENSITIVE] for the text that can't be clicked in the drop down menus. As for the background color of it, I don't know how to fix that white color...I have a problem with it on all of my dark themes also. It is mostly in my Thuar file system.

I couldn't change it using any of the hex color codes in the gtkrc for xfce...I think it has something to do with the default widgets and how they are in Linux and the theme engine. It is that way for insensitive toogle buttons also, and insensitive radio and check buttons too.

---

### Post by crimesaucer on 2007-06-15
This is my newest:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-123-3.png[/IMG]

---these are some of my new changes that I use now---


Go to your theme's gtkrc (the file inside of /usr/share/themes/Xfce-theme_name/gtk-2.0)


In the style "default" section, I make sure my x and y thickness = 0, so I have no dividing lines and so my calendar looks better

```

xthickness = 0
ythickness = 0

```

then to fix the gradient box fill, this is what I do:

```

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.10 
            shade_end = 1.00
        }
    }
}
 
widget_class "*" style "default"


``` 

This is the widget_class "*" style "default" part at the very top underneath the hex color codes for the default style.

The "shade_start = 1.10"  is the top of the toolbar, "1.10" is lighter than "1.00" (the "bg[NORMAL]" hex code color), and the "shade_end = 1.00" is the bottom of the toolbar, where the Firefox tab-bar starts. Having it at "1.00" will make it fade evenly into the rest of the app that is using the "bg[NORMAL]" color. 

Now...for the menubar, you go to this part of your gtkrc:

```

style "menubar" = "colored"
{
    xthickness = 1
    ythickness = 0

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            
            fill_style = gradient
            orientation = vertical
            shade_start = 1.20
            shade_end = 1.10
        }
    }
}

widget_class "*BonoboDockItem"     style "menubar"
class "*BonoboDockItem"            style "menubar"
widget_class "*HandleBox"          style "menubar"
class "*HandleBox"                 style "menubar"
widget_class "*ToolBar"            style "menubar"
class "*ToolBar"                   style "menubar"
widget_class "*MenuBar"            style "menubar"
class "*MenuBar"                   style "menubar"


```

...and you make the "shade_end = 1.10" (which is the bottom of the menubar),to match the top of your toolbar that was "1.10" also...

then you make the "shade_start = 1.20" which is the top of the menu bar.

Now...the most important number of those 4 is the toolbar's "shade_end = 1.00", because that makes everything smooth...you can either theme lighter or darker by going up to "1.10" or darker to "0.90".

...you have to mess with the numbers a bit to get it perfect.   

....This works properly for all apps except Firefox, AbiWord, and Gnumeric SpreadSheet...

AbiWord and Gnumeric still look good, it's just not as smooth as the rest of my apps in xubuntu...

For Firefox 2.0.0.4, I now use a userChrome.css to add a new tab-bar image. That fixes the ugly Firefox gradient tab-bar. I do it the exact size so everything like the tabs work perfectly.

... for the Firefox userChrome.css, I add this part onto my userChrome.css in my /home/name/.mozilla/firefox/profile.default/chrome folder  --- I also add the tabstrip.png image in that same directory.

```

#browser tabs {
    -moz-appearance: none !important;
    background-color: none !important;
    background: url("tabstrip-10.png") repeat-x top !important;
    height: 25px;
    padding: 0px;
    border: 0px;
    margin: 0px;
    }  

```



Next up is the icons, they are from the old Firefox 1.5 theme named "Glassier", and they have been substituted into the /usr/lib/firefox/chrome/classic/skin/classic/browser folder....it is the Toolbar.png
I had to fix them in GIMP to work for Firefox2 since it was an old theme...I also made them a lighter blue in GIMP. You can use any icons that are 24x24 pixels, and in the correct order and number of the default Toolbar.png icons, the whole image should be in the order below and this exact size: 336x120

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Toolbar.png[/IMG]



My bottom panel was made in the GIMP, and I used a .gtkrc-2.0 file to make it. This is the one that I use now, and I have it in my /home/name directory:

```

style "panel"
{
  bg[NORMAL] = "#E9B9D3"
  bg_pixmap[NORMAL] = "panel89.png"
  fg[NORMAL] = "#000000"
  }

widget_class "*Panel*"      style "panel"
widget "*Panel*"            style "panel"
class "*Panel*"             style "panel"



```


For Thunderbird2, I use userChrome.css to add new icons, change the text-color of unread messages, and selected unread messages, and I even add a nice little menu bar image....

For the icons, they must be in the correct order of the mail-toolbar.png and must be in this same order below:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/mail-toolbar.png[/IMG]

The default size is 24x24 pixels, and the whole mail-toolbar.png image is 408x72 pixels

For my current theme I use a scaled down, and re-ordered "AquaBird Redone" by Bodizzle

This is my Thunderbird2 userChrome.css, it's located in my /profile.default/chrome, (mine is in this directory: /home/name/.thunderbird/l6hw7hh0.default/chrome ....yours might be in a different place):

```

@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/* Change the text color of unread messages to
* any color of your liking - just change the hex value shown here. */
treechildren::-moz-tree-cell-text(unread) {
color: #F0F2E7 !important;
}


/* Change the text color of selected unread messages to
* any color of your liking - just change the hex value shown here. */
treechildren::-moz-tree-cell-text(unread, selected) {
color: #000000 !important;
}

/* Use a background image for the toolbars:
(Substitute your image file for background.gif) */

/* Add a menubar image */
menubar{
background-image: url("bluefawnNEW-sm.png") !important;
background-color: none !important;
}

/*toolbar icons*/
.toolbarbutton-1 {
  -moz-box-orient: vertical;
  list-style-image: url("mail-toolbar.png") !important;
}

```


...That's it...as well as a GIMP made touch-up of a !!!Dalek!!! picture for my Terminal so it would blend into my Gradient gtk-2.0 theme. What I do is to create a gradient color layer and match it to my bg[NORMAL] color that is the color that the gradient toolbar uses at "1.00"

---

### Post by Irti on 2007-06-18
hey crimesaucer............i was wondering if you could help me a bit with theming.......first i would want you to check out this mockup.....    [http://ubuntuforums.org/showthread.php?t=437694&highlight=beryl+plugins    ...would](http://ubuntuforums.org/showthread.php?t=437694&highlight=beryl+plugins    ...would) you mind making one like that........just a request.........and i was wondering if you could tell me some thing about this...........

#include "panel/panel.rc"

style "clearlooks-default"
{
  GtkButton      ::default_border    = { 0, 0, 0, 0 }
  GtkRange       ::trough_border     = 0
  GtkPaned       ::handle_size       = 6
  GtkRange       ::slider_width      = 15
  GtkRange       ::stepper_size      = 15

  GtkScrollbar   ::min_slider_length = 30
  GtkCheckButton ::indicator_size    = 14
  GtkMenuBar     ::internal-padding  = 0
  GtkTreeView    ::expander_size     = 14
  GtkExpander    ::expander_size     = 16
  GtkScale       ::slider-length     = 27
  #GtkToolbar     ::button-relief     = GTK_RELIEF_NORMAL
  #GtkMenuBar     ::shadow-type       = GTK_SHADOW_OUT
  #GtkScrollbar   ::has-secondary-forward-stepper = 1
  #GtkScrollbar   ::has-secondary-backward-stepper = 1

  GtkButton      ::child-displacement-x = 1
  GtkButton      ::child-displacement-y = 1

  GtkMenu        ::horizontal_padding = 0
  GtkMenu        ::vertical_padding = 0

  WnckTasklist   ::fade-overlay-rect = 0

  xthickness = 1
  ythickness = 1


 [COLOR="Red"] fg[NORMAL]        = @fg_color #"#000000" # black
  fg[PRELIGHT]      = @fg_color #"#000000" # black
  fg[SELECTED]      = @selected_fg_color #"#ffffff" # white 
  fg[ACTIVE]        = @fg_color #"#000000" # black
  fg[INSENSITIVE]   = darker (@bg_color) #"#b5b3ac" # dark beige

  bg[NORMAL]        = @bg_color # "#ede9e3"
  bg[PRELIGHT]      = shade (1.02, @bg_color) #"#f9f7f3" # very light beige
  bg[SELECTED]	    = @selected_bg_color # "#5598d7" # deepsky
  bg[INSENSITIVE]   = @bg_color # "#efebe5" # beige
  bg[ACTIVE]        = shade (0.9, @bg_color) #"#dcd4c9" #"#d7d3ca" # dark beige

  base[NORMAL]      = @base_color # "#ffffff" # white 
  base[PRELIGHT]    = shade (0.95, @bg_color) # "#5f8ec4" # dark beige
  base[ACTIVE]      = shade (0.9, @selected_bg_color) # "#a69f91" # darker deepsky
  base[SELECTED]    = @selected_bg_color # "#5598d7" # deepsky
  base[INSENSITIVE] = @bg_color # "#e8e5de" # beige

  text[NORMAL]      = @text_color # "#000000" # black
  text[PRELIGHT]    = @text_color # "#000000" # black
  text[ACTIVE]      = @selected_fg_color # "#ffffff" # white
  text[SELECTED]    = @selected_fg_color # "#ffffff" # white
  text[INSENSITIVE] = darker (@bg_color) # "#b5b3ac" # dark beige
[/COLOR]
  engine "clearlooks" 
  {
    #scrollbar_color   = "#76acde"
    [COLOR="Red"]menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradien[/COLOR]t
    animation         = TRUE
    [COLOR="Red"]style             = GLOSSY[/COLOR]
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
  bg[NORMAL]        = shade (1.05, @bg_color) # "#f6f4f1"
  bg[INSENSITIVE]   = shade (1.04, @bg_color) # "#f2efeb"
  bg[PRELIGHT]      = shade (1.08, @bg_color) # "#faf9f8"
}

style "clearlooks-notebook" = "clearlooks-wide"
{
#  bg[NORMAL]      = "#efebe5"
#  bg[INSENSITIVE] = "#efebe5"
}

style "clearlooks-tasklist" = "clearlooks-default"
{
  xthickness = 5
  ythickness = 3
}

style "clearlooks-menu" = "clearlooks-default"
{
  xthickness = 0
  ythickness = 0
  bg[NORMAL] = shade (1.08, @bg_color) # "#f9f7f3"
}

style "clearlooks-menubar-item" = "clearlooks-button"
{
#    fg[PRELIGHT] = "#000000"
}

style "clearlooks-menu-item" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 3
  fg[PRELIGHT] = @selected_fg_color
}

style "clearlooks-tree" = "clearlooks-default"
{
  xthickness = 2
  ythickness = 2
}

style "clearlooks-frame-title" = "clearlooks-default"
{
  fg[NORMAL] = lighter (@fg_color) # "#404040"
}

style "clearlooks-tooltips" = "clearlooks-default"
{
  xthickness = 4
  ythickness = 4
  bg[NORMAL] = { 1.0,1.0,0.75 }
}

style "clearlooks-progressbar" = "clearlooks-wide"
{
  xthickness = 1
  ythickness = 1
  # fg[PRELIGHT]  = "#ffffff"
}

style "clearlooks-combo" = "clearlooks-button"
{
}

style "clearlooks-menubar" = "blackrock-default"
{
#  bg[NORMAL]   = "#bacedb"
}

style "clearlooks-scale" = "clearooks-button"
{
	GtkRange::trough-side-details = 1
}	

#style "panel" {
#  	bg_pixmap[NORMAL] = "panel.png"
#}

# widget styles
class "GtkWidget"    style "clearlooks-default"
class "GtkButton"    style "clearlooks-button"
class "GtkScale"     style "clearlooks-scale"
class "GtkCombo"     style "clearlooks-button"
class "GtkRange"     style "clearlooks-wide"
class "GtkFrame"     style "clearlooks-wide"
class "GtkSeparator" style "clearlooks-wide"
class "GtkMenu"      style "clearlooks-menu"
class "GtkEntry"     style "clearlooks-wider"
class "GtkMenuItem"    style "clearlooks-menu-item"
class "GtkNotebook"    style "clearlooks-notebook"
class "GtkProgressBar" style "clearlooks-progressbar"
#class "Panel*" 		style "panel"
#class "GtkMenuBar" style "clearlooks-menubar"

widget_class "*MenuItem.*" style "clearlooks-menu-item"
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




in the menu bar style where the effects are given.....what all effects can we use over there............and how do we change the color of the window menubar..........is there a way to change the background color of fonts on the dektop.(my fonts are black and there is a white background around it which looks kinda irritating)..........and how can i change the color of the dropdown menus and all...............i see you did some crazy stuff with the themes man...looks great..............

---

### Post by crimesaucer on 2007-06-18
I'll have to play around with clear looks for a while...I have only been using the xfce engine for themes because I thought it would work best with my xubuntu and xfce4.4

As for the mockup...It seems that all you would have to do would be to create a panel image for the top panel, and get a clear OSX dock for the bottom...other then that, it was just a picture of a nice wallpaper.

You could make a theme based on the color of the top panel...either with a bg[NORMAL] color of the top panel and a gradient, or a pix map image of the glossy look using a theme engine that uses pix maps...you would have to ask on the forum which theme engine uses pix map images best for toolbars and menubars...

But I will look into the clear looks engine since it is very popular in ubuntu...and I'll get back to you.


EDIT- I also don't think it is possible to have the Beryl Thumbnail views on a clear dock (?) or the pager (workspace switcher)...and I don't think the wifi is able to be put on a clear dock like that...it's a nice idea for a multi-purpose "transparent" dock...but I wouldn't know how to make it.

---

### Post by kpolice on 2007-06-18
@irti

Anything like @fg_color or @bg_color are symbolic colors used in the latest gtk and the purpose of this is to recolor a theme easily. Usually you define the colors on the top of your gtkrc file only once so if you wan't to change something is easier and also to use the new customize option in GNOME 2.18 

You should check the gtkrc file from Clearlooks on the latest GNOME. 

The menubarstyle is an option from Clearlooks, the name says it all.

Finally the STYLE is also a Clerlooks property, in the svn version of Clearlooks (I don't know if it's the same for 2.18 ) you have CLASSIC, GLOSSY and GUMMY, btw Cimi is doing a great job with them.

---

### Post by crimesaucer on 2007-06-19
I just wanted to say that I edited my first post on page one so that it explains my new theme style better.

I also tried to make it easier to read.

...and I wish people would post similar gtkrc descriptions for different theme engines, since xfce isn't the most popular theme engine out there, and it's the only theme engine that I know a bit about...so I wouldn't mind learning something new, and I'm sure it would help people that use other theme engines.

Also...any Firefox/Thunderbird userChrome.css tips or other forms of eye candy tips are appreciated.

---

### Post by Irti on 2007-06-19
@ crimesaucer..seriously i would be glad to see a similar description for the clearlooks engine.......i tried out the xfce...but it didnt seem to work on ubuntu.....i mean i made some changes and all and tried to apply the new theme after saving the gtkrc file..but it made no difference... :-k ...anyways it would be really nice seeing that mockup on an ubuntu though............

@ kpolice....thanx i got a general idea of the stuff........am still trying to make it work though  :-P

edit .... @ crimesaucer..........i can post all the gtkrc files of wateva theme engines you want dude.....just keep up the gud work.!!! =D>

---

### Post by kpolice on 2007-06-19
Tutorial
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

### Post by crimesaucer on 2007-06-19
> **kpolice said:**
> Tutorial
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

Thanks, I actually found that guide after I had learned all of those things on my own, I like how it's written but it doesn't go into enough detail about the unique things...like this part:

> 
Engines

/!\ Hmm, I am not entirely happy with this section. While I think that there is not much it should cover, this feels like it is too little.

As said earlier, engines are used to define the look and extend the styles. For example to use the Clearlooks engine, you can just do the following.

style "some-style" {
        engine "clearlooks" {
                # engine specific settings go here
        }
}

This means the Clearlooks engine will be used with its default settings. You can modify engine settings in the block. For a description of the possible options for different engines please refere to their documentation at ../GtkEngines.




...the "engine specific settings" are what I want the most and I can never find any detail on it form any page, including the links on that site.


For example, I learned about a gradient boxfill from playing with the Xfce-winter gtkrc, and then I started trying to add a gradient boxfill to different style specific settings, and it worked out beautifully...now I wish I could learn more about other engine specific settings for xfce and other themes engines...

I also would love to learn a bit more about this area:

```

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
    GtkScrollbar::min_slider_length   = 37
    GtkToolbar::shadow_type           = out
    GtkWidget::focus-line-width       = 1
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0


```

I know about the:
GtkScrollbar::min_slider_length   = 37
GtkRadioButton::indicator_size    = 15
GtkRange::slider_width            = 15
GtkRange::stepper_size            = 15
GtkRange::stepper_spacing         = 0
...and the shadow types

...but I wish there was more charts to the different settings for sizes and shapes...I also wish there were was more of a breakdown of how to write all of the possibilities of a certain theme engine to utilize all of the different buttons and ways to draw them...rounded corners, square, gradients, sunken....

---

### Post by kpolice on 2007-06-19
The properties on the code you posted have descriptions on the tutorial and also in the GTK documentation.

To get the engine specific details just check the default themes that come with it because most of the time the settings are there and are self explanatory, you can also check the source code.

For example Clearlooks:
```
    colorize_scrollbar = FALSE
    menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    animation         = FALSE
    style             = CLASSIC
    radius            = 3.0
```

If you check the Gummy, Glossy and Inverted themes (which are Clearlooks) you will see the difference between them. 

Murrine has a complete description of each setting on Cimi's site.

---

### Post by crimesaucer on 2007-06-19
> **kpolice said:**
> The properties on the code you posted have descriptions on the tutorial and also in the GTK documentation.

To get the engine specific details just check the default themes that come with it because most of the time the settings are there and are self explanatory, you can also check the source code.

For example Clearlooks:
```
    colorize_scrollbar = FALSE
    menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    animation         = FALSE
    style             = CLASSIC
    radius            = 3.0
```

If you check the Gummy, Glossy and Inverted themes (which are Clearlooks) you will see the difference between them. 

Murrine has a complete description of each setting on Cimi's site.

The xfce link does not work...for the GtkEngines...and less than half of those links work...I liked the one for the Smooth GTK engine: [http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/SmoothEngine](http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/SmoothEngine)

and yes, I like how some themes like the clear looks gtkrc include the possible settings, but I always wonder if there are more possible...Like that scrollbar:

```

colorize_scrollbar = FALSE
    menubarstyle      = 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    animation         = FALSE
    style             = CLASSIC
    radius            = 3.0

```

I wonder what TRUE would do and what other styles can be written besides CLASSIC?


When using xfce, I was lucky to find all of the extra possibilities on my xfce theme, with out any tips included in the gtkrc, and from just trying things to see if certain things worked...some themes on Gnome-Looks.org and Xfce-Looks.org have well written gtkrc's that explain a few things...but a lot don't.

...I just think there should be a site with every theme engine known to Linux, with a chart for each of them and the different settings for each widget...and the possibilities of gradient or shade boxfills or use of pix map images....

...also can you link me to the Murrine page you were talking about, that was the next theme engine I was going to try and use because I like the buttons...thanks.

---

### Post by kpolice on 2007-06-19
The style properties like 
```
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 10
```

aren't engine specific, all of them are gtk properties so they apply to any engine.

About the murrine engine
[http://cimi.netsons.org/pages/murrine/options.php](http://cimi.netsons.org/pages/murrine/options.php)

---

### Post by crimesaucer on 2007-06-19
> **kpolice said:**
> The style properties like 
```
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 10
```

aren't engine specific, all of them are gtk properties so they apply to any engine.

About the murrine engine
[http://cimi.netsons.org/pages/murrine/options.php](http://cimi.netsons.org/pages/murrine/options.php)

Yeah, I hadn't messed with any of that because I was happy with my buttons...but I would guess that is a style default that I could change and see the results...and use my trial and error method to find a unique style that I am happy with...

Thanks for the link...and I also edited my post above to explain a point a bit further so check it out...

---

### Post by Irti on 2007-06-19
these are some effects that i found in the Gnomesmooth -green theme ........ they basically use the smooth engine........i hope its usefull...........

style "vscrollbar" 
{
	engine "smooth" {
		fill
		{
			style = shaded
			hdirection = vertical
			vdirection = horizontal
			shade1 = 1.05
			shade2 = 0.95

and


style "hscrollbar" 
{
	engine "smooth" {
		fill
		{
			style = shaded
			hdirection = vertical
			vdirection = horizontal
			shade1 = 1.05
			shade2 = 0.95
		}
	
		line
		{
			style = smooth
			thickness = 1
		}
	
		trough
		{
			fill
			{
				style = solid
			}
		}
	
		grip
		{
			style = dots_in
			count = 3
			spacing = 2
		}

		focus
		{
			foreground[ACTIVE] = "#83A67F"
			foreground[SELECTED] = "#83A67F"
			foreground[NORMAL] = "#83A67F"
			foreground[PRELIGHT] = "#83A67F"
		}
	
		arrow
		{
			style = cleanice
			solid = TRUE
			xpadding = 1
			ypadding = 1

			INSENSITIVE
			{
				etched = TRUE
			}
		}
	}
}

---

### Post by Irti on 2007-06-19
you also mentioned in your first post in this thread that 


bg[NORMAL] = This is the overall color of the Browser for Firefox, xubuntu/ubuntu, Thunderbird, and all apps. It creates the color that is used for my gradient browser themes. It is also all of the buttons, scroll bar handles, panel handle, Drop down menus (before you roll over them with the mouse tool tip).

i wonder if there is a way to use seperate colors for windows from the menus ....and you know seperate the colors of the buttons from panel handles and all...??

---

### Post by kpolice on 2007-06-19
If you read the tutorial you will understand how it works and how to apply different styles to different widgets.

---

### Post by crimesaucer on 2007-06-19
I find the best thing to do is to just try every idea you have, along with reading my tutorial, his link to the GTK tutorial, the tips on different gtkrc files and what ever else you find about themes...

...If it doesn't work, it either won't show, or it will cause your theme to go to the default gray and blue...or if you really screw things up....you can always find a way to fix it.

---

### Post by crimesaucer on 2007-06-20
A new variation that I made a bit tighter:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-8.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-5-8.png[/IMG]

---

### Post by ceil420 on 2007-06-30
Hi. I got a few questions (mainly regarding the secret identity of a couple of classes/widgets/whatever). First, an image of the Work In Progress itself:

[IMG]http://img402.imageshack.us/img402/773/sativagtkhelpmewi3.png[/IMG]

And now my questions (which corrospond to the arrows):

#1: The titlebar is definitely changing. A lot. That was a concept piece. No need for insults. That's not the point of this post.

#2: What is this class/widget_class called? I can't figure it out, and any time I try something for it (like "*Combo*" or "*Box*"), something changes that I don't want to.

#3: Same question/issue as #2. I'd like the drop-down arrow thing to be the same shape/style as the one below it ("GtkCombo"), but don't know which class/widget to fit the style to.

And a question that can't be shown in that picture: Does anyone know if there's a comprehensive guide to everything that can go between the **engine "xfce"** brackets? Reading this thread, it seems that most people are eager to learn about the other engines. Well, I'd like to stick proudly by little Xerry (that's what I call the mouse; heard it called that in [IRC]("irc://irc.freenode.net/xfce") once), and just milk the Xfce engine for all it's work. A google of *xfce theme engine boxfill smooth_edge* (I figured some of the 'parts' would help get more results) led me here, yet sadly after five pages I remain unanswered.

Thanks for thoughts/answers o/

(By the way, I've seen some groovie themes here, guys, keep it up! (And not a Vista/Mac look in the lot of 'em ^^))

Edit: Thought I'd stick my gtkrc so far in here:

```
style "default"
{

# Gtk widgetry


# Modify the X/Y thickness
  xthickness = 0
  ythickness = 0

# Set the background,foreground, text, and base colours
  bg[NORMAL]		= "#009900"	# The normal colour.
  bg[PRELIGHT]		= "#00c300"	# "On hover".
  bg[ACTIVE]		= "#00ed00"	# When a button is pressed.
  bg[INSENSITIVE]	= "#008000"	# Disabled widget.
  bg[SELECTED]		= "#00ff00"	# When text is selected.
  fg[NORMAL]		= "#17fc00"
  fg[PRELIGHT]		= "#ac3600"
  fg[ACTIVE]		= "#ff5151"
  fg[INSENSITIVE]	= "#008000"
  fg[SELECTED]		= "#000000"
  text[NORMAL]		= "#00dc00"
  text[PRELIGHT]	= "#00ff00"
  text[ACTIVE]		= "#00ff99"
  text[INSENSITIVE]	= "#008000"
  text[SELECTED]	= "#000000"
  base[NORMAL]		= "#008000"
  base[PRELIGHT]	= "#ff6e6e"
  base[ACTIVE]		= "#ff6e6e"
  base[INSENSITIVE]	= "#a84848"
  base[SELECTED]	= "#ffb66e"

}

style "testing"
{

  xthickness = 0
  ythickness = 0

  bg[NORMAL]	= "#000000"
  fg[NORMAL]	= "#000000"
  text[NORMAL]	= "#000000"
  base[NORMAL]	= "#000000"

  engine "xfce"
  {
    smooth_edge = true
  }

}

style "scrollbar" = "default"
{

  xthickness = 0
  ythickness = 1

  engine "xfce" 
  {
     grip_style = smooth
     smooth_edge = true
     boxfill
     {
         fill_style = gradient
         orientation = auto
         shade_start = 1.13
         shade_end = 0.87
     }
  }

}

style "menubar" = "default"
{

  xthickness = 0
  ythickness = 0

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 0.92
      shade_end = 1.00
    }
  }
}

style "menuitem" = "default"
{

  fg[NORMAL]	= "#fc1700"
  fg[ACTIVE]	= "#51ff51"
  fg[SELECTED]	= "#ff0000"

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 1.00
      shade_end = 0.87
    }
  }
}

style "button" = "default"
{

  xthickness = 1
  ythickness = 1

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 1.10
      shade_end = 0.95
    }
  }
}

style "check" = "default"
{

  text[NORMAL]		= "#00ff00"
  fg[NORMAL]		= "#00dc00"
  fg[PRELIGHT]		= "#a300a3"
  fg[ACTIVE]		= "#80ff80"
  fg[SELECTED]		= "#32ff32"
  fg[INSENSITIVE]	= "#008000"
  base[NORMAL]		= "#ff0000"
  base[PRELIGHT]	= "#ff6e6e"
  base[ACTIVE]		= "#ff6e6e"
  base[INSENSITIVE]	= "#a84848"
  base[SELECTED]	= "#ffb66e"

}

style "titlebar" = "default"
{

  bg[SELECTED]		= "#00ac00"
  bg[INSENSITIVE]	= "#008000"
  fg[SELECTED]		= "#ff0000"
  fg[INSENSITIVE]	= "#800000"
}

style "panel" = "default"
{

  xthickness = 0
  ythickness = 0

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 0.83
      shade_end = 1.13
    }
  }
}

widget_class "*"		style "default"

widget_class "*Button*"		style "button"
class "*Button*"		style "button"
widget_class "*button*"		style "button"
class "*button*"		style "button"
widget_class "*OptionMenu*"	style "button"
class "*OptionMenu*"		style "button"
widget_class "*Tree*"		style "button"
class "*Tree*"			style "button"
widget_class "*GtkScale*"	style "button"
class "*GtkScale*"		style "button"

widget_class "*Panel*"		style "panel"
class "*Panel*"			style "panel"

widget_class "*CheckButton*"	style "check"
class "*CheckButton*"		style "check"
widget_class "*RadioButton*"	style "check"
class "*RadioButton*"		style "check"

widget_class "*List*"		style "default"
class "*List*"			style "default"
widget_class "*Text*"		style "check"
class "*Text*"			style "check"
widget_class "*Entry*"		style "check"	# Drop down list/Editbox
class "*Entry*"			style "check"
widget_class "*ComboBox*"	style "check"
class "*ComboBox*"		style "check"

widget_class "*MenuBar"		style "menubar"
class "*MenuBar"		style "menubar"
widget_class "*ToolBar"		style "menubar"
class "*ToolBar"		style "menubar"
widget_class "*BonoboDockItem"	style "menubar"
class "*BonoboDockItem"		style "menubar"
widget_class "*HandleBox"	style "menubar"
class "*HandleBox"		style "menubar"

widget_class "*MenuItem*"	style "menuitem"
class "*MenuItem*"		style "menuitem"

widget_class "*Scrollbar*"	style "scrollbar"
class "*Scrollbar*"		style "scrollbar"
widget_class "*GtkProgress*"	style "scrollbar"
class "*GtkProgress*"		style "scrollbar"

widget "xfwm"			style "titlebar"
class "MetaFrames"		style "titlebar"
widget_class "MetaFrames"	style "titlebar"
```

(Like I said, it's a Work In Progress)

---

### Post by crimesaucer on 2007-07-02
Hello, I'll try to help...but remember, I'm a beginner also...

For #1, can you explain how it's "changing"...and I don't insult people so don't worry, and I hope others don't insult me either if I do something wrong.

Constructive criticism is a much better way to learn.

As for the colors of the title bar:

```

style "titlebar" = "default"
{
    bg[SELECTED]      = "background color of open window"
    fg[SELECTED]      =  "title text color of open window"
    bg[INSENSITIVE]   = "background color of the windows that are behind the open window"
    fg[INSENSITIVE]   =  "title text color of the windows behind the open window (doesn't change the closing buttons of the xfwm pixmap theme...you must change your xfwm window theme for that)"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 

```

...you might want to change the details of your xfwm theme: [http://wiki.xfce.org/xfwm4_theme_howto](http://wiki.xfce.org/xfwm4_theme_howto)


for #2, that is a good question, as the names on "thewidgetfactory" are: ComboBox and ComboBoxEntry...but they aren't in my gtkrc, or any Xfce gtkrc that I have looked at.

I know that I make the ComboBox match with this part of my gtkrc:

```

style "colored" = "default"
{
    xthickness = 2  #  Affects the Thunar Path Box as well as other things.
    ythickness = 2  #  Affects the Thunar Path Box as well as other things.

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
            fill_style = gradient    
            orientation = vertical    
            shade_start = 1.24        
            shade_end = 0.83          

# I changed the "fill_style = plain", to  "= gradient" for the rollover buttons.
# It affects drop down menus in Firefox, and other menus. I chose "orientation = vertical"
# try "orientation = auto" and see if you like it.   
# auto will draw the gradient sideways sometimes. 
# Also mess with the "shade_start" percentage numbers 
# and the "shade_end" percentage numbers for different affects.

	}                             
    }
}

widget_class "*List*"              style "colored"
class "*List*"                     style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"


```


and for #3, I don't know how to change the size of the arrow, and it seems that way in most Xfce themes also. 


All I know how to do is change the colors of the arrows and the backgrounds of it...and that is in that section above...in the: style "colored" = "default" 

and I think you know that part good because all of your colors match....



....as for your 4:20 theme, I can tell your close button is a weed leaf, and your minimize button is a bowl, but what is your middle button on the right? Is it a heart?

---

### Post by ceil420 on 2007-07-02
> **crimesaucer said:**
> Hello, I'll try to help...but remember, I'm a beginner also...

For #1, can you explain how it's "changing"...and I don't insult people so don't worry, and I hope others don't insult me either if I do something wrong.

for #2, that is a good question, as the names on "thewidgetfactory" are: ComboBox and ComboBoxEntry...but they aren't in my gtkrc, or any Xfce gtkrc that I have looked at.

I know that I make the ComboBox match with this part of my gtkrc:

[CODE/CODE]

and for #3, I don't know how to change the size of the arrow, and it seems that way in most Xfce themes also. 

All I know how to do is change the colors of the arrows and the backgrounds of it...and that is in that section above...in the: style "colored" = "default" 

and I think you know that part good because all of your colors match....

....as for your 4:20 theme, I can tell your close button is a weed leaf, and your minimize button is a bowl, but what is your middle button on the right? Is it a heart?

For #1, when I posted about it, I meant to imply that I didn't need help with it :x Xfwm4 is easy (i love bringing ascii art to life with .xpm files :D), it's the gtkrc part I was havin' problems with.

For #2, You're right, and after much tweakery, I discovered how to do it :)

For #3, Damn. It'd be nice to set those buttons to be the same size.

And the maximize button is a very poorly done hookah :p (the shade button turned into a peace sign in the final version, and the minimize button is now a standing joint that's easier to click; all the buttons got rasta-fied to Red, Yellow, and Green ;) )

While your response is much appreciated, I learned a lot between the time of this writing and the time of my last; having completed the "Sativa" theme, and nearly finished another, which I'll post here (along with it's gtkrc file; I can post the xfwm4 files if someone *really* wants them), based on Final Fantasy VII. I made the desktop back in my Windows days on Photoshop CS2 (man I miss that program), using a still from the Advent Chidlren movie and a custom feather brush with various effects that I wish I could easily duplicate in the GIMP :x

[IMG]http://img233.imageshack.us/img233/7110/desktop02julyoz0.png[/IMG]

The theme's only like 85% done, I'd say; I thought it was complete until I saw it outside of TheWidgetFactory (excellent program, that). I'm not too happy with the browns I put in it; I'll post a better look at the theme itself when I do. But you can kinda see the buttons on my panel (those won't change), and everything important about the xfwm4 files is visible. I worked very hard scaling down various images (including my own personal seal for the "shade" button, and a feather from the desktop for "minimize"; that meteor "close" button is from the Final Fantasy VII logo itself) in the GIMP to 18x18 pixels, and then typing them up Mousepad, and picking colours straight out of the images (for the chocobo and meteor). Except for the chocobo, all the buttons use a gradient with the colours from the meteor; I just the drop of colour the chocobo adds to the titlebar :)

And here's the gtkrc file (like I said, those flesh tones are gonna change for the windows; they don't look bad as fonts):

```
# Colours (shades of white, blue, and flesh)
#
# FFFFFF F3E6DD
# F1EBF9 EAD8CB
# D4D4F8 D6BEAC
# C5BBED CAA990
# B7A1F4 BE9373
# 8080FF A77149
# 5050FF 92572B
# 0000FF 82481D

style "default"
{

  GtkRange::slider_width		= 14
  GtkRange::stepper_size		= 14
  GtkRange::stepper_spacing		= 2
  GtkRange::trough_border		= 0
  GtkScrollbar::min_slider_length	= 20
  GtkMenu::horizontal-padding		= 4
  GtkMenuItem::selected_shadow_type	= out
  GtkMenuItem::horizontal_padding	= 1
  GtkRadioButton::indicator_size	= 10
  GtkToolbar::shadow_type		= none
  GtkWidget::focus-line-width		= 0
  GtkNotebook::tab-curvature		= 5
  GtkNotebook::tab-overlap		= 3

  xthickness = 2
  ythickness = 2

  bg[NORMAL]		= "#FFFFFF"	# The normal colour.
  bg[PRELIGHT]		= "#F1EBF9"	# "On hover".
  bg[ACTIVE]		= "#C5BBED"	# When a button is pressed.
  bg[INSENSITIVE]	= "#D6BEAC"	# Disabled widget.
  bg[SELECTED]		= "#8080FF"	# When text is selected.
  fg[NORMAL]		= "#82481D"
  fg[PRELIGHT]		= "#BA9E89"
  fg[ACTIVE]		= "#A77149"
  fg[INSENSITIVE]	= "#5D4F44"
  fg[SELECTED]		= "#FFFFFF"
  text[NORMAL]		= "#92572B"
  text[PRELIGHT]	= "#82481D"
  text[ACTIVE]		= "#EAD8CB"
  text[INSENSITIVE]	= "#D6BEAC"
  text[SELECTED]	= "#FFFFFF"
  base[NORMAL]		= "#EAD8CB"
  base[PRELIGHT]	= "#F3E6DD"
  base[ACTIVE]		= "#D2B7A2"
  base[INSENSITIVE]	= "#A77149"
  base[SELECTED]	= "#A88E77"

}

style "testing"
{

  xthickness = 5
  ythickness = 5

#  bg[NORMAL]		= "#FFFFFF"	# The normal colour.
#  bg[PRELIGHT]		= "#FFFFFF"	# "On hover".
#  bg[ACTIVE]		= "#FFFFFF"	# When a button is pressed.
#  bg[INSENSITIVE]	= "#FFFFFF"	# Disabled widget.
#  bg[SELECTED]		= "#FFFFFF"	# When text is selected.
#  fg[NORMAL]		= "#FFFFFF"
#  fg[PRELIGHT]		= "#FFFFFF"
#  fg[ACTIVE]		= "#FFFFFF"
#  fg[INSENSITIVE]	= "#FFFFFF"
#  fg[SELECTED]		= "#FFFFFF"
#  text[NORMAL]		= "#FFFFFF"
#  text[PRELIGHT]	= "#FFFFFF"
#  text[ACTIVE]		= "#FFFFFF"
#  text[INSENSITIVE]	= "#FFFFFF"
#  text[SELECTED]	= "#FFFFFF"
#  base[NORMAL]		= "#FFFFFF"
#  base[PRELIGHT]	= "#FFFFFF"
#  base[ACTIVE]		= "#FFFFFF"
#  base[INSENSITIVE]	= "#FFFFFF"
#  base[SELECTED]	= "#FFFFFF"

  engine "xfce"
  {
    smooth_edge = false
  }

}

style "pbar" = "default"
{

  xthickness = 0
  ythickness = 0

  bg[NORMAL]	= "#FFFFFF"
  bg[PRELIGHT]	= "#F1EBF9"
  engine "xfce" 
  {
     smooth_edge = true
     boxfill
     {
         fill_style = gradient
         orientation = auto
         shade_start = 1.13
         shade_end = 0.87
     }
  }

}

style "scale" = "default"
{

  xthickness = 2
  ythickness = 2

  bg[NORMAL]		= "#D4D4F8"
  bg[PRELIGHT]		= "#F1EBF9"
  bg[ACTIVE]		= "#F1EBF9"
  bg[INSENSITIVE]	= "#B7A1F4"
  base[SELECTED]	= "#F1EBF9"
  base[ACTIVE]		= "#FFFFFF"

  engine "xfce"
  {
    grip_style = slide
    smooth_edge = true
    boxfill
    {
      fill_style = gradient
      shade_start = 1.13
      shade_end = 1.00
    }
  }

}

style "menubar" = "default"
{

  xthickness = 0
  ythickness = 0

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 0.92
      shade_end = 1.00
    }
  }
}

style "menuitem" = "default"
{

  xthickness = 2
  ythickness = 2

  fg[NORMAL]		= "#8080FF"
  fg[PRELIGHT]		= "#0000FF"

  engine "xfce"
  {
    smooth_edge = true
    boxfill
    {
      fill_style = gradient
      orientation = auto
      shade_start = 1.13
      shade_end = 0.87
    }
  }
}

style "button" = "default"
{

  xthickness = 2
  ythickness = 2

  fg[NORMAL]		= "#A77149"
  fg[PRELIGHT]		= "#82481D"
  fg[ACTIVE]		= "#92572B"
  fg[INSENSITIVE]	= "#5D4F44"

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 1.13
      shade_end = 0.87
    }
  }
}

style "check" = "default"
{

  xthickness = 1
  ythickness = 1

  bg[SELECTED]		= "#CAA990"

}

style "frame" = "default"
{

  xthickness	= 1
  ythickness	= 1

  fg[NORMAL]		= "#A77149"
  bg[NORMAL]		= "#D6BEAC"

}

style "tabs" = "default"
{

  xthickness	= 1
  ythickness	= 1

  bg[ACTIVE]		= "#F1EBF9"

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = auto
      shade_start = 1.13
      shade_end = 1.00
    }
  }

}

widget_class "*"		style "default"

widget_class "*Button*"		style "button"
class "*Button*"		style "button"
widget_class "*button*"		style "button"
class "*button*"		style "button"
widget_class "*OptionMenu*"	style "button"
class "*OptionMenu*"		style "button"
widget_class "*Tree*"		style "button"
class "*Tree*"			style "button"

widget_class "*CheckButton*"	style "check"
class "*CheckButton*"		style "check"
widget_class "*RadioButton*"	style "check"
class "*RadioButton*"		style "check"
widget_class "*ComboBox*"	style "check"
class "*ComboBox*"		style "check"
widget_class "*List*"		style "check"
class "*List*"			style "check"
widget_class "*Text*"		style "check"
class "*Text*"			style "check"
widget_class "*Entry*"		style "check"
class "*Entry*"			style "check"
widget_class "*ComboBoxEntry*"	style "check"
class "*ComboBoxEntry*"		style "check"

widget_class "*MenuBar"		style "menubar"
class "*MenuBar"		style "menubar"
widget_class "*ToolBar"		style "menubar"
class "*ToolBar"		style "menubar"
widget_class "*BonoboDockItem"	style "menubar"
class "*BonoboDockItem"		style "menubar"
widget_class "*HandleBox"	style "menubar"
class "*HandleBox"		style "menubar"

widget_class "*MenuItem*"	style "menuitem"
class "*MenuItem*"		style "menuitem"

widget_class "*GtkProgress*"	style "pbar"
class "*GtkProgress*"		style "pbar"

widget_class "*Scrollbar*"	style "scale"
class "*Scrollbar*"		style "scale"
widget_class "*GtkScale*"	style "scale"
class "*GtkScale*"		style "scale"
widget_class "*Scale*"		style "scale"
class "*Scale*"			style "scale"

widget_class "*Frame*"		style "frame"
class "*Frame*"			style "frame"

widget_class "*Notebook*"	style "tabs"
class "*Notebook*"		style "tabs"

widget "xfwm"			style "default"
class "MetaFrames"		style "default"
widget_class "MetaFrames"	style "default"
```

Looking over that again, it reminds me; if anyone's lookin' for how to change the tabs, it's GtkNotebook widget :x Took me a while to figure that out. I'll post a WidgetFactory shot after I fine-tune it some more, and the completed gtkrc file. If I'm happy enough with the theme, you may even see it on xfce-look.org in the near future ;)

Thanks again, crimesaucer o/ And happy theming, everyone \o

---

### Post by crimesaucer on 2007-07-02
Post a picture of the GtkNotebook widget when you finish, I would like to see how you changed it's look.

---

### Post by ceil420 on 2007-07-02
Presenting: the LadyLockheart theme made by me :)

[IMG]http://img225.imageshack.us/img225/9233/ladylockheartiw6.png[/IMG]

The panel:

[IMG]http://img96.imageshack.us/img96/3733/ladylockheartpaneljj2.png[/IMG]

The tab curvature bit didn't have as big effect as I was hoping it would, but there's still a subtle change there. I also want to make a matching cursor and icon set before the theme as a whole is released to the world at large, though. This has turned into a bigger project than I initially thought! Of course, I have to figure out *how* to make icons and cursors before I can go further :x Looks like I've got another night of googling and inspecting other cursors and icons ahead of me.

Oh, and here's the gtkrc file (but this time it's cleaned up a bit more; I took out the 'testing' bit for one thing :p):

```
# "Lady Lockheart" theme for Xfce, made by Ceil
# Based on a Final Fantasy VII desktop, made by the
# same author: http://www.deviantart.com/deviation/23611017/

# Colours (shades of white, blue, and flesh)
#
# FFFFFF F3E6DD
# F1EBF9 EAD8CB
# D4D4F8 D6BEAC
# C5BBED CAA990
# B7A1F4 BE9373
# 8080FF A77149
# 5050FF 92572B
# 0000FF 82481D

style "default"
{

  GtkRange::slider_width		= 14
  GtkRange::stepper_size		= 14
  GtkRange::stepper_spacing		= 2
  GtkRange::trough_border		= 0
  GtkScrollbar::min_slider_length	= 20
  GtkMenu::horizontal-padding		= 4
  GtkMenuItem::selected_shadow_type	= out
  GtkMenuItem::horizontal_padding	= 1
  GtkRadioButton::indicator_size	= 10
  GtkToolbar::shadow_type		= none
  GtkToolbar::button-relief		= normal
  GtkWidget::focus-line-width		= 0
  GtkNotebook::tab-curvature		= 3
  GtkNotebook::tab-overlap		= 3

  xthickness = 2
  ythickness = 2

  bg[NORMAL]		= "#FFFFFF"	# The normal colour.
  bg[PRELIGHT]		= "#F1EBF9"	# "On hover".
  bg[ACTIVE]		= "#C5BBED"	# When a button is pressed.
  bg[INSENSITIVE]	= "#D6BEAC"	# Disabled widget.
  bg[SELECTED]		= "#8080FF"	# When text is selected.
  fg[NORMAL]		= "#82481D"
  fg[PRELIGHT]		= "#BA9E89"
  fg[ACTIVE]		= "#A77149"
  fg[INSENSITIVE]	= "#5D4F44"
  fg[SELECTED]		= "#FFFFFF"
  text[NORMAL]		= "#92572B"
  text[PRELIGHT]	= "#82481D"
  text[ACTIVE]		= "#EAD8CB"
  text[INSENSITIVE]	= "#D6BEAC"
  text[SELECTED]	= "#FFFFFF"
  base[NORMAL]		= "#F1EBF9"
  base[PRELIGHT]	= "#F3E6DD"
  base[ACTIVE]		= "#D2B7A2"
  base[INSENSITIVE]	= "#8080FF"
  base[SELECTED]	= "#A88E77"

}

style "pbar" = "default"
{

  xthickness = 0
  ythickness = 0

  bg[NORMAL]	= "#FFFFFF"
  bg[PRELIGHT]	= "#F1EBF9"
  engine "xfce" 
  {
     smooth_edge = true
     boxfill
     {
         fill_style = gradient
         orientation = auto
         shade_start = 1.13
         shade_end = 0.87
     }
  }

}

style "scale" = "default"
{

  xthickness = 2
  ythickness = 2

  bg[NORMAL]		= "#D4D4F8"
  bg[PRELIGHT]		= "#F1EBF9"
  bg[ACTIVE]		= "#F1EBF9"
  bg[INSENSITIVE]	= "#B7A1F4"
  base[SELECTED]	= "#F1EBF9"
  base[ACTIVE]		= "#FFFFFF"

  engine "xfce"
  {
    grip_style = slide
    smooth_edge = true
    boxfill
    {
      fill_style = gradient
      shade_start = 1.13
      shade_end = 1.00
    }
  }

}

style "menubar" = "default"
{

  xthickness = 0
  ythickness = 0

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 0.92
      shade_end = 1.00
    }
  }
}

style "menuitem" = "default"
{

  xthickness = 2
  ythickness = 2

  fg[NORMAL]		= "#8080FF"
  fg[PRELIGHT]		= "#0000FF"

  engine "xfce"
  {
    smooth_edge = true
    boxfill
    {
      fill_style = gradient
      orientation = auto
      shade_start = 1.13
      shade_end = 0.87
    }
  }
}

style "button" = "default"
{

  xthickness = 2
  ythickness = 2

  fg[NORMAL]		= "#A77149"
  fg[PRELIGHT]		= "#82481D"
  fg[ACTIVE]		= "#92572B"
  fg[INSENSITIVE]	= "#5D4F44"

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 1.13
      shade_end = 0.87
    }
  }
}

style "check" = "default"
{

  xthickness = 1
  ythickness = 1

  bg[SELECTED]		= "#CAA990"
  base[NORMAL]		= "#F1EBF9"
  base[PRELIGHT]	= "#F3E6DD"
  base[ACTIVE]		= "#D2B7A2"
  base[INSENSITIVE]	= "#8080FF"
  base[SELECTED]	= "#A88E77"

}

style "frame" = "default"
{

  xthickness	= 1
  ythickness	= 1

  fg[NORMAL]		= "#A77149"
  bg[NORMAL]		= "#D6BEAC"

}

style "tabs" = "default"
{

  xthickness	= 1
  ythickness	= 1

  bg[ACTIVE]		= "#F1EBF9"

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = auto
      shade_start = 1.13
      shade_end = 1.00
    }
  }

}

widget_class "*"		style "default"

widget_class "*Button*"		style "button"
class "*Button*"		style "button"
widget_class "*button*"		style "button"
class "*button*"		style "button"
widget_class "*OptionMenu*"	style "button"
class "*OptionMenu*"		style "button"
widget_class "*Tree*"		style "button"
class "*Tree*"			style "button"

widget_class "*CheckButton*"	style "check"
class "*CheckButton*"		style "check"
widget_class "*RadioButton*"	style "check"
class "*RadioButton*"		style "check"
widget_class "*ComboBox*"	style "check"
class "*ComboBox*"		style "check"
widget_class "*List*"		style "check"
class "*List*"			style "check"
widget_class "*Text*"		style "check"
class "*Text*"			style "check"
widget_class "*Entry*"		style "check"
class "*Entry*"			style "check"
widget_class "*ComboBoxEntry*"	style "check"
class "*ComboBoxEntry*"		style "check"

widget_class "*MenuBar"		style "menubar"
class "*MenuBar"		style "menubar"
widget_class "*ToolBar"		style "menubar"
class "*ToolBar"		style "menubar"
widget_class "*BonoboDockItem"	style "menubar"
class "*BonoboDockItem"		style "menubar"
widget_class "*HandleBox"	style "menubar"
class "*HandleBox"		style "menubar"

widget_class "*MenuItem*"	style "menuitem"
class "*MenuItem*"		style "menuitem"

widget_class "*GtkProgress*"	style "pbar"
class "*GtkProgress*"		style "pbar"

widget_class "*Scrollbar*"	style "scale"
class "*Scrollbar*"		style "scale"
widget_class "*GtkScale*"	style "scale"
class "*GtkScale*"		style "scale"
widget_class "*Scale*"		style "scale"
class "*Scale*"			style "scale"
widget_class "*Scroll*"		style "scale"
class "*Scroll*"		style "scale"

widget_class "*Frame*"		style "frame"
class "*Frame*"			style "frame"

widget_class "*Notebook*"	style "tabs"
class "*Notebook*"		style "tabs"

widget "xfwm"			style "default"
class "MetaFrames"		style "default"
widget_class "MetaFrames"	style "default"
```

If someone can tell me how to change the background colour of the clock, that'd be great ;x That's the only big issue I've got left with the theme. But, I've got cursors to make :)

Edit: Did some poking around in the Xfce theme engine source code, and it does indeed look like it's as limited as it seems. Here's the "tokens" (copied from xfce_rc_style.h), and all the options I think are possible with this particular engine:

```
enum
{
    TOKEN_SMOOTHEDGE = G_TOKEN_LAST + 1,
    TOKEN_BOXFILL,
    TOKEN_FILL_STYLE,
    TOKEN_GRIP_STYLE,
    TOKEN_GRIP_NONE,
    TOKEN_GRIP_ROUGH,
    TOKEN_GRIP_SLIDE,
    TOKEN_GRADIENT,
    TOKEN_PLAIN,
    TOKEN_ORIENTATION,
    TOKEN_AUTO,
    TOKEN_HORIZONTAL,
    TOKEN_VERTICAL,
    TOKEN_NORTHERN_DIAGONAL,
    TOKEN_SOUTHERN_DIAGONAL,
    TOKEN_SHADE_START,
    TOKEN_SHADE_END,
    TOKEN_TRUE,
    TOKEN_FALSE
};

^=- that's from the style header file. Here's all you can do with /engine "xfce"/ -=v

engine "xfce" {
  smooth_edge = true, false
  grip_style = none, rough, slide
  boxfill {
    fill_style = gradient, plain
    orientation = auto, horizontal, vertical, northern_diagonal, southern_diagonal
    shade_start = FLOAT
    shade_end = FLOAT
  }
}
```

I was kind of hoping there'd be more :xThen, Xfce is meant to be light; but this theme engine is crazy light. Still, my pretty theme is pure Xfce :)

Maybe one day I'll do the same for other theme engines. I've got a document with all the options for the Smooth engine I've seen used, but I haven't actually seen the source code for it. I'm not even sure I want to see the source for Clearlooks and Pixmap :x That much C code would probably give me a headache! Still, I hope this helps someone.

---

### Post by moredhel on 2007-07-03
Guide looks good, though I have yet to trial it.

---

### Post by crimesaucer on 2007-07-03
Thank you, feel free to add any tips that you might know about xfce or any other theme engine.

Also, any tips/links about custom icons, userChrome.css, panel images, and window decorations such as Emerald are also welcome....

---

### Post by ceil420 on 2007-07-03
Only thing I know about custom icons is that you'll have your work cut out for you if you're planning on making a whole set; there's literally hundreds of them (737 svg icons alone in the gnome set; there are also six different sizes in png format). I don't know anything about anything else yet :x Here's my notes on the "smooth" engine, sorted alphabetically, but with no comments; it just shows every option I came across in /usr/share/themes:

```
engine "smooth" {

  real_sliders = true,false
  resize_grip = true,false
  tab_style = square,round

  arrow {
    etched = true,false
    insensitive {
      etched = true,false
    }
    solid = true,false
    style = CleanIce,wonderland
    xpadding = INT
    ypadding = INT
  }

  button {
    embeddable = true,false
  }

  check {
    fill { }
    line { }
    motif = false,true
    style = clean,wonderland
  }

  edge {
    line { }
  }

  fill {
    color1[STATUS] = "#HEX"
    color2[STATUS] = "#HEX"
    hdirection = vertical,fdiagonal
    quadratic = true,false
    shade1 = 0.00-1.99
    shade2 = 0.00-1.99
    style = shaded,solid,gradient
    vdirection = horizontal,fdiagonal
  }

  grip {
    count = INT
    fill { }
    spacing = INT
    style = mac_buds_in,none,dots_out,ns_buds_in
    tollbar_overlap = true,false
  }

  line {
    style = smooth,none,thin.flat
    thickness = INT
  }

  option {
    fill { }
    line { }
    motif = false,true
    style = round,circle,clean
  }

  progress {
    line { }
  }

  tabs {
    style = square
  }

  trough {
    fill { }
    line { }
    show_value = true,false
    xpadding = INT
    ypadding = INT
  }

}
```

And for something slightly off topic (but partly relevant, because I made them to go with my theme), I present my FFVII cursor theme :) I didn't make all 77 cursors; just the ones that actually get used. You can compare my chart with the one found at [http://www.xed.ch/lwm/tcltkref/tk.cursor.html](http://www.xed.ch/lwm/tcltkref/tk.cursor.html)

[img]http://img169.imageshack.us/img169/4800/previewbe0.png[/img]

---

### Post by bvc on 2007-07-04
is there nothing in the source for the arrows? I find it hard to believe there's no arrow config. In the smooth engine you can do a little with size with```
		arrow
		{
			style = cleanice
			solid = TRUE
			xpadding = 0
			ypadding = 0

			INSENSITIVE
			{
				etched = TRUE
			}
		}
```but don't even try```
		arrow
		{
			xpadding = 0
			ypadding = 0
		}
```because you'll lock your puter :p

In gnome the clock font can be controlled with```
style "panel-clock"
{
fg[NORMAL] = "#FF0000"
}
widget "*.clock-applet-button.*" style "panel-clock"
#widget "*PanelWidget*" style "panel-clock"
#widget "*PanelApplet*" style "panel-clock"
#widget_class "*Panel*GtkButton" style "panel-clock"
```but to get the bg to change I had to use```
style "panel-clock"
{
bg[NORMAL] = "#FFFFFF"
}
widget "*.clock-applet-button.*" style "panel-clock"
#widget "*PanelWidget*" style "panel-clock"
widget "*PanelApplet*" style "panel-clock"
#widget_class "*Panel*GtkButton" style "panel-clock"
``` but then the panel buttons change to. Something to tinker with for ya. I haven't figured out the right combination in gnome.

I am curious though. If you want to customize, why not use the smooth engine? It can look so much like the xfce engine. I know you don't get a few distinctions but if you want control the smooth engine has far more than any other engine.

For the pager in gnome-panel> style "pager" {

}
widget "*WnckPager" style "pager"of course put your bg and base colors in there.


If you're like me and can't stand the panel handle in gnome use a 10x10 pixel transparent image and```
style "handle"
{
engine "pixmap"
  {
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= VERTICAL
    }
    image
    {
      function			= HANDLE
      file              		= "pixel.png"
      border            		= { 0, 0, 0, 0 }
      stretch           		= TRUE
      orientation			= HORIZONTAL
    }
  }
}
class "PanelAppletFrame" style "handle"
class "GtkPaned"       	style "handle"
class "*Panel*" style "handle"
```

there was a time the smooth engine claimed to use images and  I tried it, but it was horrible. Later versions it didn't work and I admit it would be useless since you can use multiple engines for a theme. I put the above handle code in my gtkrc-2.0 in my home dir

---

### Post by crimesaucer on 2007-07-07
> **ceil420 said:**
> 

...from your picture in the above post...


#3: Same question/issue as #2. I'd like the drop-down arrow thing to be the same shape/style as the one below it ("GtkCombo"), but don't know which class/widget to fit the style to.




I found an answer for question #3.



I fixed this default setting (that I noticed you don't have on your gtkrc):



```
GtkButton::focus-padding          = 0
```

maybe try that...


This is my new theme's look:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-11-8.png[/IMG]


this is a bit of code from my last theme that I fixed when making my new theme:


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-10-12.png[/IMG]


```

GtkButton::default_border         = {0, 0, 0, 0}
GtkButton::default_outside_border = {0, 0, 0, 0}
GtkButton::default_spacing        = 0
GtkButton::focus-line-width       = 0
GtkButton::focus-padding          = 0

```

---

### Post by bvc on 2007-07-07
> **crimesaucer said:**
> I found an answer for question #3.

I fixed this default setting (that I noticed you don't have on your gtkrc):

```
GtkButton::focus-padding          = 0
```
maybe try that...apply the button code of the button to the check style which includes
widget_class "*Entry*"
class "*Entry*"
widget_class "*ComboBox*"
class "*ComboBox*"

```
  xthickness = 1
  ythickness = 1

  engine "xfce"
  {
    boxfill
    {
      fill_style = gradient
      orientation = vertical
      shade_start = 1.10
      shade_end = 0.95
    }
  }
```Of course removing those classes from the check style may resolve it as well.....I didn't try...

---

### Post by crimesaucer on 2007-07-07
I had mine in style "default"

and style "colored" = "default"


...just like most of the xubuntu default themes.

---

### Post by bvc on 2007-07-07
that doesn't tell me anything. All I know is when I did the above the buttons and arrows of the combobox's and buttons matched. Changing the focus-padding won't change the button.

---

### Post by crimesaucer on 2007-07-07
Worked for me.



This is before: 

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-13-15.png[/IMG]



This is after:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-14-10.png[/IMG]


This was my style default for my before picture:

```

gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 0
    GtkButton::focus-line-width       = 0
    GtkButton::focus-padding          = 2
    GtkCheckButton::indicator_size    = 10
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 0
    GtkPaned::handle_size             = 24
    GtkRadioButton::indicator_size    = 10
    GtkRange::slider_width            = 15
    GtkRange::stepper_size            = 15
    GtkRange::stepper_spacing         = 0
    GtkRange::trough_border           = 0
    GtkScrollbar::min_slider_length   = 34
    GtkToolbar::shadow_type           = out
    GtkWidget::focus-line-width       = 0
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 0
    ythickness = 0

    fg[NORMAL]        = "#000000"
    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"
    fg[SELECTED]      = "#000000"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#F0F2E7"
    bg[ACTIVE]        = "#8697AB"
    bg[PRELIGHT]      = "#8697AB"
    bg[SELECTED]      = "#6F6F73"
    bg[INSENSITIVE]   = "#F0F2E7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"
    text[SELECTED]    = "#000000"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#8697AB"
    base[ACTIVE]      = "#8697AB"
    base[PRELIGHT]    = "#6F6F73"
    base[SELECTED]    = "#6F6F73"
    base[INSENSITIVE] = "#F0F2E7"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.89 
            shade_end = 1.00
        }
    }
}
 
widget_class "*" style "default"

style "colored" = "default"
{
    xthickness = 2
    ythickness = 2

    bg[ACTIVE]        = "#B9C09C"
    bg[PRELIGHT]      = "#6F6F73"

    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"

    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}

widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*List*"              style "colored"
class "*List*"                     style "colored"


```


This was my style default after changing only one line of code:

```

# xfce-milk, gradients, and rounded buttons.
#


gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 0
    GtkButton::focus-line-width       = 0
    GtkButton::focus-padding          = 0
    GtkCheckButton::indicator_size    = 10
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 0
    GtkPaned::handle_size             = 24
    GtkRadioButton::indicator_size    = 10
    GtkRange::slider_width            = 15
    GtkRange::stepper_size            = 15
    GtkRange::stepper_spacing         = 0
    GtkRange::trough_border           = 0
    GtkScrollbar::min_slider_length   = 34
    GtkToolbar::shadow_type           = out
    GtkWidget::focus-line-width       = 0
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 0
    ythickness = 0

    fg[NORMAL]        = "#000000"
    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"
    fg[SELECTED]      = "#000000"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#F0F2E7"
    bg[ACTIVE]        = "#8697AB"
    bg[PRELIGHT]      = "#8697AB"
    bg[SELECTED]      = "#6F6F73"
    bg[INSENSITIVE]   = "#F0F2E7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"
    text[SELECTED]    = "#000000"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#8697AB"
    base[ACTIVE]      = "#8697AB"
    base[PRELIGHT]    = "#6F6F73"
    base[SELECTED]    = "#6F6F73"
    base[INSENSITIVE] = "#F0F2E7"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.89 
            shade_end = 1.00
        }
    }
}
 
widget_class "*" style "default"

style "colored" = "default"
{
    xthickness = 2
    ythickness = 2

    bg[ACTIVE]        = "#B9C09C"
    bg[PRELIGHT]      = "#6F6F73"

    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"

    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}

widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*List*"              style "colored"
class "*List*"                     style "colored"


```



...I think it worked for me because the GtkCombo used the style setting from my default "GtkButton::focus-padding          = 0", and applied it to the button part of the xfce default GtkCombo . 

I could be wrong.


I also changed my panel to match my new theme:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-17-10.png[/IMG]

---

### Post by bvc on 2007-07-07
Yes, that's why. You don't have separate button and combo styles.

---

### Post by crimesaucer on 2007-07-07
Well I have a seperate button style, just not the Combo so it's default.

this is the complete gtkrc for my last theme called milkyblue2, if you feel like checking it out on your computer have fun with it:

```

# xfce-milk, gradients, and rounded buttons.
#


gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 0
    GtkButton::focus-line-width       = 0
    GtkButton::focus-padding          = 0
    GtkCheckButton::indicator_size    = 10
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 0
    GtkPaned::handle_size             = 24
    GtkRadioButton::indicator_size    = 10
    GtkRange::slider_width            = 15
    GtkRange::stepper_size            = 15
    GtkRange::stepper_spacing         = 0
    GtkRange::trough_border           = 0
    GtkScrollbar::min_slider_length   = 34
    GtkToolbar::shadow_type           = out
    GtkWidget::focus-line-width       = 0
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 0
    ythickness = 0

    fg[NORMAL]        = "#000000"
    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"
    fg[SELECTED]      = "#000000"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#F0F2E7"
    bg[ACTIVE]        = "#8697AB"
    bg[PRELIGHT]      = "#8697AB"
    bg[SELECTED]      = "#6F6F73"
    bg[INSENSITIVE]   = "#F0F2E7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"
    text[SELECTED]    = "#000000"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#8697AB"
    base[ACTIVE]      = "#8697AB"
    base[PRELIGHT]    = "#6F6F73"
    base[SELECTED]    = "#6F6F73"
    base[INSENSITIVE] = "#F0F2E7"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.89 
            shade_end = 1.00
        }
    }
}
 
widget_class "*" style "default"

style "colored" = "default"
{
    xthickness = 2
    ythickness = 2

    bg[ACTIVE]        = "#B9C09C"
    bg[PRELIGHT]      = "#6F6F73"

    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#000000"

    text[ACTIVE]      = "#FFFFFF"
    text[PRELIGHT]    = "#000000"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}

widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*List*"              style "colored"
class "*List*"                     style "colored"

style "menubar" = "colored"
{
    xthickness = 0
    ythickness = 0

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            
            fill_style = gradient
            orientation = vertical
            shade_start = 0.79
            shade_end = 0.89
        }
    }
}

widget_class "*BonoboDockItem"     style "menubar"
class "*BonoboDockItem"            style "menubar"
widget_class "*HandleBox"          style "menubar"
class "*HandleBox"                 style "menubar"
widget_class "*ToolBar"            style "menubar"
class "*ToolBar"                   style "menubar"
widget_class "*MenuBar"            style "menubar"
class "*MenuBar"                   style "menubar"

style "menuitem" = "colored"
{
    xthickness = 2
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.73
            shade_end = 0.93
        }
    }
}

widget_class "*MenuItem*"          style "menuitem"
class "*MenuItem*"                 style "menuitem"

style "scrollbar" = "default"
{
    xthickness = 1
    ythickness = 1
    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 1.73
            shade_end = 0.60
        }
    }
}

widget_class "*Scrollbar*"         style "scrollbar"
class "*Scrollbar*"                style "scrollbar"
widget_class "*GtkProgress*"       style "scrollbar" 
class "*GtkProgress*"              style "scrollbar" 

style "button" = "colored"
{
    xthickness = 2
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.92
            shade_end = 0.82
        }
    }
}

widget_class "*Button*"            style "button" 
class "*Button*"                   style "button" 
widget_class "*button*"            style "button" 
class "*button*"                   style "button" 
widget_class "*Togglebutton*"      style "button" 
class "*Togglebutton*"             style "button" 
widget_class "*togglebutton*"      style "button" 
class "*togglebutton*"             style "button" 
widget_class "*OptionMenu*"        style "button" 
class "*OptionMenu*"               style "button" 
widget_class "*Tree*"              style "button" 
class "*Tree*"                     style "button" 
widget_class "*GtkScale*"          style "button" 
class "*GtkScale*"                 style "button" 

widget_class "*CheckButton*"       style "default"
class "*CheckButton*"              style "default"
widget_class "*RadioButton*"       style "default"
class "*RadioButton*"              style "default"

# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar" = "default"
{
    bg[SELECTED]      = "#8697AB"
    fg[SELECTED]      = "#F0F2E7"
    bg[INSENSITIVE]   = "#6F6F73"
    fg[INSENSITIVE]   = "#8697AB"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 



```

My current theme uses the shadows. out, out and etched-in, and few other modifications. I've also changed my grip style to none so that it looks smoother.

---

### Post by crimesaucer on 2007-07-08
This is a complete look at my newest xfce theme:



[img]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22-13.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22y-1.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-22y-1.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-38-8.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-38-9.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-38-9.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-39-7.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-39-8.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-39-8.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-10.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-9.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-31-9.png)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-14.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-13.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-13.png)

[img]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-23-13.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-23-12.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-23-12.png)

[img]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-27-8.png[/img]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-27-7.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-27-7.png)

---

### Post by bvc on 2007-07-08
> **crimesaucer said:**
> Well I have a seperate button style, just not the Combo so it's default.I would have to check but the button should be higher than the combo in hierarchy, so the combo should by default inherit button properties unless a separate combo style is specified. Maybe that doesn't apply to arrows? But I see now, you didn't post your entire gtkrc. I was using the other users gtkrc to fix the problem anyway. Your desktop looks good!

---

### Post by crimesaucer on 2007-07-08
Thank you, I'm still learning. I also need to start learning how to theme for some other engines besides xfce.

---

### Post by ceil420 on 2007-07-25
Still no luck on the clock <_< (been a while; I've been busy)

I even went so far as to create a new style called "clock" with every colour as white and applied it it to widget_class and class "*clock*", to no avail. Does no one know how to change the colour of the panel clock in Xfce? freenode/xfce apparently doesn't :x

---

### Post by smartboyathome on 2007-07-25
I wish I had come accross this when I stated editing my gtkrc theme. Would have saved me time. :) Oh well, I still like what I did.

---

### Post by crimesaucer on 2007-07-25
> **ceil420 said:**
> Still no luck on the clock <_< (been a while; I've been busy)

I even went so far as to create a new style called "clock" with every colour as white and applied it it to widget_class and class "*clock*", to no avail. Does no one know how to change the colour of the panel clock in Xfce? freenode/xfce apparently doesn't :x

Try uninstalling the xfce4 panel "Clock", and then in that same xfce4 panel plug-in list, add the "Orage Clock"...which you can change the colors of in right click properties...plus there are better settings and a Calendar.


I use the Orage Clock and as you can see in my screenshots, the colors always match....plus, it uses the gtkrc-2.0 file for bg_pixmap[NORMAL] images.

---

### Post by crimesaucer on 2007-07-25
> **smartboyathome said:**
> I wish I had come accross this when I stated editing my gtkrc theme. Would have saved me time. :) Oh well, I still like what I did.


Feel free to add anything you have learned.

I haven't really been adding any new info lately, because I finally made a theme that I feel like staying with....maybe in a month or two I'll try some new theme changes and post the results.

---

### Post by fwwarr on 2007-07-30
Hi

Does anyone know how to set the font color of items in a ComboBox?
I need it different that the default text[NORMAL]

The theme is mostly white on black, except for regular text areas which are black on white. The only problem are the combobox items that are not selected or hovered: they appear black on black.

Here are the relevant parts of the gtkrc:

```

style "default"
{
#[...]
fg[NORMAL]		= "#ffffff" #Normal Button Text
fg[PRELIGHT]		= "#ffffff" #Mouseover button text
fg[ACTIVE]		= "#ffffff" #Active button text
fg[SELECTED]		= "#909090" # ??
fg[INSENSITIVE]		= "#909090" # ??

bg[NORMAL]		= "#080808" #Inactive Window Title Bar
bg[PRELIGHT]		= "#000000" # ??
bg[ACTIVE]		= "#000000" # ??
bg[SELECTED]		= "#080808" #Active Window Title Bar
bg[INSENSITIVE] 	= "#3f3f3f" # ??

base[NORMAL]		= "#ffffff" #"#000000" Text Area Background
base[PRELIGHT]		= "#313131" # ??
base[ACTIVE]		= "#071f46" #Inactive Selection Background
base[SELECTED]		= "#0d377c" #Active Selection Background
base[INSENSITIVE]	= "#ffffff" #"#000000" Disabled Text Area Background

text[NORMAL]		= "#000000" #"#ffffff"
text[PRELIGHT]		= "#ffffff"
text[ACTIVE]		= "#ffffff" #Inactive Selection Text
text[SELECTED]		= "#ffffff" #Active Selection Text
text[INSENSITIVE]	= "#606060"

}

class "GtkWidget" style "default"

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
#[...]
}

widget_class "*Combo*" style "optionmenu"

style "menuitem" = "default"
{
xthickness		= 1
fg[PRELIGHT] 	= "#ffffff"
text[PRELIGHT]	= "#949494"
#[...]
}


widget_class "*List" style "list-header"
widget_class "*GtkTree*" style "list-header"
widget_class "*GtkCList*" style "list-header"
class "GtkButton" 			style "button"
class "GtkRadioButton" 		style "radiobutton"
class "GtkRadioMenuItem" 	style "radiobutton"
class "GtkCheckButton" 		style "checkbutton"
class "GtkCheckMenuItem" 	style "checkbutton"
class "GtkOptionMenu" 		style "optionmenu"
class "GtkCombo*" 			style "optionmenu"
class "GtkListItem"		style "menuitem"
class "*Font*" 				style "optionmenu"
class "GtkEntry" 			style "entry"
class "GtkOldEditable" 		style "entry"
class "GtkSpinButton" 	 	style "spinbutton"
class "GtkRuler" 			style "ruler"
class "GtkScrollbar" 			style "scrollbar"
class "GtkProgressBar" 		style "progressbar"
class "GtkRange" 			style "range"
class "GtkMenu" 			style "menu"
class "GtkMenuBar*" 		 	style "menubar"
widget_class "*MenuBar.*" 	style "menubar"
class "GtkMenuItem"			style "menuitem"
class "GtkTearoffMenuItem"	style "menuitem"
class "GtkNotebook"	 		style "notebook"
class "GtkToolbar" 			style "flat"
class "GtkHandleBox" 		style "handlebox"
class "GtkEventBox" 			style "flat"
class "GtkPaned" 			style "handlebox"
class "GtkLayout" 			style "layout"
class "SPButton" 			style "SPbutton"
widget "gtk-tooltips" 		style "tooltips"
```

Thanks for any help!

---

### Post by xl_cheese on 2007-07-30
> **fwwarr said:**
> Hi

Does anyone know how to set the font color of items in a ComboBox?
I need it different that the default text[NORMAL]

The theme is mostly white on black, except for regular text areas which are black on white. The only problem are the combobox items that are not selected or hovered: they appear black on black.

Here are the relevant parts of the gtkrc:

```

style "default"
{
#[...]
fg[NORMAL]		= "#ffffff" #Normal Button Text
fg[PRELIGHT]		= "#ffffff" #Mouseover button text
fg[ACTIVE]		= "#ffffff" #Active button text
fg[SELECTED]		= "#909090" # ??
fg[INSENSITIVE]		= "#909090" # ??

bg[NORMAL]		= "#080808" #Inactive Window Title Bar
bg[PRELIGHT]		= "#000000" # ??
bg[ACTIVE]		= "#000000" # ??
bg[SELECTED]		= "#080808" #Active Window Title Bar
bg[INSENSITIVE] 	= "#3f3f3f" # ??

base[NORMAL]		= "#ffffff" #"#000000" Text Area Background
base[PRELIGHT]		= "#313131" # ??
base[ACTIVE]		= "#071f46" #Inactive Selection Background
base[SELECTED]		= "#0d377c" #Active Selection Background
base[INSENSITIVE]	= "#ffffff" #"#000000" Disabled Text Area Background

text[NORMAL]		= "#000000" #"#ffffff"
text[PRELIGHT]		= "#ffffff"
text[ACTIVE]		= "#ffffff" #Inactive Selection Text
text[SELECTED]		= "#ffffff" #Active Selection Text
text[INSENSITIVE]	= "#606060"

}

class "GtkWidget" style "default"

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
#[...]
}

widget_class "*Combo*" style "optionmenu"

style "menuitem" = "default"
{
xthickness		= 1
fg[PRELIGHT] 	= "#ffffff"
text[PRELIGHT]	= "#949494"
#[...]
}


widget_class "*List" style "list-header"
widget_class "*GtkTree*" style "list-header"
widget_class "*GtkCList*" style "list-header"
class "GtkButton" 			style "button"
class "GtkRadioButton" 		style "radiobutton"
class "GtkRadioMenuItem" 	style "radiobutton"
class "GtkCheckButton" 		style "checkbutton"
class "GtkCheckMenuItem" 	style "checkbutton"
class "GtkOptionMenu" 		style "optionmenu"
class "GtkCombo*" 			style "optionmenu"
class "GtkListItem"		style "menuitem"
class "*Font*" 				style "optionmenu"
class "GtkEntry" 			style "entry"
class "GtkOldEditable" 		style "entry"
class "GtkSpinButton" 	 	style "spinbutton"
class "GtkRuler" 			style "ruler"
class "GtkScrollbar" 			style "scrollbar"
class "GtkProgressBar" 		style "progressbar"
class "GtkRange" 			style "range"
class "GtkMenu" 			style "menu"
class "GtkMenuBar*" 		 	style "menubar"
widget_class "*MenuBar.*" 	style "menubar"
class "GtkMenuItem"			style "menuitem"
class "GtkTearoffMenuItem"	style "menuitem"
class "GtkNotebook"	 		style "notebook"
class "GtkToolbar" 			style "flat"
class "GtkHandleBox" 		style "handlebox"
class "GtkEventBox" 			style "flat"
class "GtkPaned" 			style "handlebox"
class "GtkLayout" 			style "layout"
class "SPButton" 			style "SPbutton"
widget "gtk-tooltips" 		style "tooltips"
```

Thanks for any help!

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
#[...]
}

try this:

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
fg[NORMAL]  = "#FFFFFF" 
bg[NORMAL] = "#000000"
#[...]
}

fg is the color of your font in window and menus.
bg is the background color of those things.

text is the color of the text you write with a keyboard.

---

### Post by fwwarr on 2007-07-30
> **xl_cheese said:**
> style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
#[...]
}

try this:

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
fg[NORMAL]  = "#FFFFFF" 
bg[NORMAL] = "#000000"
#[...]
}

fg is the color of your font in window and menus.
bg is the background color of those things.

text is the color of the text you write with a keyboard.

Thanks for the quick reply!
Unfortunately this does not work.
I'm pretty sure the value that has to be changed is the text[NORMAL] one because when I change only that value in the "default" style, the elements I'm having trouble with do change color. It's just that I want them to be a different color than the one in the default style.

Note that I'm not talking about OptionMenu items, these seem to work fine. The same problem affects the items in the address and search bar drop downs in firefox. What I want is for the box itself to have black text on a white background, but I want the dropdown to have white text on a black background (I know this may look a little weird in firefox, but this is the way it needs to be to look right everywhere else)

Thanks

---

### Post by xl_cheese on 2007-07-30
> **fwwarr said:**
> Thanks for the quick reply!
Unfortunately this does not work.
I'm pretty sure the value that has to be changed is the text[NORMAL] one because when I change only that value in the "default" style, the elements I'm having trouble with do change color. It's just that I want them to be a different color than the one in the default style.

Note that I'm not talking about OptionMenu items, these seem to work fine. The same problem affects the items in the address and search bar drop downs in firefox. What I want is for the box itself to have black text on a white background, but I want the dropdown to have white text on a black background (I know this may look a little weird in firefox, but this is the way it needs to be to look right everywhere else)

Thanks

firefox is a different can of worms.  you need to create a userchrome.css file.

[http://ubuntuforums.org/showthread.php?t=503508](http://ubuntuforums.org/showthread.php?t=503508)

---

### Post by superzorro on 2007-07-30
Thank you crimesaucer for this howto, 
I'm complete new to (x)ubuntu and I'm messing around with the colors of the panels.
But I have a question is it possible to have different colors for the panels, I like very much having the upper panel with the applications and the bottom panel as "dock", however when I change the color of the panel it affects both, is there a way to select a different color for each panel?

---

### Post by crimesaucer on 2007-07-30
> **superzorro said:**
> Thank you crimesaucer for this howto, 
I'm complete new to (x)ubuntu and I'm messing around with the colors of the panels.
But I have a question is it possible to have different colors for the panels, I like very much having the upper panel with the applications and the bottom panel as "dock", however when I change the color of the panel it affects both, is there a way to select a different color for each panel?

You're welcome, and you can always share any pointers for customizations that you've learned.


As for your panel question, you could create a gtkrc-2.0 (for your panel), and put any image you want in there. I haven't learned if it is possible to write it into a regular gtkrc, but when I tried, it didn't work with a bg_pixmap[NORMAL] or a gradient box fill...

 I usually make a matching gradient image using two colors of my gtk-2.0 theme, or, I make an image that matches my Emerald window theme, and the write a simple .gtkrc-2.0 file and put it in to my /home/folder with the rest of my hidden files:

```

style "panel"
{
  bg[NORMAL] = "#EFEBE7"
  bg_pixmap[NORMAL] = "panel_striper2.png"
  fg[NORMAL] = "#000000"
  }

widget_class "*Panel*"      style "panel"
widget "*Panel*"            style "panel"
class "*Panel*"             style "panel"

```


But, as of a yesterday I started to use an image that I made from this site: [http://www.stripegenerator.com/](http://www.stripegenerator.com/)

here it is: 

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-5-12.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-6-11.png[/IMG]


....and this is my newest creation that the panel image matches:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-4b.png[/IMG]


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-14.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-13.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-13.png)


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-16.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-15.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-7-15.png)


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-2-13.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-2-12.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-2-12.png)


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-15.png[/IMG]
[http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-14.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-1-14.png)

---

### Post by superzorro on 2007-08-02
Thank you very much crimesaucer for your prompt answer, I will try out your solution and hopefully upload some screenshots.

---

### Post by Hells_Dark on 2007-08-08
Does anybody know how to reduce the height of the pager ?

---

### Post by Hells_Dark on 2007-08-08
tss. this gnome pager is just ugly with a lot of themes and nobody cares..
Are there alternative pagers ? >_<

---

### Post by bvc on 2007-08-11
> **fwwarr said:**
> Hi

Does anyone know how to set the font color of items in a ComboBox?
I need it different that the default text[NORMAL]

The theme is mostly white on black, except for regular text areas which are black on white. The only problem are the combobox items that are not selected or hovered: they appear black on black.

Here are the relevant parts of the gtkrc:

```

style "default"
{
#[...]
fg[NORMAL]		= "#ffffff" #Normal Button Text
fg[PRELIGHT]		= "#ffffff" #Mouseover button text
fg[ACTIVE]		= "#ffffff" #Active button text
fg[SELECTED]		= "#909090" # ??
fg[INSENSITIVE]		= "#909090" # ??

bg[NORMAL]		= "#080808" #Inactive Window Title Bar
bg[PRELIGHT]		= "#000000" # ??
bg[ACTIVE]		= "#000000" # ??
bg[SELECTED]		= "#080808" #Active Window Title Bar
bg[INSENSITIVE] 	= "#3f3f3f" # ??

base[NORMAL]		= "#ffffff" #"#000000" Text Area Background
base[PRELIGHT]		= "#313131" # ??
base[ACTIVE]		= "#071f46" #Inactive Selection Background
base[SELECTED]		= "#0d377c" #Active Selection Background
base[INSENSITIVE]	= "#ffffff" #"#000000" Disabled Text Area Background

text[NORMAL]		= "#000000" #"#ffffff"
text[PRELIGHT]		= "#ffffff"
text[ACTIVE]		= "#ffffff" #Inactive Selection Text
text[SELECTED]		= "#ffffff" #Active Selection Text
text[INSENSITIVE]	= "#606060"

}

class "GtkWidget" style "default"

style "optionmenu" = "default"
{
text[NORMAL]		= "#ffffff"
#[...]
}

widget_class "*Combo*" style "optionmenu"

style "menuitem" = "default"
{
xthickness		= 1
fg[PRELIGHT] 	= "#ffffff"
text[PRELIGHT]	= "#949494"
#[...]
}


widget_class "*List" style "list-header"
widget_class "*GtkTree*" style "list-header"
widget_class "*GtkCList*" style "list-header"
class "GtkButton" 			style "button"
class "GtkRadioButton" 		style "radiobutton"
class "GtkRadioMenuItem" 	style "radiobutton"
class "GtkCheckButton" 		style "checkbutton"
class "GtkCheckMenuItem" 	style "checkbutton"
class "GtkOptionMenu" 		style "optionmenu"
class "GtkCombo*" 			style "optionmenu"
class "GtkListItem"		style "menuitem"
class "*Font*" 				style "optionmenu"
class "GtkEntry" 			style "entry"
class "GtkOldEditable" 		style "entry"
class "GtkSpinButton" 	 	style "spinbutton"
class "GtkRuler" 			style "ruler"
class "GtkScrollbar" 			style "scrollbar"
class "GtkProgressBar" 		style "progressbar"
class "GtkRange" 			style "range"
class "GtkMenu" 			style "menu"
class "GtkMenuBar*" 		 	style "menubar"
widget_class "*MenuBar.*" 	style "menubar"
class "GtkMenuItem"			style "menuitem"
class "GtkTearoffMenuItem"	style "menuitem"
class "GtkNotebook"	 		style "notebook"
class "GtkToolbar" 			style "flat"
class "GtkHandleBox" 		style "handlebox"
class "GtkEventBox" 			style "flat"
class "GtkPaned" 			style "handlebox"
class "GtkLayout" 			style "layout"
class "SPButton" 			style "SPbutton"
widget "gtk-tooltips" 		style "tooltips"
```

Thanks for any help!

```
style "combobox"		= "default"
{
  text[NORMAL]				= "#54A6BB"
```
```
class "GTKCombo" 					style "combobox"
widget_class "*Combo.*" 			style "combobox"
class "GTKComboBox" 				style "combobox"
widget_class "*ComboBox.*" 		style "combobox"
class "GTKComboBoxEntry" 			style "combobox"
widget_class "*ComboBoxEntry.*" 		style "combobox"
```works for me in the pixmap engine. This was taken from Onux Blue

---

### Post by dkaddict on 2007-09-09
Crimesaucer-

Good how2 m8.

I have managed to get a theme using the xfce gtk engine working and looking ok in Ubuntu Feisty.

I have attached a couple of screenshots of the xfce-winter hack I did as a result of this guide.
There are 2 shots of nautilus-I am going with the second style which uses a darker gradient-this way it blends in with the window frame better. It looks better in firefox that way too
 The panel is an image I made in GIMP (I have made hundreds of panel bars with gimp and use them by way of the panels right-click properties box).

I echo all who have asked for a clearlooks-engine guide similar to this. It would be great if there could be one for the 'pixbuff' engine too as I reckon that could be made to look pretty cool. I have been playing around with the 'Human' theme that comes as default with Ubuntu. It uses the clearlooks engine but I am slowly getting the hang of themeing it myself. I am just a bit lost around all of the 'class' variables and stuff like that. I only started playing around with these gtkrc files the other day and am surprised at how easy it is to get the hang of them.

Again, nice post crimesaucer.

peace

dk

---

### Post by ayoli on 2007-09-10
this code (from post 31)
```
#browser tabs {
    -moz-appearance: none !important;
    background-color: none !important;
    background: url("<some_bg>.png") repeat-x top !important;
    height: 25px;
    padding: 0px;
    border: 0px;
    margin: 0px;
    }
```
didn't work much for me.
I want a flat tab look in FF for non selected tabs. I've tried a flat color pnf as background, a simple color as background, I 've also tried to play with:
```
tab {
    -moz-appearance: none !important;
    background-color: <some_color> !important;
}
```
but I m stuck with FF tabs gradients.
Any suggestions ? :)

---

### Post by ayoli on 2007-09-10
> **dkaddict said:**
> 

I echo all who have asked for a clearlooks-engine guide similar to this. It would be great if there could be one for the 'pixbuff' engine too as I reckon that could be made to look pretty cool. I have been playing around with the 'Human' theme that comes as default with Ubuntu. It uses the clearlooks engine but I am slowly getting the hang of themeing it myself. I am just a bit lost around all of the 'class' variables and stuff like that. I only started playing around with these gtkrc files the other day and am surprised at how easy it is to get the hang of them.



pixbuf engine permit (almost) all what you want for theming, but it tooks much more memory/proc IMO.

---

### Post by crimesaucer on 2007-09-10
> **dkaddict said:**
> Crimesaucer-

Good how2 m8.

I have managed to get a theme using the xfce gtk engine working and looking ok in Ubuntu Feisty.

I have attached a couple of screenshots of the xfce-winter hack I did as a result of this guide.
There are 2 shots of nautilus-I am going with the second style which uses a darker gradient-this way it blends in with the window frame better. It looks better in firefox that way too
 The panel is an image I made in GIMP (I have made hundreds of panel bars with gimp and use them by way of the panels right-click properties box).

I echo all who have asked for a clearlooks-engine guide similar to this. It would be great if there could be one for the 'pixbuff' engine too as I reckon that could be made to look pretty cool. I have been playing around with the 'Human' theme that comes as default with Ubuntu. It uses the clearlooks engine but I am slowly getting the hang of themeing it myself. I am just a bit lost around all of the 'class' variables and stuff like that. I only started playing around with these gtkrc files the other day and am surprised at how easy it is to get the hang of them.

Again, nice post crimesaucer.

peace

dk

Thank you.

---

### Post by Vendri on 2007-09-12
I would like to say,as many have, thank you. That was an excellent guide when I was a novice; it really helped me get a handle on the whole process. I've now got a theme that I am very pleased with, there is only one problem. I'm not sure what to call them(I'm thinking alt-text, for some reason), but whenever you hover your cursor over a button, text appears in a yellow box. The only problem is, I have white text, which makes it very difficult to read. I was wondering if you knew how to change the colour of the box (or the writing, if it didn't change ALL text). Again, many thanks!

---

### Post by melonenmelli on 2007-09-19
hello!

can someone tell me how to edit this window item or how it is called?
I'm trying to change it's color...

---

### Post by xl_cheese on 2007-09-19
> **melonenmelli said:**
> hello!

can someone tell me how to edit this window item or how it is called?
I'm trying to change it's color...

Those are the Range sliders.

---

### Post by melonenmelli on 2007-09-19
> **xl_cheese said:**
> Those are the Range sliders.


perfect! :D

thanks very much!

i added:

```
style "range"
{

	bg[PRELIGHT]  		= "#20FF00"
   bg[NORMAL] 			= "#43C632"


}
```

---

### Post by 3dxtrip on 2007-10-02
I use a dark theme in Xubuntu (Neutronium Gilouche&#65289;

The problems come with Text color on active texts links:

I can't read very well because the color is blue and the contrast with the background is very low.

[[IMG]http://img406.imageshack.us/img406/1166/fixtn1.th.png[/IMG]](http://img406.imageshack.us/my.php?image=fixtn1.png)

How can i change the color of the text links?

Thanks

---

### Post by dkaddict on 2007-10-08
Hello hello,

Thanks to this how2 I have been getting well into hacking these gtkrc files and have even uploaded a couple of my creations at Gnome look.

I mentioned in an earlier post that I would like to see a how2 such as the one here for the clearlooks engine. What I have discovered since is that themes written for the clearlooks engine are relatively short and really only offer one the opportunity to change the colours of the widgets and buttons etc.

To really make a mess I downloaded a load of different themes from gnome-look.org, unpacked them, and searched through all of the folders until I found one that used the pixmap engine, had seperate 'rc' files for the menu-bar, tool-bar, and panel, and had folders containing '.png' images for virtually every button, arrow, slider etc that the theme used. To make my changes was as easy as creating, for eg, a button with the GIMP and saving it either as the original file name or changing the path in the gtkrc file for the given image.

The links below are what I came up with by way of hacking the 'FC-Fino-Core' theme (can't find it again at Gnome-Look-search=0 results?????) which uses the pixmap engine.

My first hack

[http://www.gnome-look.org/content/show.php/maryj?content=67052](http://www.gnome-look.org/content/show.php/maryj?content=67052)

My final effort

[http://www.gnome-look.org/content/show.php/maryj2?content=67118](http://www.gnome-look.org/content/show.php/maryj2?content=67118)

Having got the hang of the pixmap engine, I had another delve into some themes and found one which uses the 'Aurora' engine. The Aurora engine is similar to Clearlooks and Murrine so much of the layout and the buttons/scrollbar look is fixed. it can be changed by way of incorporating the pixmap engine but I am only just working all of that out so...

Anyway, I started with a bog standard Aurora gtkrc, stole a few lines of code which gave me the opportunity to create my own toolbar style and panel and came up with the next two themes.

First attempt

[http://www.gnome-look.org/content/show.php/Aurora-wave?content=67305](http://www.gnome-look.org/content/show.php/Aurora-wave?content=67305)

Final

[http://www.gnome-look.org/content/show.php/Aurora-wave-0.1?content=67321](http://www.gnome-look.org/content/show.php/Aurora-wave-0.1?content=67321)

Now I ain't posting my themes to big up myself. That would not be wise because my themes are nowhere near as well made as crimesaucers or any of the other themers out there. I only post them to show that if a newb like me can get creative, anyone can do it if they follow the guide at the start of this thread. 

This how2 has given me loads of entertainment and I am well and truly addicted to hacking themes now!!

peace

dk

---

### Post by crimesaucer on 2007-10-09
> **dkaddict said:**
> Hello hello,

Thanks to this how2 I have been getting well into hacking these gtkrc files and have even uploaded a couple of my creations at Gnome look.

I mentioned in an earlier post that I would like to see a how2 such as the one here for the clearlooks engine. What I have discovered since is that themes written for the clearlooks engine are relatively short and really only offer one the opportunity to change the colours of the widgets and buttons etc.

To really make a mess I downloaded a load of different themes from gnome-look.org, unpacked them, and searched through all of the folders until I found one that used the pixmap engine, had seperate 'rc' files for the menu-bar, tool-bar, and panel, and had folders containing '.png' images for virtually every button, arrow, slider etc that the theme used. To make my changes was as easy as creating, for eg, a button with the GIMP and saving it either as the original file name or changing the path in the gtkrc file for the given image.

The links below are what I came up with by way of hacking the 'FC-Fino-Core' theme (can't find it again at Gnome-Look-search=0 results?????) which uses the pixmap engine.

My first hack

[http://www.gnome-look.org/content/show.php/maryj?content=67052](http://www.gnome-look.org/content/show.php/maryj?content=67052)

My final effort

[http://www.gnome-look.org/content/show.php/maryj2?content=67118](http://www.gnome-look.org/content/show.php/maryj2?content=67118)

Having got the hang of the pixmap engine, I had another delve into some themes and found one which uses the 'Aurora' engine. The Aurora engine is similar to Clearlooks and Murrine so much of the layout and the buttons/scrollbar look is fixed. it can be changed by way of incorporating the pixmap engine but I am only just working all of that out so...

Anyway, I started with a bog standard Aurora gtkrc, stole a few lines of code which gave me the opportunity to create my own toolbar style and panel and came up with the next two themes.

First attempt

[http://www.gnome-look.org/content/show.php/Aurora-wave?content=67305](http://www.gnome-look.org/content/show.php/Aurora-wave?content=67305)

Final

[http://www.gnome-look.org/content/show.php/Aurora-wave-0.1?content=67321](http://www.gnome-look.org/content/show.php/Aurora-wave-0.1?content=67321)

Now I ain't posting my themes to big up myself. That would not be wise because my themes are nowhere near as well made as crimesaucers or any of the other themers out there. I only post them to show that if a newb like me can get creative, anyone can do it if they follow the guide at the start of this thread. 

This how2 has given me loads of entertainment and I am well and truly addicted to hacking themes now!!

peace

dk

Actually, those are really nice looking.


I actually compiled the aurora engine and the murrine engine last night because I am planning on learning to make themes for those two engines, as well as the clearlooks engine with the glossy look of the new Gnome.


I really like those fading tabs and buttons you did, and everything else too. Those are both very good, and I like both of the color themes also.


Feel free to post any more themes or info, as well as links to your downloads.

---

### Post by nikoPSK on 2007-12-25
very, very nice! :KS

---

### Post by Neon612 on 2008-03-02
I've been reading through your posts and so far this seems like it could be real simple to do, but, alas, I've run into a bit of a snag. The theme folder will not let me save or paste my edited GTKRC file into it. So I can edit a file but not put it in the right directory. 

How can I get it so I can put my edited file into the theme directory?

---

### Post by yabbadabbadont on 2008-03-02
> **Neon612 said:**
> I've been reading through your posts and so far this seems like it could be real simple to do, but, alas, I've run into a bit of a snag. The theme folder will not let me save or paste my edited GTKRC file into it. So I can edit a file but not put it in the right directory. 

How can I get it so I can put my edited file into the theme directory?

Use sudo or gksudu to start your editor.  Alternatively, copy the theme to your ~/.themes directory and modify it there.  Since it is now in a directory that your user owns, you will have permission to modify it without sudo.

---

### Post by Precapice on 2008-05-08
> **Neon612 said:**
> I've been reading through your posts and so far this seems like it could be real simple to do, but, alas, I've run into a bit of a snag. The theme folder will not let me save or paste my edited GTKRC file into it. So I can edit a file but not put it in the right directory. 

How can I get it so I can put my edited file into the theme directory?

press Alt-F2 and type 
gksudo nautilus 

but be careful you are now browsing as root and can really screw things up.

as Yabbaddabbadont says it is wiser to install your theme in your home/.themes folder. it is hidden.

This is what works for me......

To do this create a folder on your desktop yourthemename/gtk-2.0/gtkrc

then compress it yourthemename.tar.gz 

open theme manager window (appearance) and click install navigate to your .tar.gz file 
click open.

now go to customize your theme should be under the controls tab.
You need to click some other theme first and then select your them for it to take affect. Don't know why this happens but there you have it.

Hope that helps ;)

---

### Post by smartboyathome on 2008-05-09
If you install it in $HOME/.themes, then it won't be applied to root. I would suggest a symlink from there to /usr/share/themes so that you can develop it and avoid inconsistancies.

---

### Post by hihihi on 2008-07-31
hello there,

thanks for sharing your insites and super howto too.

my question:
does anybody know how to change the insensitive color of insensitive text?

i am making a dark theme and it is looking better and better, but the insitives are insensitive: white offsets are psychadelic and irritating..

please help,

thanks 10000x times

---

### Post by jjgomera on 2008-09-07
Hello

I'm looking for the variable to change this colour (see attachment) but i can find in this guide, does anyone know how to change the colour for vertical and horizontal scrollbar when they are inactive, when the mouse is not over them?

---

### Post by leetrefz on 2008-09-10
Hey I've got a theme I really like but I want to make the close & minimise buttons on the xfwm4 window edge lighter. Can you tell me which line for that?

Thank you!

---

### Post by crimesaucer on 2008-09-11
> **leetrefz said:**
> Hey I've got a theme I really like but I want to make the close & minimise buttons on the xfwm4 window edge lighter. Can you tell me which line for that?

Thank you!

It's been a while since I was active in this thread.... I use Gnome now that I have 4GB's of ram on a dual core, and themeing for clearlooks and murrina is pretty easy.


But to answer this question about xfwm4 buttons, you would have to replace the .png buttons with the newer lighter ones that you would make using gimp.


I've made a few basic xfwm4 themes (all using the default kokodi theme), you should go to the /usr/share/themes/"window-theme-that-you're-using"/xfwm4 directory. 


In there you will see both .xpm files and .png files, as well as a themerc. You can modify some things in the themerc, you can also change the shape/size/color of your window theme by modifing all of the .xpm files. For the buttons and gloss efect, you can make your own .png images to replace the other .png images that go over the .xpm backgrounds. Just keep everything the same size.


It's a bit of work. I hope this helps.



These are a couple of my newest Gnome clearlooks themes, with my own UbuntuStudio icons theme, and emerald theme:

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-2-1.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-2.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-2.png)

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-5.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-5-1.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-5-1.png)

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11-1.jpg[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-11.jpg)

[img]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-1.png[/img]
Large View: [http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10.png)

---

### Post by quantruong1985 on 2008-12-15
I want my menus have rounded corners instead of square. How can I do that??

---

### Post by seenxu on 2008-12-15
great tutorial, thx.

---

### Post by smartboyathome on 2008-12-15
> **quantruong1985 said:**
> I want my menus have rounded corners instead of square. How can I do that??

Can't, unfortunately. :(

---

### Post by crimesaucer on 2008-12-15
> **seenxu said:**
> great tutorial, thx.

Thank you, I haven't made a "xfce4-engines" theme since the summer of 2007.... I started to use gnome and the clearlooks-glossy engine that is pretty straight forward and easy to customize..... then I went back to xfce4 and fell in love with the murrine-svn engines.


I think the murrine-svn is one of the most customizable engines out there. This is my current:

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-5.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-4.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-4.png)

---

### Post by thomasboleyn on 2009-06-04
> **crimesaucer said:**
> Thank you, I haven't made a "xfce4-engines" theme since the summer of 2007.... I started to use gnome and the clearlooks-glossy engine that is pretty straight forward and easy to customize..... then I went back to xfce4 and fell in love with the murrine-svn engines.


I think the murrine-svn is one of the most customizable engines out there. This is my current:

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-5.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-4.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-48-4.png)

Sorry to dig up and old thread.. I'm using a murrine based theme in Ubuntu Jaunty at the moment and am having trouble finding out what to edit in the gktrc file to make the gnome panel clock appear on 2 lines, like with a line break. I have seen win7 clone themes on gnome-look that do do this, though at the moment I can only achieve this in my current theme by putting a literal line break in to the custom format of the clock in gconf-editor, but it ends up looking strange as the bottom line of the clock is very close the bottom of the panel. The panel that I use is 40px, and I do not want to increase or decrease this (If I increase to 47px+ it causes the line break, but this is too much of an increase for me).

Any help would be apreciated, thanks.

---

### Post by Fzang on 2009-06-04
Thank you, this guide is really helpful :D

Do you have any tips on how to make rounded edges on theme borders? Mine always seem jaggy because they're not anti aliased properly

EDIT: I'd also like to know how to change the color of the sidebar BG in nautilus. Couldn't seem to find any info on that

---

### Post by dumblebee100 on 2009-08-07
Well I should thank for the tutorial ....I read your tutorial ...I didn't understand many but didn't stopped trying ..so after some trial and error process I came up with cool flat theme just perfect for my taste ...

I have a little problem with gtkrc 

I posted two screenshots
 screenshot 10 is my present theme ....Its flat but I dont want the blue line at the top of tab ..instead I want it like shade which will be in glossy theme 

my requirement is the tab style in glossy theme ....screenshot 11

all I want is my tabs should have gradient colour instead of the line over top ...I think you people get my problem

---

### Post by dumblebee100 on 2009-08-18
please somebody take interest in my problem and solve my problems ....

I dont think that this little thing will be a great deal to you users ....bcz all of u have edited full gtkrc's but I asking for only a little from that

---

### Post by Exodist on 2009-09-13
> **dumblebee100 said:**
> Well I should thank for the tutorial ....I read your tutorial ...I didn't understand many but didn't stopped trying ..so after some trial and error process I came up with cool flat theme just perfect for my taste ...

I have a little problem with gtkrc 

I posted two screenshots
 screenshot 10 is my present theme ....Its flat but I dont want the blue line at the top of tab ..instead I want it like shade which will be in glossy theme 

my requirement is the tab style in glossy theme ....screenshot 11

all I want is my tabs should have gradient colour instead of the line over top ...I think you people get my problem

[B]engine "clearlooks" {
		colorize_scrollbar = FALSE
		reliefstyle = 2
		menubarstyle = 2
		toolbarstyle = 1
		animation = TRUE
		radius = 3.0
		style = GLOSSY

		# Set a hint to disable backward compatibility fallbacks.
		hint = "use-hints"
	}[/B]

Style = GLOSSY controls it. Unfortunately it changes the entire theme to glossy and not just the tabs.

---

### Post by crimesaucer on 2009-11-03
> **dumblebee100 said:**
> please somebody take interest in my problem and solve my problems ....

I dont think that this little thing will be a great deal to you users ....bcz all of u have edited full gtkrc's but I asking for only a little from that

I'm sorry, I stopped using ubuntu in 2007, and when the fourms discontinued the Other OS section I find myself rarely visiting my old Ubuntu Forums account. This is the first time I've seen this question (on 11/03/09), and it looks like Exodist answered it correctly.

Just change "style = CLASSIC" or "style = GUMMY" to:

```
style = GLOSSY
```

for the tabs to use a fade (it will also change the buttons and other things).


If you try the murrine gtk engine, you can also use the faded tabs while still using the murrine style buttons and other things. I put this part in some of my murrine gtkrc files for faded tabs (although usually I use the CLASSIC setting because I think it looks best):

```

style "notebook" = "notebook-bg"
{	
	engine "clearlooks"
	{
		radius = 0.0
		style = GLOSSY
	}
}

```

This gives me Clearlooks tabs on a murrine theme.

clearlooks CLASSIC tabs on murrine:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-Classic.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-Classic-1.png)

clearlooks GUMMY tabs on murrine:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-Gummy.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-Gummy-1.png)

clearlooks GLOSSY tabs on murrine:
[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-glossy.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-10-glossy-1.png)

---

### Post by 10Digits on 2009-11-16
After digging through so many sites for gtk themes ur post was most helpful...trying to mod clearlooks mettalico....an already perfect looking theme.


Anyways found a software called The Widget Laboratory...it shows what changes you have done to the current theme instantly...which encouraged me to use it as I am uncomfortable with codes that last more than a page.
More about it....check out this URL..[http://www.ohloh.net/p/twl](http://www.ohloh.net/p/twl)

PS I think you may know about this software already but i wanted tomention it in this post anyways....:D

---

### Post by Exodist on 2009-11-16
The OP of this thread did try to describe how to mod a theme, but he left out lots a valuable information.

You can find the best information here [http://live.gnome.org/GnomeArt/Tutorials]("http://live.gnome.org/GnomeArt/Tutorials/")

---

### Post by Minsky on 2009-11-17
Hi, I'm new to altering themes and I hope that someone will be able to help me. I'm using Karmic with ATI drivers, Compiz installed and Extra Effects enabled. Is there a way to alter the transparency of the 3 main menu backgrounds (Applications,Places,System), whilst they're opened? I know that you can change the transparency of the whole lot with the Opacity settings in Compiz, and that I can alter the background colour in the gtkrc file, but I just want to alter the background transparency of the menus whilst leaving the text intact. What I'm after is for the menus, when displayed, to merge with the wallpaper with only an outline and the menu items text displayed. Am I right in thinking that a colour's alpha setting alters its transparency level and if so, where would I apply the setting in the gtkrc file to get the effect that I'm after?

---

### Post by Minsky on 2009-11-22
Can anyone help me out with this?

---

### Post by crimesaucer on 2009-11-24
> **Minsky said:**
> Can anyone help me out with this?

The only thing I can say is check out the RGBA murrine thermes that Cimi makes and hope for these themes one day: 

[http://www.cimitan.com/blog/wp-content/rgba-murrine-170208.png](http://www.cimitan.com/blog/wp-content/rgba-murrine-170208.png)
[http://www.cimitan.com/blog/wp-content/murrine_rgba.png](http://www.cimitan.com/blog/wp-content/murrine_rgba.png)
[http://www.cimitan.com/blog/wp-content/murrine_rgba-2.jpg](http://www.cimitan.com/blog/wp-content/murrine_rgba-2.jpg)

Blog posts about RGBA: 

[http://www.cimitan.com/blog/2008/11/16/murrine-needs-a-laptop-status-of-rgba-murrine-projects/](http://www.cimitan.com/blog/2008/11/16/murrine-needs-a-laptop-status-of-rgba-murrine-projects/)

[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/)

---

### Post by crimesaucer on 2009-11-24
> **Exodist said:**
> The OP of this thread did try to describe how to mod a theme, but he left out lots a valuable information.

You can find the best information here [http://live.gnome.org/GnomeArt/Tutorials]("http://live.gnome.org/GnomeArt/Tutorials/")


Hello, I was the creator of this thread.... I made it way back in March 2007 after messing around with some xfce4 themes. 



This thread is as old as dirt and mostly for the "xfce4 gtk engine" (which basically nobody uses). I'm always surprised when I see people digging up this ancient thread.



You can see my current murrine themes here (and some clearlooks): [http://crimesaucer.deviantart.com/gallery/](http://crimesaucer.deviantart.com/gallery/)
(the old xfce4 themes from this thread are on page 5 and 6)



There wasn't much information available when I wrote this back in early 2007, especially about the xfce4 gtk engines. 



There were no easy GUI apps included with gnome for changing the colors of gtk2 themes..... Beryl was around version 1.0 and considered "bleeding edge" back then..... hell, running "the widget factory" and modifying gtkrcs through trial and error was about the only thing that I found I could do. 



..... and the Gnome Tutorials that you and other people have linked are all good to read about gtk widgets, but none of them had an easy explanation that a beginner (such as myself) could follow to change a few colors and widget styles.



I am in no way a developer or a Linux guru, and in fact this post is a bit of an embarrassment now. It was basically me learning a few things and then sharing it with other beginners.



Hopefully someone will create a more current thread for everybody to discuss gtk2 themes in, I haven't even been in the Ubuntu Forums much since they closed the "Other OS" section (I haven't used xubuntu since 7.04).



So good luck to everyone, and hopefully this thread will be closed.

---

### Post by Minsky on 2009-11-25
Thanks Crimesaucer, I'll check out the links!

---

### Post by vie et mort on 2009-12-05
Anyone know how to change the color of this gtkrc's titlebar / frame? Not sure what exactly its called but its the bar all the way at the top of any open window, right above the menu-bar and it says the name of whatever you have open.
> [INDENT]# Author: perfectska04 (Victor C.)
# Theme:  Shiki-Colors for Murrine 0.9.3+.
# Description: Shiki-Colors is 100% free and open source.

# NOTE: Uncommenting means to delete the "#" at the beginning of a line. Commenting means to add a "#" at the beginning of a line. The "#" tells the theme wether to ignore the specified line or not.

# These are the defined colors for the theme, you can change them in GNOME's appearance preferences.
gtk_color_scheme = "fg_color:#101010\nbg_color:#D8D8D8\nbase_color:#fff\ntext_color:#1A1A1A\nselected_bg_color:#97bf60\nselected_fg_color:#fff\ntooltip_bg_color:#F5F5B5\ntooltip_fg_color:#000\nframe_color:#333333\ninactive_frame_color:#333333"

#########
# ICONS 
#########
gtk-icon-sizes    = "gtk-button=16,16" # This makes button icons smaller.
#gtk-icon-sizes = "gtk-large-toolbar=16,16:gtk-small-toolbar=16,16:panel-menu=16,16:gtk-button=16,16" # This enables "compact-mode".
#gtk-button-images    = 0 # Enables or disables icons on buttons (OS X-like).
#gtk-menu-popup-delay    = 1 # Makes menus pop up faster! Set to 1 instead of 0 to avoid any bugs.

##########
# PANELS 
##########
include "panel.rc" # This includes the file that handles panel theming. Gradient panel backgrounds are enabled by default for this setting. Please edit panel.rc if you don't want gradient backgrounds in your panels, or plan to use transparent/custom panels.

# The following lines make panel-menu-applet, slab-main-menu and gimmie applet's text bold. The radius value sets the roundness value of the selected menu-item.
style "bold-panel-menu"
{
    font_name = "Bold"

    engine "murrine" {
    roundness = 2
    }
}

style "bold-panel-slab"
{
    font_name = "Bold"
}
widget "*Panel*slab-main-menu-panel-button*" style "bold-panel-slab"
widget "*gimmie*" style "bold-panel-slab"
widget "*Panel*MenuBar*" style "bold-panel-menu"

##########################
# GENERAL THEME SETTINGS 
##########################
style "murrine-default"
{
    xthickness = 1
    ythickness = 1

    GtkButton::child-displacement-x    = 0 # Pressed button icon displacement.
    GtkButton::child-displacement-y    = 1 # Pressed button icon displacement.

    GtkButton::default-border    = { 0, 0, 0, 0 }
    GtkCheckButton::indicator-size    = 14 # Size for check buttons.
    GtkRadioButton::indicator-size    = 14 # Size for radio buttons.
    GtkPaned::handle-size        = 6 # Width of handles.

    GtkRange::trough-border        = 0
    GtkRange::slider-width        = 15 # Scrollbar width.
    GtkRange::stepper-size        = 15 # Stepper height.

    GtkScale::slider-length        = 24 # Length of sliders.
    GtkScale::trough-side-details    = 1
    GtkScrollbar::min-slider-length    = 35 # Min. length of scrollbars.

    GtkMenuBar::internal-padding    = 0
    GtkExpander::expander-size    = 16
    GtkToolbar::internal-padding    = 1 # Toolbar padding.
    GtkTreeView::expander-size    = 14
    GtkTreeView::vertical-separator    = 0

    GtkMenu::horizontal-padding    = 0
    GtkMenu::vertical-padding    = 0

    WnckTasklist::fade-overlay-rect    = 0
    GtkEntry::honors-transparent-bg-hint = 1
    GtkEntry::progress-border    = { 2, 2, 2, 2 } # Border of GtkEntry progressbars.

#    GtkWidget::focus-padding    = 0 # This can give you a more compact appearance.
      GtkScrolledWindow::scrollbar-spacing    = 1 # This sets the spacing between scrollbars.

# Uncomment one or both of the following for flat/unified menus or toolbars:
    GtkToolbar::shadow-type        = GTK_SHADOW_NONE  # Makes toolbars flat and unified.
#    GtkMenuBar::shadow-type        = GTK_SHADOW_NONE  # Makes menus flat and unified.

    ####################
    # Color Definitions
    ####################
    fg[NORMAL]        = @fg_color 
    fg[PRELIGHT]      = @fg_color
    fg[SELECTED]      = @selected_fg_color
    fg[ACTIVE]        = @fg_color
    fg[INSENSITIVE]   = darker (@bg_color)

    bg[NORMAL]        = @bg_color
    bg[PRELIGHT]      = shade (1.02, @bg_color)
    bg[SELECTED]      = @selected_bg_color
    bg[INSENSITIVE]   = @bg_color
    bg[ACTIVE]        = shade (0.85, @bg_color)

    base[NORMAL]      = @base_color
    base[PRELIGHT]    = shade (0.95, @bg_color)
    base[ACTIVE]      = shade (0.75, @bg_color)
    base[SELECTED]    = @selected_bg_color
    base[INSENSITIVE] = @bg_color

    text[NORMAL]      = @text_color
    text[PRELIGHT]    = @text_color
    text[ACTIVE]      = @selected_fg_color
    text[SELECTED]    = @selected_fg_color
    text[INSENSITIVE] = darker (@bg_color)

    engine "murrine" 
    {
        contrast        = 1.0 # theme contrast.
        glazestyle        = 0 # 0 = flat hilight, 1 = curved hilight, 2 = concave style, 3 = top curved hilight, 4 = beryl hilight.
        menubarstyle        = 0 # 0 = flat, 1 = glassy, 2 = gradient, 3 = striped.
        menubaritemstyle    = 1 # 0 = menuitem look, 1 = button look.
        menuitemstyle        = 1 # 0 = flat, 1 = glassy, 2 = striped.
        listviewheaderstyle    = 1 # 0 = flat, 1 = glassy, 2 = raised.
        listviewstyle        = 0 # 0 = nothing, 1 = dotted.
scrollbarstyle = 2 # 0 = nothing, 1 = circles, 2 = handles, 3 = diagonal stripes, 4 = diagonal stripes and handles, 5 = horizontal stripes, 6 = horizontal stripes and handles.
        stepperstyle        = 1 # 0 = standard, 1 = integrated stepper handles.
        roundness        = 2 # Overall roundness of the theme.
#        progressbarstyle    = 1 # 0 = nothing, 1 = striped, 2 = cells
        animation        = TRUE  # FALSE disables progressbar animations.
                gradients        = TRUE # enables gradients.
        reliefstyle        = 2 # shadows around widgets.
        sliderstyle        = 1 # 0 = nothing added, 1 = handles.
        menustyle        = 0 # removes stripes from menus.
        rgba            = FALSE # disables rgba.
        lightborder_shade    = 1.20 # sets lightborder amount for buttons or widgets.
        lightborderstyle    = 1 # 0 = lightborder on top side, 1 = lightborder on all sides.
        highlight_shade        = 1.04 # shade for gradient hightlight.
        gradient_shades        = {1.09,1.01,1.01,0.91} # rendering of gradients.
   }
}

#################
# THEME MODULES 
#################
style "evolution-hack" = "murrine-default" # Hacks for Evolution Mail.
{    
    bg[NORMAL]    = shade (1.14, @bg_color) # Color for evo treeview headers.
    bg[PRELIGHT]    = shade (1.18, @bg_color) # Color for evo treeview header prelight.
    bg[ACTIVE]    = shade (0.75, @bg_color) # Color for unfocused evo selected items.
    bg[SELECTED]    = @selected_bg_color # Color for evo selected items.
    fg[ACTIVE]      = @selected_fg_color # Color for evo active text.
    fg[SELECTED]    = @selected_fg_color # Color for evo selected text.
}

style "murrine-wide"
{
    xthickness = 2 # Can't change, or clowns will eat you.
    ythickness = 2 # Can't change, or clowns will eat you.
}

style "murrine-wider"
{
    xthickness = 3 # Can't change, or clowns will eat you.
    ythickness = 3 # Can't change, or clowns will eat you.
}

style "murrine-entry" = "murrine-wider" {

    bg[SELECTED] = mix (0.4, @selected_bg_color, @base_color)
    fg[SELECTED] = @text_color

    engine "murrine" {
        focus_color = shade (0.65, @selected_bg_color)
    }
}

style "murrine-button" = "murrine-wider"
{
    bg[NORMAL]    = shade (1.14, @bg_color) # Color for buttons.
    bg[PRELIGHT]    = shade (1.18, @bg_color) # Color for button-prelight.
    bg[ACTIVE]    = shade (0.85, @bg_color) # Color for pressed-buttons.
      engine "murrine" 
    {
        contrast = 1.20  # Button border contrast.
    }
}

style "murrine-notebook-bg"
{
    bg[NORMAL]    = shade (1.1, @bg_color) # Tab background.
    bg[ACTIVE]    = @bg_color # Unfocused tab background.
}

style "murrine-notebook" = "murrine-notebook-bg"
{
    xthickness = 2 # Width of tabs and notebook borders.
    ythickness = 2 # Height of tabs and notebook borders.
    engine "murrine" 
    {
        roundness = 0 # Roundness of notebook tabs.
    }
}

style "murrine-menu" # This section themes custom dark menus. Leave as is.
{
    ythickness = 0
    xthickness = 0
    bg[SELECTED]    = shade (0.85, @selected_bg_color)
    bg[NORMAL]    = "#000000"
    bg[PRELIGHT]    = shade (0.85, @selected_bg_color)
    bg[ACTIVE]    = "#333333"
    bg[INSENSITIVE]    = "#3C3C3C"
    fg[NORMAL]    = "#E6E6E6" # Color for normal text.
    fg[PRELIGHT]    = @selected_fg_color
    fg[SELECTED]    = @selected_fg_color
    fg[ACTIVE]    = @selected_fg_color
    fg[INSENSITIVE]    = "#666666"
    text[NORMAL]    = @base_color # Color for menu-item radio/checks.
    base[NORMAL]    = "#666666" # Color for menu-item radio/checks background.
    text[PRELIGHT]    = @selected_fg_color
    text[SELECTED]    = @selected_fg_color
    text[ACTIVE]    = @selected_fg_color
    text[INSENSITIVE]    = "#666666"
    engine "murrine" 
    {
        roundness = 0 # Roundness of menu items.
    }
}

style "murrine-menu-item" = "murrine-wider"
{
    bg[SELECTED]    = shade (0.85, @selected_bg_color)
    bg[PRELIGHT]    = shade (0.85, @selected_bg_color)
    fg[NORMAL]    = "#E6E6E6" # Fix for XFCE menu text.
    fg[PRELIGHT]    = @selected_fg_color
    fg[SELECTED]    = @selected_fg_color
}

style "murrine-separator-menu-item"
{
    GtkSeparatorMenuItem::horizontal-padding = 4
    # We are setting the desired height by using wide-separators.
    # There is no other way to get the odd height ...
    GtkWidget::wide-separators = 1
    GtkWidget::separator-width = 1
    GtkWidget::separator-height = 7
    xthickness = 1
    ythickness = 0
}

style "murrine-menubar" # This section deals with dark menubars. Leave as is.
{
    ythickness = 0
    bg[SELECTED]    = shade (0.85, @selected_bg_color)
    bg[NORMAL]    = "#000000" # Background color for menubars.
    bg[PRELIGHT]    = shade (0.85, @selected_bg_color)
    bg[ACTIVE]    = "#000000"
    bg[INSENSITIVE]    = "#3C3C3C"
    fg[NORMAL]    = "#E6E6E6" # Color for normal text.
    fg[PRELIGHT]    = @selected_fg_color
    fg[SELECTED]    = @selected_fg_color
    fg[ACTIVE]    = @selected_fg_color
    fg[INSENSITIVE]    = "#666666"
    text[NORMAL]    = "#E6E6E6"
    text[PRELIGHT]    = @selected_fg_color
    text[SELECTED]    = @selected_fg_color
    text[ACTIVE]    = @selected_fg_color
    text[INSENSITIVE]    = "#666666"
}

style "murrine-treeview"
{
      engine "murrine" 
    {
        roundness = 0  # This makes treeview progressbars square.
    }
}

style "murrine-treeview-header" = "murrine-button"
{
    xthickness = 2
    ythickness = 1
    bg[NORMAL]    = shade (1.14, @bg_color)  # Color for treeview headers.
    bg[PRELIGHT]    = shade (1.18, @bg_color)  # Color for treeview header prelight.
    bg[ACTIVE]    = shade (0.85, @bg_color)  # Color for pressed-treeview.
      engine "murrine" 
    {
        roundness    = 0  # This makes treeview progressbars square.
    }
}

style "murrine-frame-title"
{
    fg[NORMAL]    = lighter (@fg_color)
}

style "murrine-tooltips" = "murrine-wider"
{
    bg[NORMAL]    = @tooltip_bg_color
    fg[NORMAL]    = @tooltip_fg_color
}

style "metacity-frame" = "murrine-default"
{
    bg[SELECTED]    = shade (0.85, @selected_bg_color)  # Color for metacity borders.
}

style "murrine-progressbar"
{
    xthickness = 0
    ythickness = 0
    fg[PRELIGHT]    = @selected_fg_color  # Progressbar prelighted text.
    engine "murrine" 
    {
    roundness    = 0 # Progressbar roundness.
    }
}

style "murrine-statusbar"
{
    xthickness = 2
}

style "murrine-comboboxentry"
{
}

style "murrine-spinbutton"
{
    bg[ACTIVE]   = shade (0.85, @bg_color)  # Color for pressed-spinbuttons.
}

style "murrine-scale" = "murrine-button"
{
    GtkRange       ::slider-width    = 15 # Width of sliders.
    bg[NORMAL]    = shade (1.14, @bg_color) # Color for sliders.
    bg[PRELIGHT]    = shade (1.18, @bg_color) # Color for slider prelight.
    bg[ACTIVE]    = shade (0.85, @bg_color) # Color for pressed-sliders.
      engine "murrine" 
    {
        contrast = 1.20  # Slider border contrast.
    }
}

style "murrine-hscale" = "murrine-scale"
{
}

style "murrine-vscale" = "murrine-scale"
{
}

style "murrine-nautilus-location" # Workaround for nautilus' messages.
{
    bg[NORMAL]    = shade (1.25, @selected_bg_color)
}

style "murrine-radiocheck" = "murrine-default"
{
    text[NORMAL]    = @selected_fg_color # Color for checks/radio items.
    text[PRELIGHT]    = @selected_fg_color # Color for checks/radio items.
}

##############
# SCROLLBARS
##############
style "murrine-scrollbar"
{
#    GtkScrollbar::trough-border    = 0 # Change to a higher value for border around scrollbars.
    bg[NORMAL]    = shade (1.14, @bg_color) # Color for non-colored scrollbars.
    bg[INSENSITIVE]    = @bg_color # Color for non-colored scrollbars.
    bg[PRELIGHT]    = @bg_color # Color for scrollbar prelight? (probably obsolete)
    bg[ACTIVE]    = @bg_color # Color for scrollbar rail's background.
    bg[SELECTED]    = @selected_bg_color # Color of scrollbars.
    fg[PRELIGHT]    = shade (0.60, @selected_bg_color) # Highlighted scrollbar button.
    fg[ACTIVE]    = shade (0.40, @selected_bg_color) # Pressed scrollbar button.
    engine "murrine" 
    {
        colorize_scrollbar    = FALSE # Commenting this out gives you colorful scrollbars.
        roundness        = 0 # Scrollbar roundness.
        contrast        = 1.20 # Makes scrollbar's rail borders darker.
    }
}

style "murrine-hscrollbar" = "murrine-scrollbar"
{
}

style "murrine-vscrollbar" = "murrine-scrollbar"
{
}

############
# TOOLBARS
############
# Gradient toolbars are disabled for this theme. Follow these instructions to enable them:
# 1. Comment out the line in this file that starts with "GtkToolbar::shadow-type".
# 2. Uncomment the following:

#style "murrine-toolbar" = "murrine-default"
#{
#    engine "murrine"
#    {
#        toolbarstyle = 2  # This forces gradient toolbars.
#    }
#}

#style "murrine-evo-new-button-workaround"
#{
#    engine "murrine"
#    {
#        toolbarstyle = 0
#    }
#}
#widget_class "EShellWindow.GtkVBox.BonoboDock.BonoboDockBand.BonoboDockItem*" style "murrine-evo-new-button-workaround"

#class "GtkToolbar"   style "murrine-toolbar" 
#class "GtkHandleBox" style "murrine-toolbar"


###############################################################################
# The following part of the gtkrc applies the different styles to the widgets.
###############################################################################

# Murrine default style is applied to every widget.
class "GtkWidget"    style "murrine-default"

# Increase the x/ythickness in some widgets.
class "GtkFrame"     style "murrine-wide"
class "GtkEntry"     style "murrine-entry"
class "MetaFrames"   style "metacity-frame"
class "GtkSeparator" style "murrine-wide"
class "GtkWindow"    style "metacity-frame"
class "GtkCalendar"  style "murrine-wide"

class "GtkSpinButton"  style "murrine-spinbutton"
class "GtkScale"       style "murrine-scale"
class "GtkVScale"      style "murrine-vscale"
class "GtkHScale"      style "murrine-hscale"
class "GtkScrollbar"   style "murrine-scrollbar"
class "GtkVScrollbar"  style "murrine-vscrollbar"
class "GtkHScrollbar"  style "murrine-hscrollbar"

class "GtkRadio*"    style "murrine-radiocheck"
class "GtkCheck*"    style "murrine-radiocheck"

# General matching following, the order is choosen so that the right styles override each other eg. progressbar needs to be more important then the menu match.

# This is not perfect, it could be done better (That is modify *every* widget in the notebook, and change those back that we really don't want changed)
widget_class "*<GtkNotebook>*<GtkEventBox>"     style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkDrawingArea>"  style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkLayout>"       style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkViewport>"    style "murrine-notebook-bg"
widget_class "*<GtkNotebook>*<GtkScrolledWindow>"    style "murrine-notebook-bg"

widget_class "*<GtkButton>"      style "murrine-button"
widget_class "*<GtkNotebook>"    style "murrine-notebook"
widget_class "*<GtkStatusbar>*"  style "murrine-statusbar"

widget_class "*<GtkComboBoxEntry>*" style "murrine-comboboxentry"
widget_class "*<GtkCombo>*"         style "murrine-comboboxentry"

widget_class "*<GtkMenuBar>*"           style "murrine-menubar"
widget_class "*<GtkMenu>*"              style "murrine-menu"
widget_class "*<GtkMenuItem>*"          style "murrine-menu-item"
widget_class "*<GtkSeparatorMenuItem>*" style "murrine-separator-menu-item"

widget_class "*.<GtkFrame>.<GtkLabel>" style "murrine-frame-title"
widget_class "*.<GtkTreeView>*"        style "murrine-treeview"

widget_class "*<GtkProgress>"           style "murrine-progressbar"
widget_class "*<GtkProgressBar>"       style "murrine-progressbar"

# Treeview header
widget_class "*.<GtkTreeView>.<GtkButton>" style "murrine-treeview-header"
widget_class "*.<GtkCTree>.<GtkButton>"    style "murrine-treeview-header"
widget_class "*.<GtkList>.<GtkButton>"     style "murrine-treeview-header"
widget_class "*.<GtkCList>.<GtkButton>"    style "murrine-treeview-header"

# Workarounds for Evolution
widget_class "*.ETable.ECanvas"    style "murrine-treeview-header"
widget_class "*.ETree.ECanvas"    style "murrine-treeview-header"
widget_class "*GtkCTree*"    style "evolution-hack"
widget_class "*GtkList*"    style "evolution-hack"
widget_class "*GtkCList*"    style "evolution-hack"
widget_class "*.ETree.*"    style "evolution-hack"
widget_class "*EInfoLabel*"    style "evolution-hack"

# The window of the tooltip is called "gtk-tooltip"
################################
# FIXME:
# This will not work if one embeds eg. a button into the tooltip.
# As far as I can tell right now we will need to rework the theme
# quite a bit to get this working correctly.
# (It will involve setting different priorities, etc.)
################################
widget "gtk-tooltip*" style "murrine-tooltips"

###################################################
# SPECIAL CASES AND WORKAROUNDS
###################################################

# Special case the nautilus-extra-view-widget
# ToDo: A more generic approach for all applications that have a widget like this.
widget "*.nautilus-extra-view-widget" style : highest "murrine-nautilus-location"

# Work around for [http://bugzilla.gnome.org/show_bug.cgi?id=382646](http://bugzilla.gnome.org/show_bug.cgi?id=382646)
# Note that the work around assumes that the combobox is _not_ in appears-as-list mode.
# This style does not affect GtkComboBoxEntry, it does have an effect on comboboxes in appears-as-list mode though.
style "murrine-text-is-fg-color-workaround"
{
    text[NORMAL]      = @fg_color
    text[PRELIGHT]    = @fg_color
    text[SELECTED]    = @selected_fg_color
    text[ACTIVE]      = @fg_color
    text[INSENSITIVE] = darker (@bg_color)
}
widget_class "*.<GtkComboBox>.<GtkCellView>"   style "murrine-text-is-fg-color-workaround"

style "murrine-menuitem-text-is-fg-color-workaround"
{
    text[NORMAL]        = "#E6E6E6"
    text[PRELIGHT]      = @selected_fg_color
    text[SELECTED]      = @selected_fg_color
    text[ACTIVE]        = @fg_color
    text[INSENSITIVE]   = darker (@bg_color)
}
widget "*.gtk-combobox-popup-menu.*"   style "murrine-menuitem-text-is-fg-color-workaround"

# Work around the usage of GtkLabel inside GtkListItems to display text.
# This breaks because the label is shown on a background that is based on the base color set.
style "murrine-fg-is-text-color-workaround"
{
    fg[NORMAL]      = @text_color
    fg[PRELIGHT]    = @text_color
    fg[ACTIVE]      = @selected_fg_color
    fg[SELECTED]    = @selected_fg_color
    fg[INSENSITIVE] = darker (@bg_color)
}
widget_class "*<GtkListItem>*" style "murrine-fg-is-text-color-workaround"
# The same problem also exists for GtkCList and GtkCTree.
# Only match GtkCList and not the parent widgets, because that would also change the headers.
widget_class "*<GtkCList>" style "murrine-fg-is-text-color-workaround"
widget_class "*<EelEditableLabel>" style "murrine-fg-is-text-color-workaround"

# The answer to the ultimate question of life, the universe, and everything is 42.
[/INDENT]I like messing around with these things but I could never figure out how to change the color of the very top bar. Any help would be greatly appreciated! [IMG]http://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

---

### Post by crimesaucer on 2009-12-05
> **vie et mort said:**
> Anyone know how to change the color of this gtkrc's titlebar / frame? Not sure what exactly its called but its the bar all the way at the top of any open window, right above the menu-bar and it says the name of whatever you have open.
I like messing around with these things but I could never figure out how to change the color of the very top bar. Any help would be greatly appreciated! [IMG]http://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

Did you try changing these:

```

bg[SELECTED]
bg[INSENSITIVE]

```

This worked for my xfwm4 color using murrine (active window and inactive window).

Your murrine theme is written differently than the ones that I use, and I'm not sure if you use xfwm4 or metacity or something else so my answer might not work.

---

### Post by greco on 2010-01-12
Here's another one...

I'm running Elegant-Brit and I love it. The only thing is that I would like to have the dark gray border around the windows as opposed to the default white. I tried searching the intraweb to find which settings I need to change in the gtkrc to get the border color I want but I am SOL.

Does anyone know the attributes I need to add to the gtkrc file to change the border color of windows (gnome-terminal, firefox, etc..)

Thanks in advance.

---

### Post by bander013 on 2010-01-23
As I was able to find out, bg[INSENSITIVE] is a color of RB menu, Main menu and url-guess-popup variants in Firefox

My problem is I can't change only color for 'url-guess-popup' background

I don't actually know what 'url-guess-popup' real name. If you start type some firefox url in address bar, it will roll down with variants, that's it. And I desperately need to change it bg color.

Please, give me a hand X)

---

### Post by AzureCerulean on 2010-01-29
Look at The Widget Laboratory, a Gtk theme viewer/editor.


[http://blog.mahboy.com/archives/174]("http://blog.mahboy.com/archives/174")

it's not so much an editor but a viewer loader, that lets you instantly see changes you have made to your thme.

I have searched everywhere and this is the closest thing I can find at this time.

---

### Post by lion833 on 2010-01-29
:o:o:o

It's perfect tutorial, I have to learn it, thanks very much&#65281;

---

### Post by acidrums4 on 2010-04-17
I have a question... How do I change the text color of cell items in a treeview, but only the cell items (without changing text[NORMAL] for the theme defaults?

Sorry for my bad-level english!

---

### Post by at_pradeep on 2010-04-23
nice thread!...

I am experimenting with pixmap engine. 

How can i archive following things:

1. Alternate row color for GtkMenuItems.
2. Set bold font for GtkEntry or whole of the application?
3. Set Background image to GtkTextView Widget.

I tried some test but every thing seems to fail.
can some one please explain this to me.


Thanks,
PP.

---

### Post by dannymichel on 2010-04-25
With your help, i edited [Rezlooks-Soft-Gray]("http://www.imagebam.com/image/19586e77895475")
[IMG]http://www.imagebam.com/image/19586e77895475[/IMG]
[[IMG]http://thumbnails11.imagebam.com/7790/19586e77895475.gif[/IMG]](http://www.imagebam.com/image/19586e77895475)

---

### Post by dannymichel on 2010-05-05
Noob question; i'm trying to have menu bar items 'etched-in'. can anyone help me with that?

---

### Post by crimesaucer on 2010-05-08
> **greco said:**
> Here's another one...

I'm running Elegant-Brit and I love it. The only thing is that I would like to have the dark gray border around the windows as opposed to the default white. I tried searching the intraweb to find which settings I need to change in the gtkrc to get the border color I want but I am SOL.

Does anyone know the attributes I need to add to the gtkrc file to change the border color of windows (gnome-terminal, firefox, etc..)

Thanks in advance.

Are you talking about the window borders with that 2 pixel white outline?... if you are then let me know which window manager you're using (xfwm4, metacity, emerald.. etc.)

If you use xfwm4 with xfce4 then you would need to edit the xpm files (very easy)... I'm not sure how to do it with metacity (could maybe figure it out?), and with and emerald theme it should be easy to fix.

---

### Post by lancerocke on 2010-05-08
> **crimesaucer said:**
> Are you talking about the window borders with that 2 pixel white outline?... if you are then let me know which window manager you're using (xfwm4, metacity, emerald.. etc.)

If you use xfwm4 with xfce4 then you would need to edit the xpm files (very easy)... I'm not sure how to do it with metacity (could maybe figure it out?), and with and emerald theme it should be easy to fix.no, i don't mean windows border's but that would be nice to know too, for metacity and emerald. more importantly, i want to know how to have a white outline under the text, and not all around the text, making it looked 'etched it' [[IMG]http://imgur.com/j25gB.png[/IMG]](http://imgur.com/j25gB.png)

and see where it says 'option' here?
it's only under the top text, not all around it

[[IMG]http://imgur.com/t1U7E.png[/IMG]](http://imgur.com/t1U7E.png)

---

### Post by crimesaucer on 2010-05-08
> **lion833 said:**
> :o:o:o

It's perfect tutorial, I have to learn it, thanks very much&#65281;

Thank you, the info is pretty old, and sort of incomplete... when I wrote this I was learning to theme gtkrc files through trial and error.

But like I said, I stopped writing themes for the xfce4 engine and pretty much just use the murrine engine cause it looks so nice and is very easy to figure out and customize.

Having recently switched to Gnome (less maintenance than the combo of xmonad and xfce4 that I had been using for the last few years), so this is one of my newer murrine looks:

[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple-1.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple.png)

[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple2-1.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple2.png)


> **acidrums4 said:**
> I have a question... How do I change the text color of cell items in a treeview, but only the cell items (without changing text[NORMAL] for the theme defaults?

Sorry for my bad-level english!


Sorry, I'm not sure.

---

### Post by crimesaucer on 2010-05-08
> **lancerocke said:**
> no, i don't mean windows border's but that would be nice to know too, for metacity and emerald. more importantly, i want to know how to have a white outline under the text, and not all around the text, making it looked 'etched it' 

and see where it says 'option' here?
it's only under the top text, not all around it

I'm not sure about the text... I see what you're saying... the only etched in/out shadows I know how to do is for toolbars and menubars by using:

```

GtkMenuBar::shadow_type           = out
GtkMenuItem::selected_shadow_type = none
GtkToolbar::shadow_type           = out

```

Sorry I can't help.

---

### Post by crimesaucer on 2010-05-08
> **dannymichel said:**
> Noob question; i'm trying to have menu bar items 'etched-in'. can anyone help me with that?

Sorry, like the comments above I'm not sure how to do that. The only etched-in/out/none that I know of is these:

```

GtkMenuBar::shadow_type           = out
GtkMenuItem::selected_shadow_type = in
GtkToolbar::shadow_type           = none

```

---

### Post by lancerocke on 2010-05-08
> **crimesaucer said:**
> Thank you, the info is pretty old, and sort of incomplete... when I wrote this I was learning to theme gtkrc files through trial and error.

But like I said, I stopped writing themes for the xfce4 engine and pretty much just use the murrine engine cause it looks so nice and is very easy to figure out and customize.

Having recently switched to Gnome (less maintenance than the combo of xmonad and xfce4 that I had been using for the last few years), so this is one of my newer murrine looks:

[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple-1.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple.png)

[[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple2-1.png[/IMG]](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-purple2.png)





Sorry, I'm not sure.what font is that? 8px?8.somethingpx? lucida? segoi?

> **crimesaucer said:**
> I'm not sure about the text... I see what you're saying... the only etched in/out shadows I know how to do is for toolbars and menubars by using:

```

GtkMenuBar::shadow_type           = out
GtkMenuItem::selected_shadow_type = none
GtkToolbar::shadow_type           = out

```

Sorry I can't help.
ok, np. i'll try to ask somewhere/one else.

---

### Post by crimesaucer on 2010-05-08
> **lancerocke said:**
> what font is that? 8px?8.somethingpx? lucida? segoi?

the font is Lucida Grande:size=8 (from an Apple fonts package that I found a few years back), and the conky font is "LucidaConsole:size=7" from the same package.

---

### Post by lancerocke on 2010-05-08
> **crimesaucer said:**
> the font is Lucida Grande:size=8 (from an Apple fonts package that I found a few years back), and the conky font is "LucidaConsole:size=7" from the same package.
cool. is 8px the default mac size, do you think?

---

### Post by crimesaucer on 2010-05-08
> **lancerocke said:**
> cool. is 8px the default mac size, do you think?

I'm not sure, I've never used a mac before.

---

### Post by PhotonicGuy on 2010-05-10
Nice topic! I'll try it myself

---

### Post by lancerocke on 2010-05-13
is there a way to control font line spacing in gtk themes?

---

### Post by mitra_jit2005 on 2010-05-18
y isn't this post made a sticky yet ??? i ws searching for this, for a year nw...wl post my themes within few dayzzz..

---

### Post by Crazedpsyc on 2010-05-28
I realize this is rather old, but before I start a new thread I want to check: Do you know how to let the gnome appearance editor change the colors? I tried using   base[PRELIGHT]    = "*"
but that just made everything gray and ugly.
also: how can I specify the color for the text in the gnome menu? I got it to change, but it took all the button text with it

---

### Post by crimesaucer on 2010-06-01
> **Crazedpsyc said:**
> I realize this is rather old, but before I start a new thread I want to check: Do you know how to let the gnome appearance editor change the colors? I tried using   base[PRELIGHT]    = "*"
but that just made everything gray and ugly.
also: how can I specify the color for the text in the gnome menu? I got it to change, but it took all the button text with it

Use a "gtk_color_scheme =" line at the very top of your gtkrc (look below). The gnome-appearance-editor will be able to edit the colors of your theme (be sure to use the "\n" like is shown below):

This is an example from the popular "murrine glow orange" (not one of mine)
```

# This can be overriden (via an xsetting) with eg. the gnome-appearance-properties.
gtk_color_scheme = "fg_color:#222222\nbg_color:#dedede\nbase_color:#f5f5f5\ntext_color:#292929\nselected_bg_color:#db6b2a\nselected_fg_color:#ffffff\ntooltip_bg_color:#efe6c3\ntooltip_fg_color:#333333"

```

The "gtk_color_scheme =" line is used throughout the gtkrc like this:

```

        fg[NORMAL]        = @fg_color
	fg[PRELIGHT]      = @fg_color
	fg[SELECTED]      = @selected_fg_color
	fg[INSENSITIVE]   = darker (@bg_color)
	fg[ACTIVE]        = @fg_color

	bg[NORMAL]		=  @bg_color
	bg[ACTIVE]		=  shade (1.02, @bg_color)
	bg[PRELIGHT]		=  shade (1.05, @bg_color)
	bg[SELECTED]		=  @selected_bg_color
	bg[INSENSITIVE]		=  shade (1.03,@bg_color)

	base[NORMAL]      = @base_color
	base[PRELIGHT]    = @base_color
	base[SELECTED]    = @selected_bg_color
	base[INSENSITIVE] = @bg_color
	base[ACTIVE]      = shade (0.9, @selected_bg_color)

	text[NORMAL]      = @text_color
	text[PRELIGHT]    = @text_color
	text[SELECTED]    = @selected_fg_color
	text[INSENSITIVE] = darker (@bg_color)
	text[ACTIVE]      = @selected_fg_color

```



Make sure you use these correct names of:

fg_color
bg_color
base_color
text_color
selected_bg_color
selected_fg_color
tooltip_bg_color
tooltip_fg_color


..... otherwise it won't work.



I don't use the correct names in my themes (so the "gnome color edit" doesn't work with my themes), since I like to use descriptive names in my gtkrc files: 

This is part of my gtkrc that shows my "gtk_color_scheme =" and the way I use it in the color part of the "style "default" :

```
gtk_color_scheme = "black_text:#000\ndark_menubar:#1D1D1F\ntext_editor_bg:#D0BCFD\nmenu_roll_over:#212124\ntoolbar_color:#e0e0e0\nbuttons:#e1e1e0\nstriped_progress_bar:#66458F\ninactive_tab:#C8BCE0\nopen_tab_bg:#D4C7ED\nwhite_text:#FFFFFF\ntext_neon_purple:#BCA2F9\nurl_outline:#AE75F6\ntext_insensitive:#5C507A\nbox_bg_trash:#BCA2F9"


fg[NORMAL]        = @black_text   # option menu, button font, open tab
fg[PRELIGHT]      = @black_text # font color of menurollover and rollover for radio/check boxes as well as button,Optionbutton,andtogglebutton prelights.
fg[SELECTED]      = @box_bg_trash # Gtkcombo font on dropdown selection - NOT GTK COMBO BOX!   
fg[ACTIVE]        = @black_text # pre-toggle font color, and active pre-toggle font for check/radio boxes, also for un-clicked regular tabs.
fg[INSENSITIVE]   = @text_insensitive # little arrows on scrolls

bg[NORMAL]        = shade (1.00, @toolbar_color) ## "#E2E2E2"
bg[PRELIGHT]      = shade (1.00, @box_bg_trash) ## background of text toggle mouse-over
bg[SELECTED]      = shade (1.00, @striped_progress_bar)      # menu selected roll over, and xfwm4 color 
bg[INSENSITIVE]   = @toolbar_color     # background scroll arrows
bg[ACTIVE]        = shade (1.00, @inactive_tab) # this (strangely) controls inactive tab BGs

base[NORMAL]      = @text_editor_bg     ## "#FFFFFF"
base[PRELIGHT]    = shade (1.00, @toolbar_color)     ## "#878887"
base[ACTIVE]      = shade (1.00, @menu_roll_over)     ## thunar detailed view - off window
base[SELECTED]    = shade (1.00, @menu_roll_over)     ## thunar detailed view - on window
base[INSENSITIVE] = @toolbar_color     ## "#878887"

text[NORMAL]      = @black_text     # font color for combo box (lame setting)
text[PRELIGHT]    = @black_text     # changes the check mark in radio boxes 
text[ACTIVE]      = @text_neon_purple     ## "#000001"
text[SELECTED]    = @white_text      ## "#FFFFFF"
text[INSENSITIVE] = darker (@toolbar_color)     ## "#4b4440"

```

---

### Post by kyle.huff on 2010-06-11
> **acidrums4 said:**
> I have a question... How do I change the text color of cell items in a treeview, but only the cell items (without changing text[NORMAL] for the theme defaults?

Sorry for my bad-level english!

You would do something like this in your gtkrc file:

style "CellView"
{
  text[NORMAL]		= "#ffffff"
}

class "GtkCellView" style "CellView"

widget_class "*CellView*"   style "CellView"
class "*CellView*"          style "CellView"

Hope that helps

---

### Post by Crazedpsyc on 2010-06-17
Thanks guys! It did help a lot! But look at this:
> 
gtk_color_scheme = "fg_color:#FF8576\nbg_color:#ffffff\nbase_color:#1f1f1f\nselected_bg_color:#4f4e57\nselected_fg_color:#ffffff"
style "dark-alloy-default"
{
    GtkWidget::focus_padding = 0
    
    GtkFrame::shadow_type = GTK_SHADOW_OUT
    GtkScrolledWindow::shadow_type = GTK_SHADOW_OUT
    GtkMenuBar::shadow_type = GTK_SHADOW_OUT
    GtkToolbar::shadow_type = GTK_SHADOW_OUT
    
    GtkTreeView::odd_row_color = "#424242"
    GtkTreeView::even_row_color = "#000000"
    
    bg_pixmap[NORMAL] = "default_seamless.png"

    xthickness = 2
    ythickness = 2

    fg[NORMAL] = @fg_color
    fg[PRELIGHT] = "#d8d8d8"
    fg[ACTIVE] = "#d8d8d8"
    fg[SELECTED] = @selected_fg_color
    fg[INSENSITIVE] = "#404040"

    bg[NORMAL] = @bg_color
    bg[PRELIGHT] = "#A08350"
    bg[ACTIVE] = "#4f4e57"
    bg[SELECTED] = @selected_bg_color
    bg[INSENSITIVE] = "#27282f"

    text[NORMAL] = "#FF8576"
    text[PRELIGHT] = "#ffffff"
    text[ACTIVE] = "#ffffff"
    text[SELECTED] = "#ffffff"
    text[INSENSITIVE] = "#264372"

    base[NORMAL] = base_color
    base[PRELIGHT] = "#5073A0"
    base[ACTIVE] = "#4f4e57"
    base[SELECTED] = "#4f4e57" 
    base[INSENSITIVE] = "#27282f"
...

it makes everything grey and black (the default gnome) and the colors still won't change. I used almost the exact same thing (different colors) for another theme, and it works great.
EDIT: yeah I missed the @, oops, now it works, but still don't know this:
also, where do I put (and what do I call) the thingies with the @s and stuff for "Tooltips:"

---

