---
title: "Control  + Click for Right Click"
date: 2011-12-15
forum: Apple Hardware Users
---

### Post by svtguy88 on 2011-12-15
Alright, I did a quick search for trying to fix this, but didn't come up with anything too promising.  One solution involved a hack-ish script, and the other a config file that doesn't exist on my system, so I thought I'd post to see if there's a more modern way to fix this.

I want to enable the right click context menu the way that OS X does - that being ctrl + left click.  I'm not even using a Mac, but I am using an Apple Pro keyboard/mouse (Really not sure why...I just love the feel of it).

I thought ctrl + click was default for the Macintosh keyboard layout.  I could swear I could control click the context menu when I had Debian up and running on the Powermac G4 that this keyboard/mouse set came from.

I'll keep searching, but does anyone have a quick fix?

---

### Post by rsavage on 2011-12-15
[http://askubuntu.com/questions/28667/how-do-i-do-right-clicks-on-ibook-g4](http://askubuntu.com/questions/28667/how-do-i-do-right-clicks-on-ibook-g4)
 
More info in Trackpad section here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by svtguy88 on 2011-12-15
lol.  Well, I feel dumb.  It's always nice when there's an obvious solution.

Thanks for the reply.  I used the command

```
sudo mouseemu -middle 0 0 -right 29 272
```

to configure mouseemu and it works well.

---

