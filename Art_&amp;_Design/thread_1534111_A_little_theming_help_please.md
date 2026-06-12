---
title: "A little theming help please?"
date: 2010-07-19
forum: Art &amp; Design
---

### Post by x-shaney-x on 2010-07-19
I am wanting to reduce the vertical padding in the area directly below the main toolbar in gnome apps.

So in nautilus, the bit with the breadcrumb/location things.

Is this a universal setting that can be easily changed in a gtkrc file or is it a different one per app?

I am comfortable changing things in gtkrc theme files and can mostly work out what things do but I have been unable to find out what this particular area is called.

---

### Post by LarsKongo on 2010-07-19
Try this:

```

style "nautilus-toolbar"
{
ythickness = 0
}

widget_class "*Nautilus*Toolbar*" style "nautilus-toolbar"
widget_class "*NautilusPathBar.*ToggleButton" style "nautilus-toolbar"
```

To save more vertical space I would recommend that you install nautilus-elementary instead.

---

### Post by x-shaney-x on 2010-07-20
> **LarsKongo said:**
> Try this:

```

style "nautilus-toolbar"
{
ythickness = 0
}

widget_class "*Nautilus*Toolbar*" style "nautilus-toolbar"
widget_class "*NautilusPathBar.*ToggleButton" style "nautilus-toolbar"
```To save more vertical space I would recommend that you install nautilus-elementary instead.

Unfortunately, that didn't do it but thanks anyway.
Regarding Nautilus Elementary, it's nice but there are certain things I just don't like about it.

But in any case, I was talking about the area below the toolbar in ALL gnome apps.
I was hoping it was a common variable.

For example, the are below the main toolbar in evolution has no padding around the combobox thing, I was hoping to make them all like that but I'm guessing it is a per app sort of thing and that area is defined differently in each.

---

