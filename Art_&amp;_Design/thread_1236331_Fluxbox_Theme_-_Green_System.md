---
title: "Fluxbox Theme - Green System"
date: 2009-08-10
forum: Art &amp; Design
---

### Post by Narada on 2009-08-10
Looks great with [this](http://hlaurah.deviantart.com/art/Gutter-Glitter-118271741), url=http://narada.deviantart.com/art/Octo-Spiral-3-Widescreen-128404634]this[/url] wallpaper or anything else similar in color to Underground System's 'Green System' forum style.

Paste the following theme file into ~/.fluxbox/styles and you're good to go. No pixmaps or extra files are needed. Let me know if you find any bugs.

Screenshot: [[IMG]http://img297.imageshack.us/img297/3985/fluxthemegreen.th.jpg[/IMG]](http://img297.imageshack.us/img297/3985/fluxthemegreen.jpg)
```
##################################################
# Underground Systems (Green) Fluxbox style v0.2 #
# Author: Narada                  Date: 05.2009  #
##################################################
# Note: This theme is intended for use with Artwiz fonts.
# Get them here: http://sourceforge.net/project/showfiles.php?group_id=95348
# (Dependencies not included.)
#
# Directions:  Paste this file to your ~/.fluxbox/styles directory. It should 
#              automatically be added to your Fluxbox menu's styles list. If 
#              so, you're all done. If you do not have a styles list, modify 
#              the bottom of your Fluxbox menu (~/.fluxbox/menu) in a text 
#              editor to show the following, and save.
# Find this:
# [submenu] (fluxbox menu)
# [config] (Configure) 
# And add this:
# [submenu] (User Styles) {Choose a style...}
#      [stylesdir] (~/.fluxbox/styles) 
# [end]
#
# *** IMPORTANT ***
# Change "rootCommand: fbsetbg /path/to/wallpaper" to reflect your desired
# wallpaper. (ex. ~/images/backgrounds/fubar.jpg) Do not touch anything else!
#
#######################
# Begin Configuration #
#######################
*.font:                                 snap
rootCommand:                            fbsetbg /path/to/wallpaper

menu.borderColor:                       #FFFFFF
menu.borderWidth:                       1
menu.bullet:                            triangle
menu.bullet.position:                   right
menu.frame:                             flat gradient horizontal
menu.frame.color:                       #000000
menu.frame.colorTo:                     #003300
menu.frame.disableColor:                #00EE00
menu.frame.textColor:                   #FFFFFF
menu.frame.justify:                     left
menu.height:                            25
menu.hilite.color:                      #FFFFFF
menu.hilite.textColor:                  #000000
menu.title.color:                       #000000
menu.title.textColor:                   #FFFFFF
menu.title.justify:                     center

toolbar.borderColor:                    #FFFFFF
toolbar.borderWidth:                    1
toolbar.button.color:                   #000000
toolbar.button.picColor:                #FFFFFF
toolbar.button.pressed:                 flat solid
toolbar.button.pressed.color:           #00CD00
toolbar.clock.color:                    #000000
toolbar.clock.textColor:                #FFFFFF
toolbar.height:                         15
toolbar.iconbar.borderColor:            #FFFFFF
toolbar.iconbar.borderWidth:            1
toolbar.iconbar.empty:                  flat gradient rectangle
toolbar.iconbar.empty.color:            #000000
toolbar.iconbar.empty.colorTo:          #003300
toolbar.iconbar.focused:                flat gradient rectangle
toolbar.iconbar.focused.borderColor:    #000000
toolbar.iconbar.focused.borderWidth:    1
toolbar.iconbar.focused.color:          #000000
toolbar.iconbar.focused.colorTo:        #00EE00
toolbar.iconbar.focused.textColor:      #FFFFFF
toolbar.iconbar.unfocused:              sunken gradient rectangle
toolbar.iconbar.unfocused.borderColor:  #FFFFFF
toolbar.iconbar.unfocused.borderWidth:  0
toolbar.iconbar.unfocused.color:        #003300
toolbar.iconbar.unfocused.colorTo:      #000000
toolbar.iconbar.unfocused.textColor:    #7A7A7A
toolbar.justify:                        center
toolbar.systray:                        flat solid
toolbar.systray.color:                  #000000
toolbar.label.color:                    #000000
toolbar.label.textColor:                #FFFFFF
toolbar.label.borderColor:              #FFFFFF
toolbar.label.borderWidth:              1
toolbar.workspace.color:                #000000
toolbar.workspace.colorTo:              #FFFFFF
toolbar.workspace.textColor:            #FFFFFF

window.borderColor:                     #FFFFFF
window.borderWidth:                     1
window.button.focus.color:              #000000
window.button.focus.picColor:           #FFFFFF
window.button.pressed:                  raised gradient pyramid
window.button.pressed.color:            #000000
window.button.pressed.colorTo:          #00EE00
window.button.unfocus.color:            #000000
window.button.unfocus.picColor:         #FFFFFF
window.grip.focus.color:                #00CD00
window.grip.unfocus.color:              #003300
window.handle.focus.color:              #000000
window.handle.unfocus.color:            #000000
window.handleWidth:                     2
window.justify:                         center
window.label.focus:                     raised gradient rectangle
window.label.focus.color:               #000000
window.label.focus.colorTo:             #00EE00
window.label.focus.textColor:           #FFFFFF
window.label.unfocus:                   raised gradient rectangle
window.label.unfocus.color:             #000000
window.label.unfocus.colorTo:           #003300
window.label.unfocus.textColor:         #7A7A7A
window.title.focus.color:               #000000
window.title.height:                    15
window.title.unfocus.colorTo:           #FFFFFF

slit:                                   flat gradient rectangle
slit.bevelWidth:                        0
slit.borderColor:                       #FFFFFF
slit.borderWidth:                       1
slit.color:                             #000000
slit.colorTo:                           #003300
```

---

### Post by Narada on 2009-08-10
Looks great with [this](http://narada.deviantart.com/art/Liquid-Cool-102154739) wallpaper or anything else similar in color to Underground System's 'Blue System' forum style.

Paste the following theme file into ~/.fluxbox/styles and you're good to go. No pixmaps or extra files are needed. Let me know if you find any bugs.

Screenshot: [[IMG]http://img206.imageshack.us/img206/3861/fluxthemeblue.th.jpg[/IMG]](http://img206.imageshack.us/img206/3861/fluxthemeblue.jpg)
```
#################################################
# Underground Systems (Blue) Fluxbox style v0.2 #
# Author: Narada                  Date: 05.2009 #
#################################################
# Note: This theme is intended for use with Artwiz fonts.
# Get them here: http://sourceforge.net/project/showfiles.php?group_id=95348
# (Dependencies not included.)
#
# Directions:  Paste this file to your ~/.fluxbox/styles directory. It should 
#              automatically be added to your Fluxbox menu's styles list. If 
#              so, you're all done. If you do not have a styles list, modify 
#              the bottom of your Fluxbox menu (~/.fluxbox/menu) in a text 
#              editor to show the following, and save.
# Find this:
# [submenu] (fluxbox menu)
# [config] (Configure) 
# And add this:
# [submenu] (User Styles) {Choose a style...}
#      [stylesdir] (~/.fluxbox/styles) 
# [end]
#
# *** IMPORTANT ***
# Change "rootCommand: fbsetbg /path/to/wallpaper" to reflect your desired
# wallpaper. (ex. ~/images/backgrounds/fubar.jpg) Do not touch anything else!
#
#######################
# Begin Configuration #
#######################
*.font:                                 snap
rootCommand:                            fbsetbg /path/to/wallpaper

borderColor:			        #FFFFFF
bevelWidth:			        1
borderWidth:			        1
handleWidth:			        5

menu.borderColor:                       #FFFFFF
menu.borderWidth:                       1
menu.bullet:                            triangle
menu.bullet.position:                   right
menu.frame:                             flat gradient horizontal
menu.frame.color:                       #000000
menu.frame.colorTo:                     #152b3c
menu.frame.textColor:                   #FFFFFF
menu.frame.disableColor:                #ffff00
menu.frame.justify:                     left
menu.height:                            25
menu.hilite.color:                      #FFFFFF
menu.hilite.textColor:                  #000000
menu.roundCorners:                      TopRight TopLeft
menu.title.color:                       #000000
menu.title.justify:                     center
menu.title.textColor:                   #FFFFFF

toolbar.borderWidth:                    1
toolbar.borderColor:                    #FFFFFF
toolbar.button:                         flat solid
toolbar.button.color:                   #000000
toolbar.button.picColor:                #FFFFFF
toolbar.button.pressed:                 flat solid
toolbar.button.pressed.color:           #1464F4
toolbar.clock:                          flat solid
toolbar.clock.borderWidth:              0
toolbar.clock.borderColor:              #000000
toolbar.clock.color:                    #000000
toolbar.clock.colorTo:                  #152b3c
toolbar.clock.textColor:                #FFFFFF
toolbar.height:                         16
toolbar.iconbar.borderColor:            #FFFFFF
toolbar.iconbar.borderWidth:            0
toolbar.iconbar.empty:                  flat gradient rectangle
toolbar.iconbar.empty.color:            #000000
toolbar.iconbar.empty.colorTo:          #152b3c
toolbar.iconbar.focused:                flat gradient rectangle
toolbar.iconbar.focused.color:          #000000
toolbar.iconbar.focused.colorTo:        #1464F4
toolbar.iconbar.focused.textColor:      #FFFFFF
toolbar.iconbar.unfocused:              flat gradient rectangle
toolbar.iconbar.unfocused.color:        #000000
toolbar.iconbar.unfocused.colorTo:      #152b3c
toolbar.iconbar.unfocused.textColor:    #FFFFFF
toolbar.justify:                        center
toolbar.label.color:                    #FFFFFF
toolbar.label.textColor:                #000000
toolbar.systray:                        flat solid
toolbar.systray.color:                  #000000
toolbar.systray.colorTo:                #152b3c
toobar.workspace:                       flat gradient rectangle
toolbar.workspace.borderWidth:          0
toolbar.workspace.borderColor:          #FFFFFF
toolbar.workspace.color:                #000000
toolbar.workspace.colorTo:              #152b3c
toolbar.workspace.textColor:            #FFFFFF

window.bevelWidth:                      2
window.borderWidth:                     1
window.borderColor:                     #FFFFFF
window.button.focus.color:              #FFFFFF
window.button.focus.picColor:           #000000
window.button.unfocus.color:            #000000
window.button.unfocus.picColor:         #FFFFFF
window.button.pressed.color:            #1464F4
window.grip.focus.color:                #FFFFFF
window.grip.unfocus.color:              #000000
window.handleWidth:                     3
window.handle.focus:                    flat solid
window.handle.focus.color:              #152b3c
window.handle.unfocus.color:            #152b3c
window.justify:                         center
window.label.focus:                     flat gradient rectangle
window.label.focus.color:               #000b23
window.label.focus.colorTo:             #1464F4
window.label.focus.textColor:           #FFFFFF
window.label.unfocus:                   flat solid
window.label.unfocus.color:             #152b3c
window.label.unfocus.textColor:         #FFFFFF
window.title.height:                    16
window.title.focus.color:               #000000
window.title.unfocus.color:             #000000

slit:                                   flat solid
slit.bevelWidth:                        0
slit.color:                             #061229
```

---

### Post by Narada on 2009-08-10
[IMG]http://imgur.com/o3Lww.jpg[/IMG]
Looks great with [this](http://narada.deviantart.com/art/Alien-Hall-128373267) wallpaper or anything else similar in color to Underground System's 'Negative System' forum style.

Paste the following theme file into ~/.fluxbox/styles and you're good to go. No pixmaps or extra files are needed. Let me know if you find any bugs.

Screenshot: [[IMG]http://img329.imageshack.us/img329/9415/fluxthemenegative.th.jpg[/IMG]](http://img329.imageshack.us/my.php?image=fluxthemenegative.jpg)
```
#####################################################
# Underground Systems (Negative) Fluxbox style v0.2 #
# Author: Narada                      Date: 05.2009 #
#####################################################
# Note: This theme is intended for use with Artwiz fonts.
# Get them here: http://sourceforge.net/project/showfiles.php?group_id=95348
# (Dependencies not included.)
#
# Directions:  Paste this file to your ~/.fluxbox/styles directory. It should 
#              automatically be added to your Fluxbox menu's styles list. If 
#              so, you're all done. If you do not have a styles list, modify 
#              the bottom of your Fluxbox menu (~/.fluxbox/menu) in a text 
#              editor to show the following, and save.
# Find this:
# [submenu] (fluxbox menu)
# [config] (Configure) 
# And add this:
# [submenu] (User Styles) {Choose a style...}
#      [stylesdir] (~/.fluxbox/styles) 
# [end]
#
# *** IMPORTANT ***
# Change "rootCommand: fbsetbg /path/to/wallpaper" to reflect your desired
# wallpaper. (ex. ~/images/backgrounds/fubar.jpg) Do not touch anything else!
#
#######################
# Begin Configuration #
#######################
*.font:                                 snap
rootCommand:                            fbsetbg /path/to/wallpaper
borderColor:			        black
bevelWidth:			        1
borderWidth:			        1
handleWidth:			        5

menu.borderColor:                       #000000
menu.borderWidth:                       1
menu.bullet:                            triangle
menu.bullet.position:                   right
menu.frame:                             flat gradient horizontal
menu.frame.color:                       #FFFFFF
menu.frame.colorTo:                     #FFFFFF
menu.frame.textColor:                   #000000
menu.frame.disableColor:                #1464F4
menu.frame.justify:                     left
menu.height:                            25
menu.hilite.color:                      #000000
menu.hilite.textColor:                  #FFFFFF
menu.roundCorners:                      TopRight TopLeft
menu.title.color:                       #000000
menu.title.justify:                     center
menu.title.textColor:                   #FFFFFF

toolbar.borderWidth:                    1
toolbar.borderColor:                    #000000
toolbar.button.borderColor:             #000000
toolbar.button.borderWidth:             0
toolbar.button.color:                   #000000
toolbar.button.picColor:                #FFFFFF
toolbar.button.pressed:                 flat solid
toolbar.button.pressed.color:           #1464F4
toolbar.clock.borderWidth:              1
toolbar.clock.borderColor:              #000000
toolbar.clock.color:                    #FFFFFF
toolbar.clock.textColor:                #000000
toolbar.height:                         16
toolbar.iconbar.borderColor:            #000000
toolbar.iconbar.borderWidth:            1
toolbar.iconbar.empty:                  flat solid
toolbar.iconbar.empty.color:            #EEEEEE
toolbar.iconbar.focused:                flat solid 
toolbar.iconbar.focused.color:          #000000
toolbar.iconbar.focused.textColor:      #FFFFFF
toolbar.iconbar.unfocused:              flat solid
toolbar.iconbar.unfocused.color:        #EEEEEE
toolbar.iconbar.unfocused.textColor:    #000000
toolbar.justify:                        center
toolbar.systray:                        flat solid
toolbar.systray.color:                  #EEEEEE
toolbar.systray.colorTo:                #152b3c
toolbar.workspace.borderWidth:          1
toolbar.workspace.borderColor:          #000000
toolbar.workspace.color:                #FFFFFF
toolbar.workspace.textColor:            #000000
toolbar.label.color:                    #FFFFFF
toolbar.label.textColor:                #000000

window.borderWidth:                     1
window.borderColor:                     #000000
window.button.focus.color:              #FFFFFF
window.button.focus.picColor:           #000000
window.button.unfocus.color:            #000000
window.button.unfocus.picColor:         #FFFFFF
window.button.pressed.color:            #1464F4
window.grip.focus.color:                #FFFFFF
window.grip.unfocus.color:              #000000
window.handleWidth:                     2
window.handle.focus:                    flat solid
window.handle.focus.color:              #000000
window.handle.unfocus.color:            #FFFFFF
window.justify:                         center
window.label.focus:                     flat solid
window.label.focus.color:               #000000
window.label.focus.colorTo:             #EEEEEE
window.label.focus.textColor:           #FFFFFF
window.label.unfocus:                   flat solid
window.label.unfocus.color:             #FFFFFF
window.label.unfocus.textColor:         #000000
window.title.height:                    16
window.title.focus.color:               #FFFFFF
window.title.unfocus.colorTo:           #000000

slit:                                   flat solid
slit.bevelWidth:                        0
slit.borderWidth:                       1
slit.borderColor:                       #000000
slit.color:                             #FFFFFF
```

---

### Post by Narada on 2009-08-10
[IMG]http://imgur.com/quGPH.jpg[/IMG]
Looks great with [this](http://img29.imageshack.us/img29/3277/ergoproxynat.jpg) wallpaper or anything else similar in color to Underground System's 'Mono System' forum style.

Paste the following theme file into ~/.fluxbox/styles and you're good to go. No pixmaps or extra files are needed. Let me know if you find any bugs.

Screenshot*: [[IMG]http://img199.imageshack.us/img199/1673/fluxthememono.th.jpg[/IMG]](http://img199.imageshack.us/img199/1673/fluxthememono.jpg)
```
#################################################
# Underground Systems (Mono) Fluxbox style v0.3 #
# Author: Narada                  Date: 05.2009 #
#################################################
# Note: This theme is intended for use with Artwiz fonts.
# Get them here: http://sourceforge.net/project/showfiles.php?group_id=95348
# (Dependencies not included.)
#
# Directions:  Paste this file to your ~/.fluxbox/styles directory. It should 
#              automatically be added to your Fluxbox menu's styles list. If 
#              so, you're all done. If you do not have a styles list, modify 
#              the bottom of your Fluxbox menu (~/.fluxbox/menu) in a text 
#              editor to show the following, and save.
# Find this:
# [submenu] (fluxbox menu)
# [config] (Configure) 
# And add this:
# [submenu] (User Styles) {Choose a style...}
#      [stylesdir] (~/.fluxbox/styles) 
# [end]
#
# *** IMPORTANT ***
# Change "rootCommand: fbsetbg /path/to/wallpaper" to reflect your desired
# wallpaper. (ex. ~/images/backgrounds/fubar.jpg) Do not touch anything else!
#
#######################
# Begin Configuration #
#######################
*.font:                                 snap
rootCommand:                            fbsetbg /path/to/wallpaper

menu.borderColor:                       #FFFFFF
menu.borderWidth:                       1
menu.bullet:                            triangle
menu.bullet.position:                   right
menu.frame:                             flat gradient horizontal
menu.frame.color:                       #000000
menu.frame.colorTo:                     #7A7A7A
menu.frame.disableColor:                #00EE00
menu.frame.textColor:                   #FFFFFF
menu.frame.justify:                     left
menu.height:                            25
menu.hilite.color:                      #FFFFFF
menu.hilite.textColor:                  #000000
menu.title.color:                       #000000
menu.title.textColor:                   #FFFFFF
menu.title.justify:                     center

toolbar.borderColor:                    #FFFFFF
toolbar.borderWidth:                    1
toolbar.button.color:                   #000000
toolbar.button.picColor:                #FFFFFF
toolbar.button.pressed:                 flat solid
toolbar.button.pressed.color:           #7A7A7A
toolbar.clock.color:                    #000000
toolbar.clock.textColor:                #FFFFFF
toolbar.height:                         15
toolbar.iconbar.empty:                  flat gradient rectangle
toolbar.iconbar.empty.color:            #000000
toolbar.iconbar.empty.colorTo:          #FFFFFF
toolbar.iconbar.focused:                flat gradient rectangle
toolbar.iconbar.focused.borderWidth:  0
toolbar.iconbar.focused.color:          #000000
toolbar.iconbar.focused.colorTo:        #FFFFFF
toolbar.iconbar.focused.textColor:      #000000
toolbar.iconbar.unfocused:              flat solid
toolbar.iconbar.unfocused.borderWidth:  0
toolbar.iconbar.unfocused.color:        #000000
toolbar.iconbar.unfocused.textColor:    #7A7A7A
toolbar.justify:                        center
toolbar.label.color:                    #000000
toolbar.label.textColor:                #FFFFFF
toolbar.systray:                        flat solid
toolbar.systray.color:                  #000000
toolbar.workspace.color:                #000000
toolbar.workspace.textColor:            #FFFFFF

window.borderColor:                     #FFFFFF
window.borderWidth:                     1
window.button.focus.color:              #000000
window.button.focus.picColor:           #FFFFFF
window.button.pressed:                  raised gradient pyramid
window.button.pressed.color:            #000000
window.button.pressed.colorTo:          #FFFFFF
window.button.unfocus.color:            #000000
window.button.unfocus.picColor:         #FFFFFF
window.grip.focus.color:                #FFFFFF
window.grip.unfocus.color:              #000000
window.handle.focus.color:              #000000
window.handle.unfocus.color:            #FFFFFF
window.handleWidth:                     2
window.justify:                         center
window.label.focus:                     raised gradient pyramid
window.label.focus.color:               #000000
window.label.focus.colorTo:             #FFFFFF
window.label.focus.textColor:           #000000
window.label.unfocus:                   flat solid
window.label.unfocus.color:             #000000
window.label.unfocus.textColor:         #7A7A7A
window.title.focus.color:               #000000
window.title.height:                    15
window.title.unfocus.colorTo:           #FFFFFF

slit:                                   flat gradient rectangle
slit.bevelWidth:                        0
slit.borderColor:                       #FFFFFF
slit.borderWidth:                       1
slit.color:                             #000000
slit.colorTo:                           #FFFFFF
```
*Note: The icon backgrounds for Qt apps in the systray are now black instead of grey.

---

### Post by Narada on 2009-08-10
[IMG]http://imgur.com/eY4bc.jpg[/IMG]
Screenshot: [[IMG]http://img20.imageshack.us/img20/6581/fluxthemehaktos.th.jpg[/IMG]](http://img20.imageshack.us/my.php?image=fluxthemehaktos.jpg)
```
# Style: HaKT Flux
# Author: Malik
# Date: 08.2009 
############################################################################
# Note: This theme is intended for use with Artwiz fonts.
# Get them here: http://sourceforge.net/project/showfiles.php?group_id=95348
############################################################################
*.font:                                 snap
rootCommand:                            fbsetbg /path/to/wallpaper
borderColor:			        black
bevelWidth:			        1
borderWidth:			        1
handleWidth:			        5

menu.borderColor:                       #000000
menu.borderWidth:                       2
menu.bullet:                            triangle
menu.bullet.position:                   right
menu.frame:                             flat
menu.frame.color:                       #660000
menu.frame.textColor:                   #FFFFFF
menu.frame.disableColor:                #1464F4
menu.frame.justify:                     left
menu.height:                            25
menu.hilite.color:                      #808080
menu.hilite.textColor:                  #FFFFFF
menu.roundCorners:                      TopRight TopLeft
menu.title.color:                       #000000
menu.title.colorTo:                     #000000
menu.title.justify:                     center
menu.title.textColor:                   #FFFFFF

toolbar.color:                          #660000
toolbar.*.bevelWidth:                   2
toolbar.borderWidth:                    2
toolbar.borderColor:                    #000000
toolbar.button.borderColor:             #000000
toolbar.button.borderWidth:             0
toolbar.button.color:                   #000000
toolbar.button.picColor:                #FFFFFF
toolbar.button.pressed:                 flat solid
toolbar.button.pressed.color:           #808080
toolbar.clock.borderWidth:              1
toolbar.clock.borderColor:              #000000
toolbar.clock.color:                    #FFFFFF
toolbar.clock.textColor:                #000000
toolbar.height:                         16
toolbar.iconbar.borderColor:            #000000
toolbar.iconbar.borderWidth:            1
toolbar.iconbar.empty:                  raised interlaced
toolbar.iconbar.empty.color:            #000000	
toolbar.iconbar.empty.colorTo:          #333333	
toolbar.iconbar.focused:                raised interlaced 
toolbar.iconbar.focused.color:          #000000	
toolbar.iconbar.focused.colorTo:        #333333
toolbar.iconbar.focused.textColor:      #FFFFFF
toolbar.iconbar.unfocused:              raised interlaced
toolbar.iconbar.unfocused.color:        #000000
toolbar.iconbar.unfocused.colorTo:      #333333
toolbar.iconbar.unfocused.textColor:    #808080
toolbar.justify:                        center
toolbar.systray:                        flat solid
toolbar.systray.color:                  #660000
toolbar.workspace.borderWidth:          1
toolbar.workspace.borderColor:          #000000
toolbar.workspace.color:                #FFFFFF
toolbar.workspace.textColor:            #000000
toolbar.label.color:                    #FFFFFF
toolbar.label.textColor:                #000000

window.*.bevelWidth:                    2
window.title.color:                     #660000
window.borderWidth:                     2
window.borderColor:                     #000000
window.button.focus.color:              #FFFFFF
window.button.focus.picColor:           #000000
window.button.unfocus.color:            #000000
window.button.unfocus.picColor:         #FFFFFF
window.button.pressed.color:            #808080
window.grip.focus.color:                #FFFFFF
window.grip.unfocus.color:              #000000
window.handleWidth:                     2
window.handle.focus:                    flat solid
window.handle.focus.color:              #660000
window.handle.unfocus.color:            #660000
window.justify:                         center
window.label.focus:                     raised interlaced
window.label.focus.color:               #000000
window.label.focus.colorTo:             #333333
window.label.focus.textColor:           #FFFFFF
window.label.unfocus:                   raised interlaced
window.label.unfocus.color:             #000000
window.label.unfocus.colorTo:           #333333
window.label.unfocus.textColor:         #808080
window.title.height:                    16
window.title.focus.color:               #660000
window.title.unfocus.color:             #660000

slit:                                   flat solid
slit.bevelWidth:                        2
slit.borderWidth:                       1
slit.borderColor:                       #000000
slit.color:                             #660000
```

---

### Post by hessiess on 2009-08-10
Don't spam, you should have posted all your themes in one thread.

---

### Post by Narada on 2009-08-10
> **hessiess said:**
> Don't spam, you should have posted all your themes in one thread.

Sorry about that. I assumed that because they were separate individual configs it would be Ok but I also see where you're coming from. Could a mod maybe merge all of these and change the title to something more applicable? >_<

---

