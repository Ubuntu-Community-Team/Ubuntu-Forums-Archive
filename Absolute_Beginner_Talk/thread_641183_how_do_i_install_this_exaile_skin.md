---
title: "how do i install this exaile skin?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-12-15
hey guys.  im using exaile as my default player, and while its awesome, i dont really like the default look of it.  so i googled some themes and found one thats on the official exaile website ([http://www.exaile.org/themes](http://www.exaile.org/themes))

the instructions say "To install a theme, simply save it as ~/.exaile/exaile.extheme and restart Exaile".  what does this mean?  i went to my file system and looked up the folder .exaile, and took the theme, renamed it, and tried copying it but it wouldn't let me.  it said i didn't have enough permissions or something.

can someone help me please???  thanks!

---

### Post by siciliancasanova on 2007-12-15
Looks like you need to be root, type ```
sudo nautilus
```

then make your changes in that browser.

---

### Post by Jimmey on 2007-12-15
You **don't** need to be root. In your /home area press CTRL + H with nautilus. That will show the hidden folders. Look for .exaile.

On a side note, you shouldn't run graphical apps with sudo.

To run a graphical application as root, use the command 
```
gksudo appname
```

---

### Post by siciliancasanova on 2007-12-15
I don't think you would get any side effects from using sudo nautilus over gksudo nautilus.

Maybe on an installed application but not the browser.  I have never seen any instances of issues of browsing nautilus as sudo over gksudo being worse.

---

### Post by Jimmey on 2007-12-18
I'm just going from what's written [here]("http://www.psychocats.net/ubuntu/graphicalsudo"). Gksudo is a good habbit to learn.

---

