---
title: "Is it possible to have a Windows style login?"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by FireFusion on 2006-06-29
I'm really trying hard to convert my family to using Ubuntu. All is going well except the way you log in gets LOTS of complaints. Is there any way I could make it more like windows? Where you select a picture with you're name by it and don't need a password. 

Thank you for your help.

---

### Post by H.E. Pennypacker on 2006-06-29
You can definitely do that.  You're talking about the GDM screen, or the log-in screen.  I am not so sure you can change the log-in screen in Windows, while you definitely can do this with Ubuntu/Gnome.  

The best thing to do would be to head over to Gnome-Look.org, and see which log-in screen you like best:

[http://www.gnome-look.org/index.php?xcontentmode=150](http://www.gnome-look.org/index.php?xcontentmode=150)

There should be something you'll like, but I am not sure there is one that will allow you to change the image corresponding to a user.  There probably is something like this.  I'll look around and see what I find.

---

### Post by glotz on 2006-06-29
methinks system > admin > login > style : face browser
each user can select his/her face in system > prefs > about me

---

### Post by Jucato on 2006-06-29
some of the installed login styles have a sort of list of users that you could choose from.

I'm just not sure if it's advisable to have users without passwords.

---

### Post by uzi09 on 2006-06-29
lol, i know what you mean. i gave up :(

here's one that's similar, but not quite MS:
[http://www.gnome-look.org/content/show.php?content=37395](http://www.gnome-look.org/content/show.php?content=37395)

---

### Post by H.E. Pennypacker on 2006-06-29
> Where you select a picture with you're name by it 

To have a picture next to your username, go to System > About Me.  There, click on the square icon to the left of the username.  It will now allow you to look for an image that you can use for login purposes.  The next time you log-out, you should see this new picture you've selected beside your username.

Do the same thing with other members of your family.  This will work with many GDM (log-in) themes, but if not, try whichever GDM theme you like, and pick the one that will show a picture.  If you don't care about a particular GDM theme, go to System > Administration > Login Window, and for "Style," select "Plain with face browser."  "Plain with face browser" should show the image.  

> 
and don't need a password. 

To do that, go to System > Administration > Login Window.  Select the security tab, and check off "Enable automatic login" with all the users who want automatic login.  That should take care of the trick, but if it doesn't, let us know.

If it turns out this does not work and you're still being asked for a password when logging-in, first make sure that you have GDM 2.14.9 installed.  If that does not work, we'll follow up on this, but this is the general solution.

---

### Post by Rich3077 on 2006-06-29
[QUOTE=H.E. Pennypacker]To have a picture next to your username, go to System > About Me.  There, click on the square icon to the left of the username.  It will now allow you to look for an image that you can use for login purposes.  The next time you log-out, you should see this new picture you've selected beside your username.

Do the same thing with other members of your family.  This will work with many GDM (log-in) themes, but if not, try whichever GDM theme you like, and pick the one that will show a picture.  If you don't care about a particular GDM theme, go to **System > Administration > Login Window, **and for "Style," select "Plain with face browser."  "Plain with face browser" should show the image.  



To do that, go to System > Administration > Login Window.  Select the security tab, and check off "Enable automatic login" with all the users who want automatic login.  That should take care of the trick, but if it doesn't, let us know.

If it turns out this does not work and you're still being asked for a password when logging-in, first make sure that you have GDM 2.14.9 installed.  If that does not work, we'll follow up on this, but this is the general solution.[/QUOTE]

I dont have an option for **Login Window**, is there a package or something I am missing to get this to show?

Peace
Rich

---

### Post by Apple 101 on 2006-06-30
Check the Preferences menu too... I'm not in Ubuntu right now so I can't check...

---

### Post by H.E. Pennypacker on 2006-06-30
[QUOTE=Rich3077]I dont have an option for **Login Window**, is there a package or something I am missing to get this to show?

Peace
Rich[/QUOTE]

If Login Window is not in System > Administration, you must have removed it.  Go to Applications > Accessories and pick Alacarte Menu Editor.  In Alacarte, select "System."  There, you'll find a list of things that are supposed to show up in the System > Administration menu, and if something is unchecked, it won't show up.

Look for "Login Window" on that list, and make sure it is checked.  

This can be the only explanation for you not seeing Login Window.  I don't know what version of Ubuntu you are using, but all my instructions relate to Ubuntu 6.06 Dapper Drake with Gnome 2.14.

---

### Post by Rich3077 on 2006-06-30
Thanks for that tip H.E. Pennypacker, thats what I needed.


Peace
Rich

---

