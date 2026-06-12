---
title: "Help with Desktop Icons"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by tazmanmn on 2008-04-04
Ok I used the tools I had to begin with and read all the posts I could find. I am in tech support for the phone company so I don't like asking for help unless I am really stumped. I was installing the game Vendetta and did something that made everything on my desktop disappear. I have tried rebooting and going back and looking to see if I typed something in terminal wrong and still don't see the problem. Could someone please help out on this one. I used the ubuntu forum for installing the game and the only thing I changed was the icon I used in the applications menu. 
Thanks
Taz

---

### Post by sancho panza on 2008-04-05
Go to Applications>accessories/system tools>config editor.
In this program, navigate to /apps/nautilus/desktop in the left pane. There you find checkboxes to enable all the desktop icons to be visible. 
The remainings icons should be in your home/Desktop folder.

Cheers!

---

### Post by tazmanmn on 2008-04-05
So I am going to say that something is wrong if my system tools icon does not exist? What would be the other way to go about doing this? And there are no icons in my home/desktop folder...which concerns me

---

### Post by wormser on 2008-04-05
> **tazmanmn said:**
> So I am going to say that something is wrong if my system tools icon does not exist? What would be the other way to go about doing this? And there are no icons in my home/desktop folder...which concerns me

To get your Configuration Editor to show up.  Right click on Applications> Edit Menus> System Tools and check Configuration Editor.  Now you can follow Sancho Panza's directions.

> **sancho panza said:**
> Go to Applications>accessories/system tools>config editor.
In this program, navigate to /apps/nautilus/desktop in the left pane. There you find checkboxes to enable all the desktop icons to be visible. 
The remainings icons should be in your home/Desktop folder.

Cheers!

---

### Post by sancho panza on 2008-04-05
> **tazmanmn said:**
>  And there are no icons in my home/desktop folder...which concerns me
Ok. Here's how it is:
The /home/your_user_name/Desktop will have all the desktop files EXCEPT for the Computer, Your home, Network and Trash icons. These four icons can be enabled by doing what I described earlier.
If you dont have system tools in Applications menu, look in accessories. If you still cant find the config editor, install the package gconf-editor thru synaptic. Then follow my instructions.

---

