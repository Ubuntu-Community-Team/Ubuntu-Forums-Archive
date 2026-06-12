---
title: "Changing gnome-panel text color"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-05-25
Hello, everyone.

I am attempting to change the text color of my gnome-panels; I was trying to use [this tutorial]("http://brentroos.com/2006/07/07/change-gnome-panel-text-color/").  Unfortunately, the advice given in the previously mentioned tutorial did not work.  Does anyone know exactly what I should do?  I'm using Feisty.

Thanks for any suggestions.

Take care.

---

### Post by Pragmatist on 2007-05-25
I just used the tutorial and it worked for me.
```
gedit .gtkrc-2.0
```

And now don't cut-and-paste the text on the link you give, instead cut-and-paste this:
[http://brentroos.files.wordpress.com/2007/01/gtkrc-20.txt](http://brentroos.files.wordpress.com/2007/01/gtkrc-20.txt)

Save and then type:
```
killall gnome-panel
```

---

### Post by crossedout on 2007-05-25
Having learned to avoid just blindly adding or copy/paste code, I recommend navigating to your themes folder:
.themes/<YourThemeHere>/gtk-2.0

And open with gedit the file gtkrc.

Find the line labeled:
```
fg[NORMAL]="#ffffff"
```
Note: the "#ffffff" may be different for you.

Change the #ffffff to #<YourColorCodeHere>
Save.
Refresh your theme.

You can figure out your color code via Gimp's color chooser.

-Xout

---

### Post by Pragmatist on 2007-05-25
> **crossedout said:**
> Having learned to avoid just blindly adding or copy/paste code...

It is not blindly copy-and-pasting code if you understand what your copying and pasting; and, if others, who are helping you, have tried it. Likewise, if the OP were to follow your instructions without any thought, he would be doing it "blindly".

---

### Post by RKCole on 2007-05-27
Pragmatist and crossedout,

Thanks for your replies.  Pragmatist: I right-clicked on the link you gave and saved ti as .gtkrc-2.0 in my /home directory.  I should have tried to do that in the first place, as I just originally copied/pasted the text and tried to manually replace the quotation marks.  I think that this was the issue, as all works just fine now.  Here's a screenshot.

Now all I need to do is find a nice outer space background rather than just plain black.

I'll mark this as solved.

Thanks and take care.

---

### Post by Nikron on 2007-05-27
> **crossedout said:**
> Having learned to avoid just blindly adding or copy/paste code, I recommend navigating to your themes folder:
.themes/<YourThemeHere>/gtk-2.0

And open with gedit the file gtkrc.

Find the line labeled:
```
fg[NORMAL]="#ffffff"
```
Note: the "#ffffff" may be different for you.

Change the #ffffff to #<YourColorCodeHere>
Save.
Refresh your theme.

You can figure out your color code via Gimp's color chooser.

-Xout

Obviously you should not just change any random foreground color.  Make sure it's the right widget, otherwise half your theme will be screwed up.

---

### Post by quinnten83 on 2007-05-27
I have not been able to find the gtkrc-2.0 file.
browsing for it did not deliver the results and a search for it yields nothing.
I also tried the command given here, but no luck.
Is this because I'm using beryl? I really would like to change the text color, because I often use dark-colored themes.

---

### Post by RKCole on 2007-05-27
Hello, quinnten83.

My apologies.  I forgot to mention...I had the same issue in that I could not find a .gtkrc-2.0 file in my /home directory.  Actually, there wasn't one there at all.  I just saved that text file in my /home directory (/home/my_username) as .gtkrc-2.0.  After I edited it the way I wanted it, I just did (in a terminal)

```

killall gnome-panel

```

I just tested ti with Beryl and the panel changes still stand.

Beryl is something amazing. :)

Hope this helps.

---

