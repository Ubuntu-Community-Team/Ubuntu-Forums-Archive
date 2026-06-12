---
title: "Evil Error Message"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by wog on 2006-08-24
Every time I start Azureus I get [this]("http://flickr.com/photos/woggie/223486973/") error message down in the lower right corner of the screen. I've checked the router and it's set up properly, so port 43259 is set for UDP. Even Azureus claims the port is open.

Problem 1: Why do I get this error message?

Problem 2: The Hide and Hide All buttons on this window don't work, so it permanently covers the trash can and the desktop chooser boxes. How can I get rid of this window so I can use those icons? -- Hint: It won't drag out of the way either.

---

### Post by Metacarpal on 2006-08-24
I had the same problem.  No idea what caused that.  I ended up just uninstalling Azureus and going with Bittornado.

---

### Post by nudnik on 2006-08-24
I am told there is a problem with the default Java configuration, and that installing the latest Java runtime from Sun will fix any problems, but I cannot confirm this.

I too use Bittornado as it seems to work best with the current version of Ubuntu.

---

### Post by wog on 2006-08-25
I will try Java, then.

The problem with BitTornado is it can't keep track of more than one torrent at a time using just one port. I'd prefer not to open up a port for misuse by attackers if I can help it, and reconfiguring my router every time I want to get a second file seems like overkill. Some files just take a long time to finish seeding.

---

### Post by wog on 2006-08-25
I solved it.

Go to Tools > Options > Plugins and select UPnP and see if the first box is checked. If it is, uncheck it and reboot. The message box will never come up.

:)

---

### Post by Metacarpal on 2006-08-28
Nice!

---

### Post by davebgimp on 2006-08-28
You can also go to Help>About Azureus. Once the About window pops up, strangely enough, you can close all the stuck pop-ups.

---

