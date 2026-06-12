---
title: "Firefox Logo"
date: 2005-04-26
forum: Art &amp; Design
---

### Post by Sionide on 2005-04-26
Can anyone write a step-by-step guide on how to get the proper Firefox logo onto Firefox?? I know we can't bundle the icon with the distribution due to the dodgy Mozilla copyrights on it but is anything stopping us adding it in afterwards??

---

### Post by artnay on 2005-04-26
Download installer from The Mozilla Foundation's web site ([here](http://www.mozilla.org/products/firefox/)), apt-get remove the Ubuntu package, extract the package you downloaded (tar xvzf firefox-1.0.3.installer.tar.gz), move to the directory that was just created (cd firefox-installer) and execute firefox-installer (./firefox-installer). 

After the installiation, all your settings should be just as they were. If you installed 1.0.3 to some other directory than where the previous version of Firefox was before, you might want to do the following:
1. System -> Preferences -> Preferred Applications. Insert the location of firefox executable to custom command form and add %s after that.
2. Create a new symlink to /usr/bin to point the new location of new executable.
3. Fix the location of the executable to the icons that already exist and point to the old firefox executable.
4. apt-pin the mozilla-firefox package, so it won't get downloaded even if you do apt-get upgrade etc.

Why all that hassle? First of all, you get the long-desired Firefox logo.  \\:D/  1.0.3 is a bit safer than the package provided by Ubuntu, too.

BTW, If you know a decent and easy way to change the logo, you should add the answer to ubuntuguide or how-to section. This question has been asked so many times...

---

### Post by bored2k on 2005-04-26
He just wanted the logo :roll:. I uploaded it for you for you here:
[URL=http://www.imageshack.us][CENTER][img]http://img105.echo.cx/img105/1515/firefoxrgb2oa.png[/img][/CENTER]
Name that logo mozilla-firefox.png and save another copy with a .xpm extension , so once you have
mozilla-firefox.png and mozilla-firefox.xpm, copy them to /usr/share/pixmaps [need root access] and log in/out ;). If you have other themes, you would have to go to /usr/share/icons/ and copy those files to your theme directory [with their proper names].

---

### Post by TravisNewman on 2005-04-26
bored-- that only changes the launcher doesn't it?-- the plain globe is everywhere else.

---

### Post by bored2k on 2005-04-26
[QUOTE=panickedthumb]bored-- that only changes the launcher doesn't it?-- the plain globe is everywhere else.[/QUOTE]
 That's correct :-\. I was going to say it changes everything, but I just remembered I downloaded the .sh from mozilla.org.

To get the full effect I believe you'd have to go to 
/usr/lib/mozilla-firefox/icons
/usr/lib/mozilla-firefox/chrome/icons/default
 and paste your custom icon there.
[[IMG]http://img184.echo.cx/img184/7902/screenshotusrlibmozillafirefox.th.png[/IMG]](http://img184.echo.cx/my.php?image=screenshotusrlibmozillafirefox.png)

BTW [img]http://img231.echo.cx/img231/5930/document8nq.png[/img] is another firefox png.

---

### Post by Sionide on 2005-04-26
Woo, this is exactly what I was after! Thanks a lot - I'm trying it out now, would it be worth putting together a HOWTO for it? I think a lot users would do it if they knew how... I missed the beloved Firefox logo!

Edit: Just logged back in and it works perfectly! Thanks, that was a lot easier than I thought it might be... I'll make a quick HOWTO later on, as long as we're sure this isn't breaking any of Mozilla Foundation copyrights on it?? What license does the logo have anyway?

---

### Post by bored2k on 2005-04-26
[QUOTE=Sionide]Woo, this is exactly what I was after! Thanks a lot - I'm trying it out now, would it be worth putting together a HOWTO for it? I think a lot users would do it if they knew how... I missed the beloved Firefox logo!

Edit: Just logged back in and it works perfectly! Thanks, that was a lot easier than I thought it might be... I'll make a quick HOWTO later on, as long as we're sure this isn't breaking any of Mozilla Foundation copyrights on it?? What license does the logo have anyway?[/QUOTE]
 It's not like your distributing the logo or anything, after all, its your computer, you can do as you please. Maybe I could help you make a more clear way to do this for the How-to [it's your idea, you should do it] ;).

---

### Post by Sionide on 2005-04-27
Yeah, but if I upload the logos to the gallery for others to download? Is that then distributing?? I dunno, I think the dodgy licence (license?) on the logo is pretty silly anyway. Okay, I'll do it, feedback will be appriciated..

---

### Post by bored2k on 2005-04-27
[QUOTE=Sionide]Yeah, but if I upload the logos to the gallery for others to download? Is that then distributing?? I dunno, I think the dodgy licence (license?) on the logo is pretty silly anyway. Okay, I'll do it, feedback will be appriciated..[/QUOTE]
 You can always upload the logos through imageshack.us. Plus, the hideous logo can be found at mozilla.org anyway. Imageshack-Forums have no connection at all. You can just take my picture links, theyre still active.

---

### Post by Sionide on 2005-04-27
[http://ubuntuforums.org/showthread.php?t=30133](http://ubuntuforums.org/showthread.php?t=30133) :) My first HOWTO!! Woohoo...

---

### Post by Mr Hatch on 2005-05-05
[QUOTE=Sionide][http://ubuntuforums.org/showthread.php?t=30133](http://ubuntuforums.org/showthread.php?t=30133) :) My first HOWTO!! Woohoo...[/QUOTE]
 =D> 

Just a little flattery ;)

---

### Post by hazza96 on 2005-05-06
[QUOTE=Sionide]I know we can't bundle the icon with the distribution due to the dodgy Mozilla copyrights on it[/QUOTE]
Wow, really, what sort of messed up copyright are they putting on the icons? I am not aware of any other app that does not let you bundle the icon with it.

Anyone know a reason behind the decision that does not allows the bundling of the icon?

---

