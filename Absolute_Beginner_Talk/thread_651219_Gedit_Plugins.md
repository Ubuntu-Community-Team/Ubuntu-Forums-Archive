---
title: "Gedit Plugins"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-12-27
[FONT="Book Antiqua"][FONT="Arial"]:)

When you have "Tags" enabled in Gedit,  there are certain categories where you can insert, say HTML codes for certain functions.

For instance..., if you pick HTML- Tags category,  you can select font color and it will place the code for font color in your document at the place where the cursor is.

Question.  Does anyone know how to add categories to the Tag List where say,  you could add commonly used phrases to insert in your document?

I know you can click on "View" and select "Insert User Name", but it would be neat if you could have a list of phrases to choose from on the Tag List.

Anyone?









[/FONT]

---

### Post by p_quarles on 2007-12-27
It looks like the tags are defined using compressed XML files located in this directory:
```
/usr/share/gedit-2/taglist
```
You should be able to create a custom list using the same syntax.

---

