---
title: "Fixing window icon in dust sand metacity theme..."
date: 2008-11-18
forum: Art &amp; Design
---

### Post by zombiepig on 2008-11-18
I'm trying to fix the dust sand theme to properly show the window icon. Currently, the theme cuts off the right most part of the icon (see first attachment).


I can fix this if I change the metacity-theme-1.xml file, and alter the line:

    <distance name="button_width" value="20"/>

to 

    <distance name="button_width" value="28"/>

This fixes the window icon, but means the spacing for the close/max/restore buttons is wrong (see second attachment).

But if I try and get more precise, and change the lines:

<draw_ops name="button_menu_normal">
<icon x="6" y="2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

to 

<draw_ops name="button_menu_normal">
<icon x="6" y="2" width="28" height="mini_icon_height"/>
</draw_ops>

Then the window icon disappears altogether! 

Any idea what I'm doing wrong here?

---

### Post by smartboyathome on 2008-11-19
I think that making the button width only apply to the window icon, duplicating the code and creating another set of code for the window buttons, would do it.

---

### Post by zombiepig on 2008-11-19
Thanks for the reply! Unfortunately I'm not really sure what you mean :P

Is there any good beginner guides to the metacity theme format?

---

### Post by smartboyathome on 2008-11-19
Check the link in my sig, it may help you.

What I mean though is to make this:

```
<distance name="button_width" value="28"/>
```

To this:

```
<distance name="button_width" value="20"/>

<distance name="icon_width" value="28"/>
```

And then fidn the entry for button_width under the window icon's portion of the theme (just do a control + F for button_width), and then replace it with icon_width.

---

### Post by zombiepig on 2008-11-19
Ok, your way makes sense to me. But, in this metacity theme, the window icon doesn't use button_width, it's got:

```
<draw_ops name="button_menu_normal">
<icon x="6" y="2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

```

Nowhere in the file is mini_icon_width defined, and changing it to anything else makes the icon disappear :???:

I'll checkout your links and try and learn a bit more.

---

### Post by days_of_ruin on 2008-11-19
> **smartboyathome said:**
> Check the link in my sig, it may help you.

What I mean though is to make this:

```
<distance name="button_width" value="28"/>
```

To this:

```
<distance name="button_width" value="20"/>

<distance name="icon_width" value="28"/>
```

And then fidn the entry for button_width under the window icon's portion of the theme (just do a control + F for button_width), and then replace it with icon_width.

Do you mean in a frame geometry? Because that raises errors.

---

