---
title: "Firefox font issues"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Kl0wN on 2008-04-18
I have searched and seen nothing similar to my problem.. so here it goes:

I was messing around in the themes, clicked on the Inverted Large Print theme, and noticed it had a font to go along with it, so I thought what the heck, and clicked apply.

Everything was huge, so I switched to a different theme, and I got the fonts back to normal, but I still had an issue with firefox. 

I have taken a look at the Content in the Firefox options menu, but it doesn't seem to fix anything. Here's a ss:


[http://i30.tinypic.com/2mxo1h2.png](http://i30.tinypic.com/2mxo1h2.png)

If anyone could help, it would be extremely appreciated, thanks.

---

### Post by Vadi on 2008-04-18
Tried pressing Ctrl and the plus key (Ctrl + +)?

---

### Post by Kl0wN on 2008-04-18
Yes sir I have, but the URL and bookmark toolbar is still extra small, Plus, everytime I restart Firefox, it would still be the same (for ctrl ++)

---

### Post by oldsoulsong on 2008-04-18
If you just prees control (ctrl) and zero, it will reset your font size to the default setting

---

### Post by Kl0wN on 2008-04-18
That's related to ctrl ++, which doesn't work. :( 

I tried.

---

### Post by y-lee on 2008-04-18
Does this change effect all Firefox profiles if you use more than one?

If you don't use multiple profiles try creating a new one by using the below command in a terminal:

```
firefox -P
```

If this change does not effect the new profile something is wrong with your current profile. Post back and let us know.

---

### Post by Kl0wN on 2008-04-18
Hello,  y-lee

This did not fix it. It opened a new window and is still the same size.

I believe it is a theme issue, and has nothing to do with firefox.. I haven't checked any other applications.

---

### Post by y-lee on 2008-04-18
> **Kl0wN said:**
> Hello,  y-lee

This did not fix it. It opened a new window and is still the same size.

I believe it is a theme issue, and has nothing to do with firefox.. I haven't checked any other applications.

Check other applications so we know whether this is a firefox issue or a gnome (??) theme issue. I'm assuming you use gnome and not KDE or something else. If you don't use gnome let us know :)

---

### Post by quirks on 2008-04-18
It may sound silly, but have you tried restarting X (i.e., logout and login again)? Sometimes solutions are too simple to think of.

quirks

---

### Post by bmac on 2008-04-18
I had the same problem when running a non-default firefox theme. I removed the non-default firefox theme then reinstalled it. Was then able to change fonts in my content - advanced page.

---

### Post by Kl0wN on 2008-04-18
Hello,

Yes, I have logged out and then back in. This does not fix it.

Also, y-lee, this is a theme issue. 

I made another user account, and the fonts look fine on that.. I saved the default theme, where does it save to, so I can load it on here?

EDIT -

I have fixed this problem.. It was a theme issue indeed, I set the resolution dots per inch to a number higher then what it should be. The normal is 96. THank you guys for your help.. and if you don't mind, could you answer another question for me?

I have went to the last tab of the theme options, and there is a None, Normal, and Extra. I get a Composite extension is not available when I change this. How do I fix it?

---

### Post by Vadi on 2008-04-18
Another question for another thread. You're looking for "how to enable compiz" - make a thread, post what video card you got in there, and give us a link.

---

