---
title: "change default programs."
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by linuxcity on 2006-05-11
How do I change the default program for text file? Everytime I click on the Openoffice.org file, it automatically opens with Getedit. Of course, Getedit cannot open Openoffice.org format and give error.
How do I change it so it opens with Openoffice.org by default instead of Gedit?

Second, everytime I log on, the Totem player and Natilus loads when starts up. How can I disable that so none of these start when I log onto the desktop?

---

### Post by Al3xanR0 on 2006-05-11
[QUOTE=linuxcity]How do I change the default program for text file? Everytime I click on the Openoffice.org file, it automatically opens with Getedit. Of course, Getedit cannot open Openoffice.org format and give error.
How do I change it so it opens with Openoffice.org by default instead of Gedit?

Second, everytime I log on, the Totem player and Natilus loads when starts up. How can I disable that so none of these start when I log onto the desktop?[/QUOTE]

Ubuntu or Kubuntu which one are you using?

---

### Post by linuxcity on 2006-05-11
I'm using Ubuntu Dapper, latest update (GNOME).

---

### Post by 5-HT on 2006-05-11
[quote=linuxcity]...how do I change it so it opens with Openoffice.org by default instead of Gedit?...I'm using Ubuntu Dapper, latest update (GNOME).[/quote][LIST=1]
[*]Open Nautilus
[*]Right-click on on a text file
[*]Select properties
[*]Select 'Open With' tab
[*]Add 'OpenOffice.org Writer'
[*]Either select the little radio button for OpenOffice or remove 'Text Editor'[/LIST][quote=linuxcity]Second, everytime I log on, the Totem player and Natilus loads when starts up. How can I disable that so none of these start when I log onto the desktop?[/quote] 
Go to System -> Preferences -> Sessions

See if either of them are listed under 'Startup Programs' and remove accordingly.
If they are not set to start automatically, then make sure "Automatically save changes to session" is selected. 
Then just close any programs you do not want to be saved in your session and logout. 
When you login, they should be gone and you can then deselect that "Automatically save..." if you do not want that feature.*

*I described it this way because I do not get asked whether or not I would like to save my session in Dapper (not sure why as 'select on logout' is checked, but it doesn't bother me). If you do get asked whether you want to save the session then simply select 'yes' after you've closed the programs you would not like saved in the session (no need to set the automatic option).

EDIT: Missed that session question, thanks for catching it eentonig. Added the above.

HTH

---

### Post by eentonig on 2006-05-11
And for the startup question.

Go "System", "preferences", "Sessions"

Click "Startup programs" and delete the ones that irritate you.

---

### Post by linuxcity on 2006-05-11
Thanks 5-TH, that resolved both of the issues (edited)

---

