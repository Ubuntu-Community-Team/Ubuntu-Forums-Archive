---
title: "Can I copy Pidgin settings from Ubuntu to Windows?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by soleille on 2008-03-10
I mainly use Ubuntu but have a Windows 2000 partition as a fallback (due to BIOS age, Ubuntu doesn't always start up)

I'm setting up Windows afresh and would like to save me the hassle of reentering all my different accounts, passwords etc., is there a way to just copy these settings?

I thought replacing the prefs.xml in the .purple directory with the one from Ubuntu would do it, but I still have "no accounts enabled"  ...

Any ideas? Or will I have to add each and every one of my multiple entities on several networks by hand again?

---

### Post by Nirevus on 2008-03-10
It should be possible just by copying the entire .pidgin folder from Ubuntu into Windows. I can't really see a problem with doing that, and it would ensure that all your configuration files are copied over.

---

### Post by Battalion on 2008-03-10
When i was using Kubuntu feitsy i had problems with this.  I copied all the config files but windows had trouble processing them and some contacts work others didn't.  Maybe i missed something so be very sure when coping the config files! don't miss anything

---

### Post by hyperair on 2008-03-10
It's probably an issue with the newlines. All the stuff are in XML files. As such, newlines do matter. In Windows its \r\n whereas in Linux its \n. \r = carriage return and \n = line feed.

---

