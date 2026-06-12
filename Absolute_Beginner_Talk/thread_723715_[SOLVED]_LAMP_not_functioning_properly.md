---
title: "[SOLVED] LAMP not functioning properly"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-13
I've just installed LAMP Server right out of synaptic so i know everything is set up right. But made a file called "index.php" and what's inside is

```

<?php
phpinfo();
?>

```

i was just doing that to figure out my php info and to test to make sure everything was working right
but when i go to
[http://localhost/](http://localhost/)
a box pops up asking me if i want to download something
you can see a screen shot below...
how come it's not just going to the page and showing me my php info...

---

### Post by louieb on 2008-03-13
Weird its like Firefox does not know what type of file it has. why don't you download it and see what the name is and whats in it?

---

### Post by The Titan on 2008-03-13
i think PHP isn't working properly, so it is trying to download the file it doesn't recognize

---

### Post by Oldsoldier2003 on 2008-03-13
> **The Titan said:**
> i think PHP isn't working properly, so it is trying to download the file it doesn't recognize

It is an Apache configuration issue. you need to tel apache to parse php files instead of serving them as text/html.

---

### Post by Oldsoldier2003 on 2008-03-13
> **RadiationHazard said:**
> I've just installed LAMP Server right out of synaptic so i know everything is set up right. But made a file called "index.php" and what's inside is

```

<?php
phpinfo();
?>

```

i was just doing that to figure out my php info and to test to make sure everything was working right
but when i go to
[http://localhost/](http://localhost/)
a box pops up asking me if i want to download something
you can see a screen shot below...
how come it's not just going to the page and showing me my php info...
Apache is improperly configured, see these links for more info on how to make it work.
[http://ubuntuforums.org/showthread.php?t=246371](http://ubuntuforums.org/showthread.php?t=246371)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by kellemes on 2008-03-14
Also don't forget to empty the cache of Firefox.

---

### Post by RadiationHazard on 2008-03-14
thanks guys!
i just reloaded apatche =]

---

