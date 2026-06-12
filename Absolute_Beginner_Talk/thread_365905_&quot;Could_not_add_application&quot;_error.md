---
title: "&quot;Could not add application&quot; error"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Ginger The Cat on 2007-02-20
Hi,

Sometimes I want to open a file with other than the default application. e.g. sometimes I might want to open a style sheet (.css file) with gedit and sometimes with Quanta Plus a web development app.

If I right click on the file I see an "Open" option and a "Open with other Application..." option.

If I select the "Open with other Application" option I get the chance to choose my application. But whatever I choose I get the error "Could not add application. Could not add application to the application database"

I'm using Ubuntu Dapper.

I wondered if it was a permissions thing. Surely I don't need to be root when I need to do this. I noticed my .gnome/apps folder is owned by root and has 700 permissions. Don't know if this is relevant?

Cheers

Mike

---

### Post by jpeddicord on 2007-02-21
> I wondered if it was a permissions thing. Surely I don't need to be root when I need to do this. I noticed my .gnome/apps folder is owned by root and has 700 permissions. Don't know if this is relevant?That is your problem right there. To fix it, press Alt+F2 and type `gksu nautilus`. Type in your password, and the Nautilus will open.

Then, navigate to your home folder, then to .gnome. Right-click on the apps folder, and select Properties. On the permissions tab, change the Owner and Group both to your username. Close the window, then close the root file manager. You should now be able to save the list of apps properly.

Jacob

---

### Post by kitch on 2007-04-27
This is the most helpful reply I have seen yet! Thanks, BUT I am also trying to get Acroread to work as the default pdf viewer (problems with printing in evince. I can't add it as an application either.
please help.:(

---

