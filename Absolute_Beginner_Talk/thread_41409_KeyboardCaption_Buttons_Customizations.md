---
title: "Keyboard/Caption Buttons Customizations"
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by ckvs on 2005-06-13
hi all,
i am slowly (exploring live CD, comparing distributions etc.) getting ready to "make the switch"...and more and more it looks like Ubuntu it's going to be.

however, for practical reasons (40+ yrs. of keyboard habits, work in several languages, eyes getting a bit weak etc.) i simply MUST have
a) a "personal", remapped keyboard (not just simply a "switchable between layouts" kbd!),
b) increased size of the caption buttons (maximize, minimize etc.) of windows.

which puts me a bit in a Catch22 situation, coz these things require capacities (installing special programs, customizing things etc.) which would/should/will (i hope) come WITH use...ie they're presently things i don't know how to do YET. (after all, as experienced users may sometimes forget, in the very beginning one "expects" to launch and go and has not the slightest idea of what's waiting!!)
which, in turn, makes me hesitate and delay leaving the "other"O/S behind...

so:
while i have researched the keyboard remapping issue (and found some seemingly relevant progs, eg on freshmeat), i quite honestly have no idea how i would actually proceed to get this done!!! (and as i said above, it would have to be done *within the first session of the new O/S*, coz otherwise i'd be finding myself entirely lost at my box and would probably give up all too early!...coz it is NOT easy to suddenly, after many years of hands-on experience, find oneself not even able to, say, install things, to suddenly go back to "console interaction" again etc.!).
i've found nothing whatsoever which seems to apply to the caption button size customization. 

any ideas, suggestions, pieces of advice?? maybe some pointers *of the most elementary, pedestrian nature* (step by step!!)??

much obliged for any assistance!!
cpak

---

### Post by Alexander Kirillov on 2005-06-13
[QUOTE=ckvs]hi all,
i am slowly (exploring live CD, comparing distributions etc.) getting ready to "make the switch"...and more and more it looks like Ubuntu it's going to be.

however, for practical reasons (40+ yrs. of keyboard habits, work in several languages, eyes getting a bit weak etc.) i simply MUST have
a) a "personal", remapped keyboard (not just simply a "switchable between layouts" kbd!),
b) increased size of the caption buttons (maximize, minimize etc.) of windows.

which puts me a bit in a Catch22 situation, coz these things require capacities (installing special programs, customizing things etc.) which would/should/will (i hope) come WITH use...ie they're presently things i don't know how to do YET. (after all, as experienced users may sometimes forget, in the very beginning one "expects" to launch and go and has not the slightest idea of what's waiting!!)
which, in turn, makes me hesitate and delay leaving the "other"O/S behind...

so:
while i have researched the keyboard remapping issue (and found some seemingly relevant progs, eg on freshmeat), i quite honestly have no idea how i would actually proceed to get this done!!! (and as i said above, it would have to be done *within the first session of the new O/S*, coz otherwise i'd be finding myself entirely lost at my box and would probably give up all too early!...coz it is NOT easy to suddenly, after many years of hands-on experience, find oneself not even able to, say, install things, to suddenly go back to "console interaction" again etc.!).
i've found nothing whatsoever which seems to apply to the caption button size customization. 

any ideas, suggestions, pieces of advice?? maybe some pointers *of the most elementary, pedestrian nature* (step by step!!)??

much obliged for any assistance!!
cpak[/QUOTE]
 For question b): window decoration (border, buttons, etc) is defined by "graphical theme" - to be precise, metacity theme (I assume you intend to use GNOME, which is default desktop in Ubuntu). It is possible to modify existing one, but it would probalby be easier to select a theme with large buttons in  System-Preferences-Themes-Theme Detail-Window border. There is a number of themes installed by default; if none of them looks good to you, you can find more themes at  [http://art.gnome.org/themes/metacity/](http://art.gnome.org/themes/metacity/)

As for question a): the only practical way I know of creating custom keyboard layout is by manually editing the corresponding files, as described [here](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html). This is not very easy, but doable.  Have you found a GUI program to do the same? 

I could try to help with a step-by-step guidance - but I need to know more. E.g., you probably want to have your custom layout to be a modification of a standrard one - which one? What exactly you want to change?

---

### Post by ckvs on 2005-06-13
hi alexander k., and thanks for your reply.
a) the keyboard issue:
- which kbd do i use?? well, the problem starts with that, really, because while choosing the LAYOUT (us/international with deadkeys) seems straightforward, i'm not at all sure that the default (hardware discovered) choice of kbd is correct (i have an ibm thinkpad r31, with keys which show up on NONE of the configurations offered in the dropdown list). that there IS a problem is beyond doubt, because when i do set things up (using the live cd) in this manner, certain quite "normal" keys do simply nothing (eg the left ctrl key), and many of the others, more "thinkpad r31" keys (page switcher, right ctrl, etc) are entirely dead. (the "really" thinkpad specific ones, such as the "sound"keys, well, that's a special configuration issue, for which i've found references for thinkpad config programs...but all that is for much later!)

- have i found a GUI for simple key remapping? well, i've come across for instance
[http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)
but it doesn't look too promising.
[http://gnufoo.org/ucontrol/](http://gnufoo.org/ucontrol/)  might do it, partially.
in any case, the article you mention (which i had also read), is probably the ticket, but, as you say, it's an editing job, "doable but not very easy".
therefore my hesitation!!

-what i need to start, in addition to the IBM/Thinkpad basic keyboard+us international wt deadkeys working, would be:
`/~key remapped to right Shift (ie `/~ when one hits right Shift)
Tab remapped to (former) `/~
PageUp remapped to (former) Tab
PageDown remapped to (former) Capslock
(which adds up to: no functional Capslock...which, on Windoze, i have arranged via a hotkey WindowsKey+<=start capslock.exe/WindowsKey+>=stop capslock.exe....but this can probably wait until i figure out how to construct hotkeys, and find myself a capslock starter/stopper [which, until now, i haven't been able to, for Ubuntu/Debian])

b) the caption button issue:
yes, i agree with you, this seems to be theme/border problem, but in my explorations with Ubuntu Live CD i've found that i can do all kinds of things, eg making the border larger (which is NOT what i want), but NOT the following: 
-make the title bar wider (which would make the buttons bigger by a few pixels), and
-make the caption boxes twice wider, and
-especially (if such a thing were possible) to make these WIDER buttons apply to *open pages within windows* (eg docs within a word processor).

but i shall now go and fire up the U Live CD and explore the indications/websites you give in your post and see whether that'll do it!!

as for your gracious offer to help, i can't tell you have grateful i am!!
i'll try to take as little of your time as possible, yet, on the other hand, i figure that if we can do this exercise publicly together here in the forum, other people in my situation might find it useful.

so this for now and all my thanks.
ckvs

---

### Post by ckvs on 2005-06-13
also, maybe bits and pieces re kbd here:
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)
[http://devaux.fabien.free.fr/flux/](http://devaux.fabien.free.fr/flux/)
[http://lineak.sourceforge.net/index.php?nav=showdoc&docid=LinEAK_support_HOWTO&doctitle=Keyboard%20support%20HOWTO](http://lineak.sourceforge.net/index.php?nav=showdoc&docid=LinEAK_support_HOWTO&doctitle=Keyboard%20support%20HOWTO)

later,
thanks,ckvs

---

### Post by Alexander Kirillov on 2005-06-13
[QUOTE=ckvs]hi alexander k., and thanks for your reply.
a) the keyboard issue:
- which kbd do i use?? well, the problem starts with that, really, because while choosing the LAYOUT (us/international with deadkeys) seems straightforward, i'm not at all sure that the default (hardware discovered) choice of kbd is correct (i have an ibm thinkpad r31, with keys which show up on NONE of the configurations offered in the dropdown list). that there IS a problem is beyond doubt, because when i do set things up (using the live cd) in this manner, certain quite "normal" keys do simply nothing (eg the left ctrl key), and many of the others, more "thinkpad r31" keys (page switcher, right ctrl, etc) are entirely dead. (the "really" thinkpad specific ones, such as the "sound"keys, well, that's a special configuration issue, for which i've found references for thinkpad config programs...but all that is for much later!)

- have i found a GUI for simple key remapping? well, i've come across for instance
[http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)
but it doesn't look too promising.
[http://gnufoo.org/ucontrol/](http://gnufoo.org/ucontrol/)  might do it, partially.
in any case, the article you mention (which i had also read), is probably the ticket, but, as you say, it's an editing job, "doable but not very easy".
therefore my hesitation!!

-what i need to start, in addition to the IBM/Thinkpad basic keyboard+us international wt deadkeys working, would be:
`/~key remapped to right Shift (ie `/~ when one hits right Shift)
Tab remapped to (former) `/~
PageUp remapped to (former) Tab
PageDown remapped to (former) Capslock
(which adds up to: no functional Capslock...which, on Windoze, i have arranged via a hotkey WindowsKey+<=start capslock.exe/WindowsKey+>=stop capslock.exe....but this can probably wait until i figure out how to construct hotkeys, and find myself a capslock starter/stopper [which, until now, i haven't been able to, for Ubuntu/Debian])

b) the caption button issue:
yes, i agree with you, this seems to be theme/border problem, but in my explorations with Ubuntu Live CD i've found that i can do all kinds of things, eg making the border larger (which is NOT what i want), but NOT the following: 
-make the title bar wider (which would make the buttons bigger by a few pixels), and
-make the caption boxes twice wider, and
-especially (if such a thing were possible) to make these WIDER buttons apply to *open pages within windows* (eg docs within a word processor).

but i shall now go and fire up the U Live CD and explore the indications/websites you give in your post and see whether that'll do it!!

as for your gracious offer to help, i can't tell you have grateful i am!!
i'll try to take as little of your time as possible, yet, on the other hand, i figure that if we can do this exercise publicly together here in the forum, other people in my situation might find it useful.

so this for now and all my thanks.
ckvs[/QUOTE]
 I looked at some of the "graphical" apps for keyboard mapping. My advice: stay away from them. Some of them are old and use older mechanism (xmodmap, now abandoned in favor of xkb); others do not do what you want; one is for MACs only... Manual editing of symbols file seems the most reasonable to me. If I have time later, I'll try to help with this. 

As for buttons: 
 - they are normally not called "caption button" but rather window border buttons. There are some accessibility themes that have these buttons larger than usual - but in all the themes I have seen, the buttons are always square. Anf there is no way you can "stretch" them short of manually editing the theme files, or replacing some images with different ones. This is possible, but I'd suggest starting by installing the accessibility themes package and using one of their large button themes.  
 - Linux apps usually do not have "window within window" model (thanks god!); those apps that need to show several documents either do it in separate windows, or use tabs (as in firefox). These tabs usually only have "close" button, no "minimize" one. ANd these buttons are determined by different component of grpahical theme (so-called "widget theme", or more properly, gtk2 theme). Which means that they may be different from the window border buttons.

---

### Post by ckvs on 2005-06-15
hi again alexander k.,
and my thanks for your kind attention!

a) re border buttons(sorry for the wrong expression): yes, i entirely understand (as a tabbed-Opera person from way back) the interest to NOT have pages-in-windows, and i'm looking forward to get into Ubuntu and not (or only rarely, eg in OpenOffice) to have to deal with it. thanks also for suggestion exploring different themes.
which more or less "settles" this issue.

b) keyboard remapping: while i'm grateful for your advice (eg not to touch certain GUI versions), i'm also a bit "at sea" now, coz -as i'm sure you'll understand- as long as i can't concoct for myself some solution to the *interface*/kbd i'm not going to stress myself out launching into the unknown territory of Ubuntu. i mean: it's daunting enough already to imagine what one may have to customize where...and all via "text editor" input...but to hack around on a keyboard which doesn't even permit me to type as usual, well...
so, i shall continue to explore, see whether somebody has some manageable procedure i could employ (such as the article you mentioned above), and also wait and hope that you (or somebody else) may have the time necessary to show me "the ropes" for remapping a few keys.

with all my thanks,
ckvs

---

