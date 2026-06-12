---
title: "How to change default apps?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-15
I'm sure this has been asked already, but I've searched and searched but can't find the answer I'm looking for.  How do I change the default application that opens for file types?  I'm trying to have all my audio files open with Amarok.

---

### Post by trak87 on 2007-07-15
Using Nautilus, right click on the audio file (you want Amarok to open) and select the Properties option. Then look for the "Open With" tab. Make a selection there.

---

### Post by dmorand on 2007-07-16
I've done that, but it only opens it for that single instance.  The problem I'm having is that the streaming music I open from Firefox won't open in Amarok.  I don't see that program listed in there.

---

### Post by davidjmayo on 2007-07-16
In Firefox look at

Edit==>prefernces
then content tab and the files types (config how FF manages file types. click manage and choose the file type and app. You may need to add it yourself

---

### Post by dmorand on 2007-07-16
Cool, I should have looked there to begin with.  

Where would my Amarok install be located?  Sorry, I'm such a newbie.  I'm going to get a good handle on this really soon though.....I hope.

---

### Post by 56seeker on 2007-07-16
I think you can find where it's installed with the "which" command

"which amarok"

---

### Post by davidjmayo on 2007-07-16
> Where would my Amarok install be located

All over the place. Look at this 

```
locate amarok
```

---

### Post by davidjmayo on 2007-07-16
sorry i was wrong

should be

/usr/bin/amarok

do a search for  files *amarok* and look in root not your home directory

---

### Post by dmorand on 2007-07-16
> **davidjmayo said:**
> sorry i was wrong

should be

/usr/bin/amarok

do a search for  files *amarok* and look in root not your home directory

Cool.  Thanks!!

---

