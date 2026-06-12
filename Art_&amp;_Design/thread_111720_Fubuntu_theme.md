---
title: "Fubuntu theme"
date: 2006-01-02
forum: Art &amp; Design
---

### Post by DoorGunner on 2006-01-02
Hi 

I made up a bit of a theme for ubuntu in flux box. Have a look and see what you think?

[IMG]http://www.members.shaw.ca/DoorGunner/Images/FluxU.jpeg[/IMG]

I based it on the Meta theme provided by Fluxbox and adjusted some colors to match up with the warty-final-Ubuntu.png .  As well this screen shot was set up so that I have a menu transparency of 60. 

This is what you can do toinstall it if you like it.

> 
in root#
# cp /usr/share/fluxbox/styles/Meta /usr/share/fluxbox/styles/new
# gedit /usr/share/fluxbox/styles/new


Delete all the script in the new file

Insert the following script

> 
! New
! (c) joel carlbark 2003
! Modified by DoorGunner 2005
! please dont turn on aa with this style
! make sure you have the font 'glisp' (or similar).

toolbar:                             flat gradient vertical
toolbar.color:                       #4D2B1A
toolbar.colorTo:                     #341F13 

toolbar.button:                      parentrelative
toolbar.button.picColor:             #E78852

toolbar.button.pressed:              sunken solid
toolbar.button.pressed.color:        #526d8c
toolbar.button.pressed.picColor:     #000000

! clock
toolbar.clock:                       parentrelative
toolbar.clock.textColor:             #E78852

! shows workspace nr
toolbar.label:                       parentrelative
toolbar.label.textColor:             #E78852

! current active window / toolbar
toolbar.windowLabel:                 parentrelative
toolbar.windowLabel.textColor:       #E78852

! menu ---------
menu.title:                          flat gradient vertical
menu.title.color:                    #8A5332
menu.title.colorTo:                  #341F13
menu.title.textColor:                #E78852

menu.frame:                          flat gradient vertical
menu.frame.color:                    #8A5332
menu.frame.colorTo:                  #79492D
menu.frame.textColor:                #E78852

menu.hilite:                         flat solid
menu.hilite.color:                   #C18751
menu.hilite.textColor:               white

menu.bullet:                         triangle
menu.bullet.position:                right

! window --------------
window.title.focus:                  flat gradient vertical
window.title.focus.color:            #8A5332
window.title.focus.colorTo:          #341F13

window.label.focus:                  parentrelative
window.label.focus.textColor:        #E78852

window.button.focus:                 flat gradient vertical
window.button.focus.color:           #8A5332
window.button.focus.colorTo:         #341F13
window.button.focus.picColor:        #E78852

window.button.pressed:               sunken solid
window.button.pressed.color:         #405060
window.button.pressed.picColor:      #000000

window.handle.focus:                 flat gradient vertical
window.handle.focus.color:           #8A5332
window.handle.focus.colorTo:         #341F13

window.grip.focus:                   flat gradient vertical
window.grip.focus.color:             #8A5332
window.grip.focus.colorTo:           #341F13

window.frame.focus:                  flat solid
window.frame.focus.color:            white

! unfocused
window.title.unfocus:                flat gradient vertical
window.title.unfocus.color:          #8A5332
window.title.unfocus.colorTo:        #341F13

window.label.unfocus:                parentrelative
window.label.unfocus.textColor:      #949694

window.handle.unfocus:               flat gradient vertical
window.handle.unfocus.color:         #8A5332
window.handle.unfocus.colorTo:       #341F13

window.grip.unfocus:                 flat gradient vertical
window.grip.unfocus.color:           #4D2B1A
window.grip.unfocus.colorTo:         #341F13

window.frame.unfocus:                flat solid
window.frame.unfocus.color:          white

window.button.unfocus:               flat gradient vertical
window.button.unfocus.color:         #8A5332
window.button.unfocus.colorTo:       #341F13
window.button.unfocus.picColor:      #E78852

! tabs ------
window.tab.justify:                  left

window.tab.label.focus:              flat gradient vertical
window.tab.label.focus.color:        #849ec6
window.tab.label.focus.colorTo:      #526d8c
window.tab.label.focus.textColor:    #d6d7e7

window.tab.label.unfocus:            flat gradient vertical
window.tab.label.unfocus.color:      #8A5332
window.tab.label.unfocus.colorTo:    #341F13
window.tab.label.unfocus.textColor:  #E78852

window.tab.borderWidth:              1
window.tab.borderColor:              #E78852
! -------

toolbar.justify:                     left
window.justify:                      center
menu.title.justify:                  center
menu.frame.justify:                  left

borderColor:                         #000000
borderWidth:                         1
bevelWidth:                          1
frameWidth:                          1
handleWidth:                         4

rootCommand:                         fbsetbg -f /usr/share/backgrounds/warty-final-ubuntu.png
*font:                               glisp


Save and close

all you need to do is go to menu styles and select it.

Hope you enjoy it

---

### Post by Snakey on 2006-01-03
IMHO it's too dark (for me at least :p), but it doesn't mean I think it's ugly it fits well with the wallpaper, maybe it could be more nice if the minimize, maximize, close buttons are retouched a bit?

---

### Post by drfalkor on 2006-01-03
nice, but the top window border is just to big .

---

### Post by DoorGunner on 2006-01-03
Thank you for the feed back.

It is quite dark isnt it... it was a hard set of colors to work with.

may be i will try and rework it a bit with lighter colours near the ubuntu in the wallpaper.

---

