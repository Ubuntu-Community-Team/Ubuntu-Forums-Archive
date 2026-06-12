---
title: "Strange Firefox Behaviour"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-11
Could someone please explain to me why some scrips work in UserChrome, User JS, etc. while others don't or only partially?

They all work fine in Windosen't...

Thanks for any insight,

Jon

---

### Post by Seisen on 2007-05-11
What scripts are you talking about? Some of them might only we for just Windows.

---

### Post by Romin-1 on 2007-05-11
Here's a sample scrip that works in FF on Windoze but not in Ubuntu:
> /* Remove Bookmark Toolbar folder from the bookmarks menu */
menu[label="Bookmarks Toolbar Folder"] { display: none !important; }

There are a couple others as well.

What I can't figure is why some work and some don't.

Oh well, back to the scripting board,,,

Jon

---

### Post by jfinkels on 2007-05-11
> **Romin-1 said:**
> Here's a sample scrip that works in FF on Windoze but not in Ubuntu:


There are a couple others as well.

What I can't figure is why some work and some don't.

Oh well, back to the scripting board,,,

Jon

That's not a script, that's a style. Make sure it's in userChrome.css and not in the javascript file, for one!

Second, that may work with an older version of firefox...I don't know, but maybe they use a different system for naming toolbars or something. Or maybe you renamed your "Bookmarks Toolbar Folder" to something else.

You could just right-click on the toolbar, click "Customize..." and remove whatever you want that way.

Other than that, if you have a specific problem, we could help you with that if you can describe it or show us code.

---

### Post by Romin-1 on 2007-05-11
Thanks for the reply.

I have it in the proper place and the same version of FF in Windows and Dapper.

I have never used the bookmark toolbar. It is completely empty and hasn't been re-named.

What that style is supposed to do is remove the folder from the sidebar as right click-delete does not work.

Anyhoo,

Have a good one,

Jon

---

