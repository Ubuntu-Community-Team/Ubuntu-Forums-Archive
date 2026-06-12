---
title: "Zenburn theme for gnome terminal?"
date: 2009-03-09
forum: Art &amp; Design
---

### Post by chombee on 2009-03-09
Wondered if anyone has a config file for a zenburn profile/color scheme for the gnome terminal?

A %gconf.xml file is linked to this page:

[http://slinky.imukuppi.org/zenburnpage/](http://slinky.imukuppi.org/zenburnpage/)

but I followed the instructions and it doesn't seem to work. Thanks

---

### Post by kindofabuzz on 2009-04-07
> **chombee said:**
> Wondered if anyone has a config file for a zenburn profile/color scheme for the gnome terminal?

A %gconf.xml file is linked to this page:

[http://slinky.imukuppi.org/zenburnpage/](http://slinky.imukuppi.org/zenburnpage/)

but I followed the instructions and it doesn't seem to work. Thanks

that link says it's for Vim, not gnome-terminal.

---

### Post by Scott19 on 2009-04-07
:KS Hey..

Yeah..I agree with kindofabuzz... That link is more on VIM and not Gnome Terminal. But on the **"List of known ports and derivatives"** section of the link, I found this statement - Andrew Janke did a Zenburn-configuration file for Gnome Terminal. And when you click the gnome terminal, something will show up and it has this note:
"This XML file does not appear to have any style information associated with it. The document tree is shown below."

I don't know what that is... But I think you should read more..

:-k

---

### Post by ynef on 2009-05-16
Yeah, the procedure in his comment notes won't work. As a workaround, do the following:

[LIST=1]
[*]Make sure that your menu bar is showing. If it is not, right click on the terminal window and select "Show menubar".
[*]In the Edit menu, select "Profiles..."
[*]Create a new profile with whatever name you like.
[*]In your terminal, start the program "gconf-editor".
[*]Navigate to "/apps/gnome-terminal/profiles/" and then to whatever you called the profile. If it does not show up with name, it might be called something like "Profile0" or something. If the latter is the case for you, check the "visible_name" property, which should match your chosen name.
[*]Double click on the "palette" property.
[*]Remove the current contents, and paste the following (without the quotes, and it should all be on one line -- perhaps paste it into the Text Editor first to make sure that it will come out right): "#3F3F3F3F3F3F:#FFFF00000000:#EFEFEFEFEFEF:#E3E3CECEABAB:#DFDFAFAF8F8F:#CCCC93939393:#7F7F9F9F7F7F:#DCDCDCDCCCCC:#3F3F3F3F3F3F:#FFFFCFCFCFCF:#EFEFEFEFEFEF:#E3E3CECEABAB:#DFDFAFAF8F8F:#CCCC93939393:#7F7F9F9F7F7F:#DCDCDCDCCCCC". This is the contents of the file at the web page.
[*]Close everything related to gconf-editor.
[*]Switch to the profile you selected via the Terminal's Edit menu, and (if you want) change it to the default profile in Edit -> "Profiles...".
[/LIST]

It turns out that I didn't even like the zenburn theme for the terminal, but I figure that this post will be of help to those who might.

---

### Post by mrgnash on 2009-08-14
Thanks for this; I was becoming very frustrated until I found your solution :lolflag:

---

### Post by guerremdq on 2009-12-22
can i use this por xterm ? do you knwo how ?

---

