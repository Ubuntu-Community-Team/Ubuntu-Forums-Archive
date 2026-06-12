---
title: "xara question"
date: 2006-11-29
forum: Art &amp; Design
---

### Post by kman14 on 2006-11-29
i've just installed xara

and when i open it it gives me this error:

Mailcap file /etc/mailcap, line43: incomplete entry ignored


this is just before it opens to the drawing page.
is this a problem?
the program seems to be working ok.
the plugin button is greyed out but i'm assuming that i get plugins seperately - and if someone could tell me that also that would be great.

thanks.

---

### Post by Rodneyck on 2006-11-29
Funny, I noticed this today as well. I have just started using the program, tinkering really.  

Anyone?

---

### Post by jdarias on 2006-12-05
i installed the autopackage from the xara site and it works fine on edgy.

---

### Post by mrgnash on 2006-12-07
> **kman14 said:**
> i've just installed xara

and when i open it it gives me this error:

Mailcap file /etc/mailcap, line43: incomplete entry ignored


this is just before it opens to the drawing page.
is this a problem?
the program seems to be working ok.
the plugin button is greyed out but i'm assuming that i get plugins seperately - and if someone could tell me that also that would be great.

thanks.

It's not a problem, it doesn't seem to affect performance at all - and it's not unique to Xara either, Bittornado produces the same error message.

As for plugins, I don't think they've been released for the Linux version yet. Wait until the next version perhaps :)

---

### Post by gijsterbeek on 2006-12-19
The mailcap file is used to associate filetypes with their applications. Xara and other application require parsing this file before starting, maybe to define if the .xar extension is still associated with Xara.

But: it chokes on at least two applications and the way they represent themselves in mailcap:

Emerald (Beryl Themer) ( .emerald files)
Google Earth ( .kmz files, among other)

They both use a different approach for their entry in mailcap. You can correct the emerald entry as follows: 

do:

```
sudo nano /etc/mailcap
```Change the lines 

```
application/x-emerald-theme
        ext: emerald
```into one line reading

```
application/x-emerald-theme; nametemplate=%s.emerald
```This did the trick, and Emerald themes are still associated with the Emerald Settings Manager.

---

### Post by aidanr on 2007-01-23
thanks gijsterbeek, just had this problem with xara and dvd styler, that fix worked a treat

---

