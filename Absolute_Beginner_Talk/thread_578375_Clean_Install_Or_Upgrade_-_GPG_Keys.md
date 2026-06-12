---
title: "Clean Install Or Upgrade? - GPG Keys"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-10-17
1 day to go for Gutsy. Cant wait. 

Not really sure whether i should do an upgrade. I have heard they can break packages and stuff and basically just mess things up a bit. I was planning to do a completely clean install but then i realised i would need to generate new GPG Keys for enigmail and stuff, and i could really do without that.

Is there a way to keep my GPG Keys (and things like my Apache settings, and my SSH keys) on an external HD so i can use them on a clean Gutsy install?

---

### Post by jmaryinchina on 2007-10-17
Your apache settings are in /etc/apache*
You may need to save /etc/php* as well

I advise you to copy /etc and your /home/your_user_name to your ext hard disk.

Then you can pick up what you want.

---

### Post by Seisen on 2007-10-17
I have upgraded numerous times and never have had a problem with it. Backup your information you need and then trying a dist-upgrade then if nothing breaks than you have nothing to worry about, if it breaks something it can always be fixed.

---

