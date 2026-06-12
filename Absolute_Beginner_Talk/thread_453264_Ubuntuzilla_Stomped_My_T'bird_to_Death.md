---
title: "Ubuntuzilla Stomped My T'bird to Death"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by kobinasucks on 2007-05-24
I recently used Ubuntuzilla to upgrade Thunderbird to Thunderbird 2.0 and since then, I have not been able to launch Thunderbird 1, as well as a few other programs in my Applications list (e.g. Gnomesword2). When I try to launch Thunderbird 1, a tab opens on my lower panel which says "Starting Thunderbird" but then nothing happens. The same happens when I try to open GnomeSword 2 (although Zekr has not been affected) and Thunderbird Profile Manager.

Thunderbird 2.0 has a separate icon and opens just fine but the mail from my Thunderbird 1.0 profile does not show up (which was why I used Ubuntuzilla in the first place). I have a backup of my old 'mozilla-thunderbird' folder on an external harddrive so I think my mail is in there somewhere. I use Thunderbird+Webmail, which deletes the mail it extracts from my Hotmail account, which will leave me with a big problem if I cannot restore Thunderbird 1 or get Thunderbird 2.0 to somehow show the messages.

All that and I cannot get Thunderbird 1 OR 2 to send mail!

Can anyone help?

---

### Post by EndPerform on 2007-05-24
I think I know what's going on.

Check your home directory.  I'm betting there's a .mozilla-thunderbird and a .thunderbird folder.  The .thunderbird folder is probably newer, and that's where 2.0 is storing it's stuff.  If you copy .mozilla-thunderbird as .thunderbird, you should see all of your mail.  Hope this helps.

---

### Post by kobinasucks on 2007-05-24
Ahh nice... that's solved the problem of merging Thunderbird 1 and 2: got all my mail back so I don't think I'll hold onto Thunderbird 1. :D

I still can't seem to send anything from Thunderbird 2.0 though. And those other programs in my Applications Menu still won't start.

Can you help with those?

---

### Post by EndPerform on 2007-05-25
Do you get an error back when you attempt to send mail, or does it just sit?  Also, I'm not sure why your apps won't start from the menu.  Have you tried running one of them from a terminal to see if any errors show?

---

### Post by kobinasucks on 2007-05-28
Sorry for the silence: power cuts and connectivity problems are a b*tch out here in GH. Okay, figured how to take screenshots so here goes:

First up, I get this:

[IMG]file:///home/kobinagraham/Desktop/Screenshot-Enter%20your%20password%3A.png[/IMG]

... at which point I enter my password and after a few moments I get:

[IMG]file:///home/kobinagraham/Desktop/Screenshot-Alert2.png[/IMG]

This might repeat itself once or twice.

That's it. Is it my smtp settings? Or webmail? And if so, what settings do I need to have?P

---

