---
title: "How to uninstall?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by kcsx on 2008-03-29
Total newb question: How do I uninstall a program I no longer want? I installed Azureus twice and I need to get rid of the first installation because I had installed it wrong the first time. When I installed Azureus again I naturally assumed it would overwrite the older version but I guess not.

So I need to know how to uninstall if someone could give me directions to do it from the terminal or from a command menu that would be awesome.

Oh and as a side note, where does Ubuntu store all the installed programs? Is there a directory for them similar to "Program Files" in Windows? :-k

---

### Post by DBrocks on 2008-03-29
Nice avatar. Try: 
```
sudo apt-remove [package name]
```
If that doesn't work, try
sudo apt-get remove [package name]

---

### Post by saj0577 on 2008-03-29
> How do I uninstall a program I no longer want?
```
sudo apt-get remove [package name]
```

> Oh and as a side note, where does Ubuntu store all the installed programs? Is there a directory for them similar to "Program Files" in Windows?

I believe it is in /etc but dont quote me on that not totally sure myself.


Saj

---

### Post by scragar on 2008-03-29
binaries are in **/usr/bin** or **/usr/sbin**(for super user programs).

libaries are stored in /lib/ or(more commonly) /usr/lib

/usr/share is where a lot of your programs will go, however most programs pick their own install location, so it may not be there,

---

### Post by forrestcupp on 2008-03-29
How did you install the first instance of Azureus?  That will determine how you uninstall it.  If you installed it with apt-get or Synaptic, then the **sudo apt-get remove azureus** or whatever the correct package name is, will do it.

If you compiled it from source, then you have to go by that particular program's instructions on how to uninstall it.

Just out of curiosity, if you don't know where they're located, how do you know they are both on there?  One thing you could do is open Synaptic and do a search for Azureus.  You can uninstall the one you want from Synaptic, too.

---

### Post by kcsx on 2008-03-29
Ok.... now I have a different problem. I uninstalled the new installation of Azureus (oops) but know when I try again it won't remove the old version of Azureus (the one that doesn't work) because it says it can't find the package.:confused:

Whassa goin' on here?

---

### Post by kcsx on 2008-03-29
I can see Azureus listed twice in the Applications>Internet drop down menu. I'm trying the Synaptic thing right now.

---

### Post by kcsx on 2008-03-29
Ok... I used Synaptic and uninstalled it but Azureus is STILL listed in the drop down menu.

---

### Post by scragar on 2008-03-29
if it's in the menu list twice then use the edit menu option to see both properties, and not the path to both version. Post the one that's not:
/usr/bin/azureus
here

---

### Post by spiderbatdad on 2008-03-29
try this ```
sudo dpkg --purge azureus
```

---

### Post by Victormd on 2008-03-29
Once you've done all of the above, do 
> sudo apt-get autoremove
this will remove any libs or packages that are no longer needed/used...

---

### Post by kcsx on 2008-03-29
> **scragar said:**
> if it's in the menu list twice then use the edit menu option to see both properties, and not the path to both version. Post the one that's not:
/usr/bin/azureus
here


Edit Menu option? You might have to explain that one a bit more...

Oh and apparently Azureus has been completely removed from my system but it's still listed there... In the menu... TAUNTING me...

---

### Post by scragar on 2008-03-29
right click on the buttons for the menu(Applications, Places or System) and pick edit menu, then hit internet on the left side, and right click azereus, hit properties(top option) post the path it lists here(or both paths)

---

### Post by kcsx on 2008-03-29
> **scragar said:**
> right click on the buttons for the menu(Applications, Places or System) and pick edit menu, then hit internet on the left side, and right click azereus, hit properties(top option) post the path it lists here(or both paths)

That did it. Thank You! You're awesome!

---

### Post by forrestcupp on 2008-03-30
I'd say that more than likely, it's a problem with the program making 2 menu entries, rather than that it installed itself twice.  But I ask you again, how did you install the program?  That's important.

---

