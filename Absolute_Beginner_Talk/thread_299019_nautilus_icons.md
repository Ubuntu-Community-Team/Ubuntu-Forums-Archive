---
title: "nautilus icons"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by daz4126 on 2006-11-13
Hi,

I'm having a few issues with Nautilus.

I have installed a custom icon theme, but want to combine the best icons from a few different ones. What is the best way to do this? Should I make my own theme?

How do I change the icons that appear for different mime types? For example I'd like to use the firefox logo for html files.

And when I change the default logo of an application, how do I change the little logo that appears in the gnome panel. Again, Firefox still shows that little globe thing up there.

And last but by no means least, how do I get thumbnails for images. For some reason, some files do this but others don't, most annoyingly, all my icon files don't show thumbnails, so I don't know which are which.

cheers,

DAZ

---

### Post by dbbolton on 2006-11-13
i would say that you'll have to just compile your own theme.

> how do I change the little logo that appears in the gnome panel

do you mean as a launcher or a notification area icon?

---

### Post by daz4126 on 2006-11-13
Thanks for the reply, so how do I compile my own theme then?

I mean when you have the different apps running, you can see little rectangles in the menu bar (mines at the top, but I think it defaults to bottom) that show which program is running. The firefox one shows a globe even though I have changed the launcher icon to the branded fox logo.

cheers,

DAZ

---

### Post by dbbolton on 2006-11-13
here's how i would try to make an icon theme:

pick the one that has the most icons you want to use. then go to:
/usr/share/icons/(name of icon theme) 

copy that folder and paste it onto the desktop. then go through and replace the icons you don't want with the ones from the other theme(s). when it's finished (probably a good idea to re-name the parent folder on the desktop to whatever you want) right-click the folder and do "create archive."

then open
system > preferences > themes
and drag the archive onto the window to install it, and select it under "theme details."


about your little rectangles in the menubar, i'm not sure. maybe that's just on edgy (i'm running dapper).

---

### Post by daz4126 on 2006-11-14
Thanks for that. I found that the themes were being installed into a hidden folder in my home directory called .icons, so will use my favourite (Vista Inspirate) and modify it.

Does anybody have any idea why since updating to edgy, I get no previews of images or movies anymore on the desktop????

DAZ

---

### Post by crossedout on 2006-11-14
You'll also need to edit the index.theme file unless you plan to overwrite an existing theme.
Follow this [link]("http://www.ubuntuforums.org/showthread.php?t=251567&highlight=Xout") for a HowTo create a Custom Icon Theme.

-Xout

---

