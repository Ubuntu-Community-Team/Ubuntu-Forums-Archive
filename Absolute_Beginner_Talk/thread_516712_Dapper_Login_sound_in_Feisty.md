---
title: "Dapper Login sound in Feisty"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-08-03
I love the login sound for dapper and got tired of feisty's. I have the install disk for dapper. where can I find the login sound... and once found, how can I apply it to my Feisty system?

---

### Post by nichipet on 2007-08-03
I don't know which file it is, but this article is on how to disable the login sound:

[http://www.howtogeek.com/howto/ubuntu/disable-the-login-sound-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/disable-the-login-sound-on-ubuntu/)

I assume changing the sound can be done from there as well. Maybe seeing the file in use now can help you find it on Dapper.

---

### Post by coffeecat on 2007-08-03
Boot up the Dapper live CD and have a look in /usr/share/sounds. I think the log in sound is called startup.wav. Copy it and rename it because the new login sound in Feisty is also called startup.wav. When you're back in Feisty, copy the renamed file into /usr/share/sounds and select it for your login sound in System > Preferences > Sound and under the Sounds tab.

Don't forget that all the subdirectories under /usr are owned by root so you'll have to use sudo to copy your renamed sound file into /usr/share/sounds.

If you're unsure about any of the steps just post back.

---

