---
title: "Screen refresh rate only 50 Hz"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Tulx on 2007-04-20
Hi

I previously had dapper and by default it allowed only 60 Hz. With making a nice HOW-TO from these forums it allowed me also 90 Hz. (How-to was about enabling Nvidia drivers).

After using dapper for a while I had wanted to upgrade to newer version. Because I had not anything important on my dapper I decided to format it completely. I downloaded Feisty live from ubuntu homepage and installed it.

Now I have ran into a problem. My screen only allows 50 Hz after enabling Nvidia drivers from Restricted Drivers Manager. By default it was 60 Hz. (When I disable them I think it will be 60 Hz again but this is too less. When I change Hz to 57 or any other then it displays me extremely weird picture.)

Does anyone have a idea what do to or any useful HOW-TOs? Thank you.

-Tulx

---

### Post by NT4usB on 2007-04-20
what do you get when you run(in a terminal): ```
nvidia-settings
``` You should be able to change refresh there...

ed:found this thread, might be of interest. See post #9
[http://ubuntuforums.org/showthread.php?p=2494315#post2494315](http://ubuntuforums.org/showthread.php?p=2494315#post2494315)

---

### Post by Tulx on 2007-04-21
It worked! I changed my screen Hz from auto to 85 Hz. Now when I look to Preferences > Screen resolution then it is 112 Hz not 85 but it will work too. I had no idea that Feisty also has this kind of Nvidia configuration thing like XP has.

I was already subscribed to this thread. I think i will post this code there too. Maybe it helps.

Thank you - Tulx

---

