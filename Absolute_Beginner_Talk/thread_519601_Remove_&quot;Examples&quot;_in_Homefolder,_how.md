---
title: "Remove &quot;Examples&quot; in Homefolder, how?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Johnson on 2007-08-07
I do wonder how I can remove "Examples" in the Homefolder, I try but it won't do it.
I do not want to keep it, you know.

---

### Post by PartisanEntity on 2007-08-07
There is a way through the terminal, but for newbies I think the visual way is easier?

Press ALT+F2 and type ```
gksudo nautilus
```

This will open up the nautilus file browser with admin/root priviliges, you can then navigate to your home folder the delete the examples.

---

### Post by Johnson on 2007-08-07
> **PartisanEntity said:**
> There is a way through the terminal, but for newbies I think the visual way is easier?

Press ALT+F2 and type ```
gksudo nautilus
```

This will open up the nautilus file browser with admin/root priviliges, you can then navigate to your home folder the delete the examples.

Did that now, did not see the folder "Examples" and I also notice I saw 6.3GB free of space in that root/home folder I was in, and my home folder is actually over 120GB free of space.

They are two different part, what I do?

---

### Post by Wiebelhaus on 2007-08-07
type

> /home/username

your going to have to guide yourself a little bit here man.

---

### Post by doomster on 2007-08-07
i wouldnt use the graphic way to delete examples. its even more dangerous to do so than copy paste 
to do it through the console do  
```
 sudo rm ~/Examples
```

---

### Post by Johnson on 2007-08-07
> **sx66gns said:**
> type



your going to have to guide yourself a little bit here man.

Sorry I'm new, but I made it. Thanks dude. :)

---

### Post by topbot on 2007-08-07
actually Examples is a package, called example-content. So you can sudo apt-get remove example-content.

---

### Post by doomster on 2007-08-07
plz edit yor first post and rename it's title by adding [Solved] at the beginning :)

---

### Post by Johnson on 2007-08-07
> **topbot said:**
> actually Examples is a package, called example-content. So you can sudo apt-get remove example-content.

I did both things, thanks again.

---

### Post by stchman on 2007-08-07
> **Johnson said:**
> I do wonder how I can remove "Examples" in the Homefolder, I try but it won't do it.
I do not want to keep it, you know.

That is because it is owned by root.  To remove type the following:

sudo rm -r -f ~/Examples

It does not take up much room and has some cool icons and pics.

---

