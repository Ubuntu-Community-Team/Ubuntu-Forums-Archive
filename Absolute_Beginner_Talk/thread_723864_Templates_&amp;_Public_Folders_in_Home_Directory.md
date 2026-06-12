---
title: "Templates &amp; Public Folders in Home Directory?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-03-13
Why are the "Templates" and "Public" directories for (they are in my home directory)?  I didn't create them.  There's nothing in them.  What do they do?

---

### Post by czeckk on 2008-03-14
There arent any purposes for them, you can delete them if you want...the public folders hould have some stuff in it, but if there isnt than who cares...delete them or rename them, it won't affect anything.

---

### Post by dcstar on 2008-03-14
> **F4RR4R said:**
> Why are the "Templates" and "Public" directories for (they are in my home directory)?  I didn't create them.  There's nothing in them.  What do they do?

Various apps can create directories as you install or run them, as we have no idea what apps you have on your system we can't tell you why they are there or what they are for.

---

### Post by PeterJS on 2008-03-14
They're created by Gnome the first time you log in. The templates folder is where Gnome looks for templates for the create file right click option in nautilus. Public is for sharing data between users if the system had more restritive permissions on the home directory, but with the lax permissions, and (I assume) a single human user, it's pretty much useless.

---

### Post by mcduck on 2008-03-14
To use the Templates directory just put files of any type you want in there. For example, you could create empty text document in OpenOffice and save it into ~/Templates as "New OpenOffice text document.odt". After that the right-click on the desktop and in Nautilus windows would have a new option, "Create document/New OpenOffice text document".

I have  created template documents for all types of files I often need to create, like A4 and web site sized SVG images, a template for XHTML file with all the usual headers and stylesheet stuff already included, and templates for different reports and documents I need to write sometimes.


If you want to use this feature but don't like seeing the Templates directory in your home you can hide it this way:

In your home directory create a new fiel called ".hidden". Open it with text editor and add "Templates" on the first row. Then save the file, and close any Nautilus windows you may have open. The Templates directory is now hidden, you can press Ctrl-H in Nautilus to see it. You can hide any files and directories this way, just add each on their own line to the ".hidden" file that is in the same directory.

---

### Post by oxsyn on 2008-03-14
> **mcduck said:**
> To use the Templates directory just put files of any type you want in there. For example, you could create empty text document in OpenOffice and save it into ~/Templates as "New OpenOffice text document.odt". After that the right-click on the desktop and in Nautilus windows would have a new option, "Create document/New OpenOffice text document".

I have  created template documents for all types of files I often need to create, like A4 and web site sized SVG images, a template for XHTML file with all the usual headers and stylesheet stuff already included, and templates for different reports and documents I need to write sometimes.


If you want to use this feature but don't like seeing the Templates directory in your home you can hide it this way:

In your home directory create a new fiel called ".hidden". Open it with text editor and add "Templates" on the first row. Then save the file, and close any Nautilus windows you may have open. The Templates directory is now hidden, you can press Ctrl-H in Nautilus to see it. You can hide any files and directories this way, just add each on their own line to the ".hidden" file that is in the same directory.
Before I saw your answer, I listened to the advice of a previous poster that suggested the Templates directory is used for nothing and that I should just delete it.  I did.
After I saw your response, I recreated it.  I then created a blank Open Office Writer document in the Templates directory & named it: "Writer.odt"
When I right-click in the window and select "Create Document" I see "No templates installed."
I tried logging out & back in.  That didn't help.  I restarted the computer, that didn't help.

**Any suggestions?**

---

### Post by mcduck on 2008-03-19
I tried looking around the Configuration Editor to see if there was some key or something that sets the template directory, but I couldn't fine anything. You could try to find the Nautilus setting files from your home dir and removing them, that should reset Nautilus settings and probably solves your problem as well..

---

### Post by huffy318 on 2008-07-13
I got my templates to show up again by running xdg-user-dirs-gtk-update 
( xdg-user-dirs-update didn't help).
When i ran the update, it popped up a window saying something about changing a language, and I had previously changed my language settings, so maybe that caused the template feature to break.   It created all the other dirs again that I had deleted, but it also made nautilas see the templates.

---

