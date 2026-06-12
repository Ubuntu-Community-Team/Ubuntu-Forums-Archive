---
title: "Format date and time in Ubuntu Gnome"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by sinnerman on 2007-01-03
I need to format date and time in Gnome in next format:
[COLOR="Red"]MM.DD.YYYY HH:MM:SS[/COLOR]
or example 04.01.2007 03:17:15

How?

Thx.

---

### Post by taurus on 2007-01-03
Applications -> Accessories -> Terminal
```
sudo date 040103172007
```

---

### Post by sinnerman on 2007-01-03
Ok again.

Now, date is in format 
[COLOR="YellowGreen"]Thu 4 Jan, hh:mm:ss[/COLOR]
I need next ...
[COLOR="Red"]Thu 04.01.2007 hh:mm:ss[/COLOR]

Thx.

p.s. Not change date only format for display in Gnome.

---

### Post by natirips on 2008-02-05
I was wondering about the same thing, except I'd like my time/date to be formatted as:

YYYY-MM-DD hh:mm:ss
(where :ss at the end isn't necessary)

Is there no way to change this?

---

### Post by bumanie on 2008-02-05
I think if you type 
> man page date in terminal, the linux 'manual page' for setting time and date will appear and explain what you are after. (I think that is the code, if not, it win't work. Or look at this link [http://ubuntuforums.org/showthread.php?t=448935](http://ubuntuforums.org/showthread.php?t=448935)

---

### Post by natirips on 2008-02-05
I was talking about this:
[IMG]http://i246.photobucket.com/albums/gg102/natirips/vriyeme.png[/IMG]
The OS is called "Ubuntu", as if it ware meant for human beings, so why is the date display so heavily coded? Only Neo Anderson could read that date format... :)

---

### Post by Golem XIV on 2008-02-05
Open the configuration editor by running gconf-editor (it's also in the Applications -> System Tools menu but disabled by default. You can use the menu editor to enable it).

Open apps -> panel -> applets and find the clock.  Under custom_format enter the format string in strftime() format (more information on that format [here]("http://www.opengroup.org/onlinepubs/007908799/xsh/strftime.html")).

In your case it would be %Y-%m-%d %H:%M:%S

Note that once you do this, the custom format can be now changed directly through the clock applet so you won't have to go through gconf-editor again :-)

<edit> The format above was for natirips.  Sinnerman, your MM.DD.YYYY HH:MM:SS format would translate to %m.%d.%Y %H:%M:%S </edit>

---

### Post by natirips on 2008-02-05
Edit: My bad! I found the option later under prefs... :)




/*"custom_format" option was not offered under my clock settings, I tried adding it myself, then logged out and logged back in. The clock is still the way it was before :(
The clock is version 2.20.1 . Do you think it would be complicated to make one's own applet?*/

---

### Post by Alex Kay on 2008-06-02
> **Golem XIV said:**
> Open the configuration editor by running gconf-editor ...
Golem, thanks for the info! The only thing is that the "fomat" option has to be set to "custom", otherwise the custom_format string has no influence at all.

---

