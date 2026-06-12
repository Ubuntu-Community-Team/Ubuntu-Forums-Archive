---
title: "[SOLVED] How to remove icon from metacity title-bar"
date: 2008-06-12
forum: Art &amp; Design
---

### Post by NEUR0M4NCER on 2008-06-12
So i'm using Darklooks GTK and Unity Metacity - how can I take out the app' icon from the title-bar? I've had a look through the files, and can't see anything glaringly obvious, but then i've no idea what i'm looking for really...


Regards

---

### Post by Aphorism on 2008-06-13
How can I not reply to someone who names themselves after a terrific novel _and_ has the original video game artwork as an avatar?

Welcome to the arcane world of Metacity theming.

I'll try not to bore you with the details.

First, every different type of window has a descriptor in the theme file.  The theme file is located under the metacity directory -- version one or two depending on how sophisticated your source theme is.

Generally you will find a stanza that looks like:

```

<frame_style name="normal" geometry="normal">
  <piece position="entire_background" draw_ops="round_bevel_unfocused"/>
  <piece position="title" draw_ops="title_unfocused"/>
  <button function="close" state="normal" draw_ops="close_button_unfocused"/>
  <button function="close" state="pressed" draw_ops="close_button_unfocused_pressed"/>
  <button function="close" state="prelight" draw_ops="close_button_unfocused_prelight"/>
  <button function="maximize" state="normal" draw_ops="maximize_button_unfocused"/>
  <button function="maximize" state="pressed" draw_ops="maximize_button_unfocused_pressed"/>
  <button function="maximize" state="prelight" draw_ops="maximize_button_unfocused_prelight"/>
  <button function="minimize" state="normal" draw_ops="minimize_button_unfocused"/>
  <button function="minimize" state="pressed" draw_ops="minimize_button_unfocused_pressed"/>
  <button function="minimize" state="prelight" draw_ops="minimize_button_unfocused_prelight"/>
  <button function="menu" state="normal" draw_ops="menu_button_normal"/>
  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
</frame_style>

```

Each one of the <button function=[...]> defines how the overall window border will appear.  To get rid of your menus, simply remove the respective clause in the stanza.  

I hope this helps...
TJS

---

### Post by junior aspirin on 2008-06-14
an easier way if you are using plain Metacity and not Compiz.

1. press "Alt + F2"
2. enter "gconf-editor"
3.navigate to />apps>metacity>general
4. double click on button layout, and delete the "menu" part before the colon.

Gone!

---

### Post by NEUR0M4NCER on 2008-06-14
Both of these replies are very helpful - thank-you! I'll use the second one for now, and have a good look through the Metacity config, see what I can break in there.


Thanks!

---

