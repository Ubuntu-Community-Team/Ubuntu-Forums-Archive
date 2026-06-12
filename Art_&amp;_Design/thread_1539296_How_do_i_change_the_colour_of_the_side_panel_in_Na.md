---
title: "How do i change the colour of the side panel in Nautilus?"
date: 2010-07-26
forum: Art &amp; Design
---

### Post by Macfunky on 2010-07-26
I love changing themes on my box but i haven't found one that i like so far, just components, so i decided to compile a theme comprising of every element that i like. So far all i have done is to rename icons and add them to the themes folder with which i have started with. I am just changing icons from another theme to get my own.

One thing i really want to be able to do if it's not hard or confusing is to be able to change the colour of the side panel in Nautilus, just like in the Mac4Lin project. I have downloaded the Mac4Lin theme and searched through the folder to see if i could find where the colour was is assigned but i can't find it. Could anyone let me know how i can do this? I am assuming i assign the colour in the gtkrc file?

---

### Post by LarsKongo on 2010-07-27
```
style "nautilus-sidebar" {
	font_name                                 = "Regular"

	GtkTreeView::odd_row_color                = "#e2e2e2" # Change color here
	GtkTreeView::even_row_color               = "#e2e2e2" # Change color here
}

style "nautilus-sidebar-title"
{
	fg[NORMAL]      = @fg_color # Change text color here
	fg[PRELIGHT]    = @fg_color # Change text color here
	fg[ACTIVE]      = @fg_color # Change text color here

	bg[NORMAL]      = "#e2e2e2" # Change color here
	bg[PRELIGHT]    = "#e2e2e2" # Change color here
	bg[ACTIVE]      = "#e2e2e2" # Change color here
}

widget_class "*NautilusSidePane.*"                 style "nautilus-sidebar"
widget_class "*Nautilus*Places*Sidebar*"           style "nautilus-sidebar"
widget_class "*Nautilus*Side*.GtkWidget"           style "nautilus-sidebar"
widget_class "*Nautilus*Side*Title*"               style "nautilus-sidebar-title"	

```

Just paste it at the bottom in your gtkrc file.

---

### Post by pt123 on 2010-07-27
a shame that you can't drag and drop like the main panel

---

### Post by Zookalicious on 2010-11-18
Thank you very much LarsKongo! That helped a lot. Although since it took me a bit of research and this is the first hit on google when searching how to change side panel colours, for what it's worth the gtkrc file is located at

/usr/share/themes/"YOURCURRENTTHEME"/gtk-2.0/gtkrc

Also to edit the text colour add    
```


    text[NORMAL]      =  "#YOURCOLOUR"
    text[PRELIGHT]    = "#YOURCOLOUR"
    text[SELECTED]    =  "#YOURCOLOUR"
    text[INSENSITIVE] = "#YOURCOLOUR"
    text[ACTIVE]      =  "#YOURCOLOUR"


```under:

style "nautilus-sidebar" {



and before the closing bracket....

```

style "nautilus-sidebar" {
    font_name                                 = "Regular"

    GtkTreeView::odd_row_color                = "#39152E" # Change color here
    GtkTreeView::even_row_color               = "#39152E" # Change color here

    text[NORMAL]      =  "#YOURCOLOUR"
    text[PRELIGHT]    = "#YOURCOLOUR"
    text[SELECTED]    =  "#YOURCOLOUR"
    text[INSENSITIVE] = "#YOURCOLOUR"
    text[ACTIVE]      =  "#YOURCOLOUR"

}

```Like that.

---

