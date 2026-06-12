---
title: "dissapearing desklets"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2008-04-03
hi,

my screenlets must be re-opened everytime i want to use then despite the auto-on box being checked in the screenlet manager, i think that every time i close the screenlet manager it doesnt implement or save changes.
any help apreciated.
sorry bout spelling/grammar/syntax/etc

---

### Post by kane77 on 2008-04-03
I had this problem too.. and found no solution but created a script that would at startup start all the screenlets... if you want I will look for it

---

### Post by stubblepoo on 2008-04-03
that would be great, how would i get it?

---

### Post by Tristam Green on 2008-04-03
Are you enabling "Automatically Start on Login" in screenlets-manager?

Also, you can go to Preferences>Sessions and add your individual screenlets to start automatically.

example, using [Clear Weather]("http://www.gnome-look.org/content/show.php/Clear+Weather+Screenlet?content=66609"):

[quote=Prefs>Sessions>New]

edit Startup name:  ClearWeatherScreenlet
Command:~/.screenlets/ClearWeatherScreenlet.py > /dev/null
Comment: Starter for ClearWeatherScreenlet[/quote]


Good luck!

---

