---
title: "Advantix? Lost my OpenOffice Suite"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-04-11
First, my ISP allows short connection times. Workdays 60 min. After midnight, 4 hour sessions.

I used Advantix to download/install OpenOffice 2.0

In the morning, I re-booted and called OpenOffice Writer. A small window came up, saying:

[B]Cannot launch entry

Details: Failed to execute child process "/usr/bin/oowriter" (No such file or directory)[/B]

I looked in usr/bin/ for any versions of oo, but found only /usr/bin/open

which seems to be an application/x-executable

Is it "safe" to click this icon in /usr/bin/ ?

A google search shows this to probably be the icon on the panel no longer points to the correct directory/file.

Anybody know how to fix this?

---

### Post by picpak on 2006-04-11
Press Alt+F2 and type in oowriter2.

---

### Post by Mark_in_Hollywood on 2006-04-11
The response to ALT-F2 / oowriter2 is:

Cannot display location 'file://oowriter2'

Details: There is no default action associated with this location.

---

### Post by Mark_in_Hollywood on 2006-04-17
Success.

Problem resolved by updating 145 meg of Breezy updates and re-downloading OOo via Synaptic, an additional 134 meg. Whew!

---

