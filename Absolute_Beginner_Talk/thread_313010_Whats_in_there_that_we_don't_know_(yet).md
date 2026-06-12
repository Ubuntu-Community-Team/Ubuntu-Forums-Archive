---
title: "Whats in there that we don't know (yet)?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by rudlavibizon on 2006-12-05
I was looking for a simple calendar to use for reminders and at one moment i thought why not try just typing in console "calendar" to see if there is anything already installed and to my surprise i got this:

"Dec 05  Walt (Walter Elias) Disney born in Chicago, 1901
Dec 05  End of Prohibition, 1933 (at least the alcohol part)
Dec 05  Phi Beta Kappa founded, 1776
Dec 05  The Eighteenth Amendment repealed, ending Prohibition, 1933
Dec 05  Death of Smaug
Dec 05  Mozart dies, 1791
Dec 05  Aujourd'hui, c'est la St(e) Gérald.
Dec 05  N'oubliez pas les Géraldine !
Dec 05  Bonne fête aux Géraud !
Dec 05  Aujourd'hui, c'est la St(e) Sabas.
Dec 05  Mozart gestorben, 1791
Dec 06  St. Nicholas' Day
Dec 06  Independence Day in Finland
Dec 06* Parashat Va-Yeze
Dec 06  First sound recording made by Thomas Edison, 1877
Dec 06  The Rolling Stones play Altamont Speedway near San Francisco, 1969
Dec 06  N'oubliez pas les Nicolas !
Dec 06  Neige de saint Nicolas
        Donne froid pour trois mois.
Dec 06  Nikolaus"

So i thougt what else is  installed which may be fun or  useful. 
 
What command do i type to see what programs are installed and what commands are used to start them up? :-k

Also, you could post something you discovered.

---

### Post by bodhi.zazen on 2006-12-05
To get a listing of all installed packages, in a terminal:

```
dpkg –get-selections | grep -v deinstall > ubuntu-files
```

Now in a terminal:```
gedit ubuntu-files
```

This list will be several pages long.

---

### Post by Rui Pais on 2006-12-05
funny, isn't it?

now if you type **cal** you got what you want, but much less funny ;)

---

