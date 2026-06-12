---
title: "note to metacity theme designers"
date: 2005-10-11
forum: Art &amp; Design
---

### Post by benplaut on 2005-10-11
I've noticed that tons of themes out there, almost all, in fact, have a one or two pixel border surrounding each window. Read up about Fitt's Law - pretty much, objects on the edge of the screen are easier to click that in the middle. 

same goes for GTK themes, i guess!

:)

---

### Post by bvc on 2005-10-12
Not sure what you are saying but if it's what I think (I know what Fitt's Law is...though it is not law) I agree. IMO, anything below 3 is unusable. May look good but is a pain for anyone to use and I wish people would stop it! I have themes that appear to be 1 or 2 px but are actually 4+. Looks bad in a trans terminal but at least they are usable.

---

### Post by Wolki on 2005-10-12
[QUOTE=benplaut]I've noticed that tons of themes out there, almost all, in fact, have a one or two pixel border surrounding each window. Read up about Fitt's Law - pretty much, objects on the edge of the screen are easier to click that in the middle. 
same goes for GTK themes, i guess!
[/QUOTE]

Well, the corners are already covered by the panels, same for the top and bottom screen edges (which, no matter the theme, are active - try it). And since that part of Fitt's Law only applies to the very edges, window borders don't change anything.

(OK OK, they could follow Fitt's Law by making things like window decorations bigger, but that is by far not as effective as the steps already taken. A few pixels <<< infinity ^^;; )

---

### Post by Hatchetfish on 2005-10-14
Something I have to bring up in a discussion like this is that there's no reason for a border around maximized windows, and a very good reason for there not to be one.  

First of all, it's not useful to resize a maximized window, the whole point of them is that they fit to the entire screen. (yeah, minus panels and such, but you know what i mean)  The real issue though is that it breaks the function of applications that count on having no border to provide a fitt's law compliant button for something internal to the app. The only example I have on hand is the Opera browser.  Opera uses (along with a standard toolbar button and menu item) a ~4px wide strip along the left or right edge, the full height the window, to toggle the bookmarks panel.    

Borders around normal windows, unmaximized ones that is, are great, the opera bookmarks toggle strip isn't useful there anyway, since it's not on the edge of the screen.  Even a single pixel border when maximized makes it useless, the whole point is being able to flick the cursor over against the edge, not flick it over to the edge then carefully back up ever so slightly.

I currently can't think of any other examples than opera that use something like this, but I really wish i could.  Practically anything with a side panel suits itself to this, but most just use an x in the title of the panel (Firefox, most PDF viewers with a side panel), or a toggle that moves like a drawer handle, like the old mozilla panel grabber. 

 Anyway, long pseudo-rant post, but this happened to hit a nerve, to the extent of drawing a lurker since the days of warty into registering in order to comment.

---

### Post by benplaut on 2005-10-14
the main thing i'm refferning to is scroll bars - they are still useful, despite the proliferation of scroll mice

wolki: i've notices that they often are in KDE, but not in gnome... i use them well:

Menu - Xkill
  |
Show Desktop - Pager (for use with mouse scroll, of course)

---

### Post by Wolki on 2005-10-14
> **Hatchetfish]Something I have to bring up in a discussion like this is that there's no reason for a border around maximized windows, and a very good reason for there not to be one.[/quote]

I rearely have maximized windows, but I just tried this out and maximized windows don't have borders on a standard breezy install... nice feature, imho. 

>  Anyway, long pseudo-rant post, but this happened to hit a nerve, to the extent of drawing a lurker since the days of warty into registering in order to comment.

Interesting to read though. Nice post, especially since i have little experience with Opera (didn't really use it since version ~6 ^^ said:**
> 
the main thing i'm refferning to is scroll bars - they are still useful, despite the proliferation of scroll mice

Right, but on maximized windows they are fitts-aware (try it) and with windows that are not maximized it does not matter.

> wolki: i've notices that they often are in KDE, but not in gnome...

Not sure I understand what you mean. *confused*

---

### Post by Hatchetfish on 2005-10-15
[QUOTE=Wolki]...maximized windows don't have borders on a standard breezy install...[/QUOTE]

Excellent feature, and like I said it seems to depend entirely on the metacity theme.   Part of the reason I brought this up was that it wasn't the case in warty, so I had to go hunt down and test a bunch of metacity themes until I found one that worked (not that hard) and that I could stand (much harder...).  Part of the reason I prefer gnome is that finding a kde theme that works like this is next to impossible, and last I checked the default didn't.  

Anyway, now it's been clarified to scroll bars I guess I'm a bit off topic, but all it does is lend weight to the argument I suppose.  Just another reason not to throw away the possibility of fitts law optimization on a big lumpy border that doesn't do anything.

Now I think of it, the scroll bar thing probably never ocurred to me since I A) do indeed use a scroll mouse, and B) have to screen themes based on the opera panel toggle anyway.

---

### Post by cowlip on 2005-10-15
[QUOTE=benplaut]I've noticed that tons of themes out there, almost all, in fact, have a one or two pixel border surrounding each window. Read up about Fitt's Law - pretty much, objects on the edge of the screen are easier to click that in the middle. 

same goes for GTK themes, i guess!

:)[/QUOTE]
I know....Please someone fix Clearlooks already!  There's even an ancient bug in gnome's bugzilla for this.

Ideally metacity would do this automatically though

EDIT:  personally, I'm talking more about how the "x" on the upper right can't be closed by throwing your mouse there; those pixels block the edge.  I see the two panels as space wasting :)

---

### Post by bvc on 2005-10-16
left and right_width should be at 0 for fitts law scrollbars
left and right_titlebar_edge should be at 0 for fitts law buttons

concerning clearlooks mcity change this```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="1"/>
  <distance name="right_titlebar_edge" value="1"/>
</frame_geometry>
```
to this
```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
</frame_geometry>
```

another example is clearbox-out
change this```
<frame_geometry name="no_borders" parent="normal">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="2"/>
  <distance name="right_titlebar_edge" value="2"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="0" right="0" top="3" bottom="3"/>
</frame_geometry>
```
to this```
<frame_geometry name="no_borders" parent="normal">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="0" right="0" top="3" bottom="3"/>
</frame_geometry>
```

---

### Post by Samy_Merchi on 2005-10-16
Scrollbars indeed seem to be Fitt's-aware, but the close button in almost any case is not. You end up always flicking your mouse to the corner, then carefully backing away for a few pixels, instead of just going to the corner. Very very annoying!

---

### Post by bvc on 2005-10-16
[QUOTE=Samy_Merchi]Scrollbars indeed seem to be Fitt's-aware, but the close button in almost any case is not. You end up always flicking your mouse to the corner, then carefully backing away for a few pixels, instead of just going to the corner. Very very annoying![/QUOTE]The code above shows fitts aware buttons horizonally. To get them right vertically is possible but very ugly.
change this```
<frame_geometry name="no_borders" parent="normal">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="2"/>
  <distance name="right_titlebar_edge" value="2"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="0" right="0" top="3" bottom="3"/>
</frame_geometry>
```
to this
```
<frame_geometry name="no_borders" parent="normal">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="2"/>
  <distance name="right_titlebar_edge" value="2"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="0" right="0" top="0" bottom="6"/>
</frame_geometry>
```

it is the "button_border" top="3" that is keeping it from being fitts aware in the extreme top 'corner' (above the button). If you change bottom to 0 the button fills the entire titlebar. Again, it works but is extremely ugly. The Windows Desktop is in its very nature ugly, and therefore intented to be 'useable'. Linux supposedly strives to be both usable and appealing to the eye. Bottom line is that it's very hard to achieve both, but there really is no excuse for not at least having the above code, in my previous post, so that the buttons are at least half fitts aware. That is, so that you can at least slap your mouse to the side of the button and be able to close the window without having to come back over the button.

---

### Post by cowlip on 2005-10-16
Hey that worked...thank you!

I'm using brace 2 in metacity

---

### Post by bvc on 2005-10-16
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/fitts_buttons.png[/IMG]
1. you can see that the clearlooks theme would look really silly
2. clearbox would be moderately funny
3. clearbox is now ugly and doesn't look at all like the theme everywhere else.

---

