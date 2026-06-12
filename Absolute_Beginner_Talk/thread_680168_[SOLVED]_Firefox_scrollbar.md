---
title: "[SOLVED] Firefox scrollbar"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2008-01-27
[FONT="Arial Black"][SIZE="4"]     How  would one be able  to widen the Firefox verticul scrollbar?                                                                                                             [/SIZE][/FONT]

---

### Post by mattismyname on 2008-01-27
I think you'd be more likely to find someone who would know how to do that on a FF forum.  It probably has something to do with developing a new theme for the browser.

---

### Post by johnfarrow on 2008-01-27
Would the FF forum know of the version for Ubuntu, you think?

---

### Post by Fleece Flamingo on 2008-01-27
Yeah, there is really not that much of a significant difference.

---

### Post by nowshining on 2008-01-27
yes u will need to edit a certain file - are u using the default ubuntu theme?

---

### Post by johnfarrow on 2008-01-28
Yes using the default.  Something about making a change in "Chrome"? Don't know for sure if thats it or where its located

---

### Post by nowshining on 2008-01-28
if u were using the non-default i could prob. help u 

u can try 

/usr/share/themes

or somewhere areund there and take a look

i'm using kubuntu so idk really in gnome ' cause when i changed it - i used the mac one from gnome-look.org

---

### Post by mcduck on 2008-01-28
I don't know how to do this _only_ for Firefox, but here's how you can change the scrollbar width in all your programs, without editing the actual GTK theme you are using:

1. Create a file called ".gtkrc-2.0" inside your home if the file doesn't already exist.
2. Add the following code into that file:
```
style "wide-scrollbars"
{
	GtkRange       ::slider_width      = 19
	GtkRange       ::stepper_size      = 19
}
class "GtkRange"  style "wide-scrollbars"
```
3.Save, log out and back again.

Now you have extra-wide scrollbars.  :)

---

### Post by johnfarrow on 2008-02-01
Hey Thanks much for the info.  That .gtkrc-2.0 file worked perfectly.  Now tell me how to add SOLVED to a post.  How to show THANKS.

I appreciate your help

---

### Post by RadiationHazard on 2008-02-01
go up to the top then go to Thread Tools>Mark thread as solved

---

### Post by lswest on 2008-02-01
and to thank people. just click the medal under their posts (next to where the "edit"/"Quote" buttons are)

---

