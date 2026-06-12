---
title: "Adding programs to menu in Gnome"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by NegativeSpace on 2006-10-29
Hi,

I have a file, *idea.sh*, which executes a program.

I tried to add a shortcut to this in the *Programming* menu using *Menu Layout*.

First of all I added a new item and simply browsed to the *idea.sh*, giving me this command:

```
/usr/bin/idea\-\5\7\8\4/bin/idea\.sh
```

However, this did nothing. I then ticked the *Run Command in Terminal* box and nothing.

Next, I tried:

```
cd /usr/bin/idea-5784/bin; ./idea.sh
```

Again, I ticked the *Run Command in Terminal* box. I thought this would have worked as, if I enter this exact line into a terminal, it runs. However, nothing.

How can I get the program to run from a menu shortcut?

Regards.

---

### Post by blendmaster on 2006-10-29
Right click on your Applications drop-down, and click edit menus.

click on the programming menu, and click new item.

You can edit the information from there.

This is one Edgy, but on Dapper, instead of clicking new item, you'll go to file first, and then new item.

Hope that helps!

Edit: Apparently, you already have this down, I would think that you would need to link this to the program that you're trying to run directly, but I haven't worked with .sh programs very much...

---

### Post by NegativeSpace on 2006-10-29
Hi blendmaster,

Thanks for your help, but this brings up the same *Menu Layout* program I tried to add it with before, which doesn't seem to work for me.

I am also on Edgy, if that makes a difference.

---

### Post by blendmaster on 2006-10-29
Have you tried System >> Preferences >> Menu Layout?

It does the same thing, but I guess it's worth a shot.

Sorry I can't help more...

---

