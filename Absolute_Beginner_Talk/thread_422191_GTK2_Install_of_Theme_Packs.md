---
title: "GTK2 Install of Theme Packs"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-04-24
Heya,

I'm trying to figure out where I install the Themes I download.

From what I understand they go into the ~/.themes folder.  Now from what I understand the . means it's a hidden folder. So either I'm doing this wrong, or I need to unhide this particular folder.

Just in case its relevant here is the theme location I'm trying to install:

[http://www.gnome-look.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697](http://www.gnome-look.org/content/show.php/LiNsta+%28LiNsta+is+Not+Vista+%3B-%29?content=42697)

Now, I've installed all of the programs I need to do it (I've already changed quite a bit manually messing about), so I just basically need to know where to unpack the Themes that I do download, so that I can install them via the Theme Manager or Art Manager.

thanks,

Seth

---

### Post by johnny4north on 2007-04-24
my folder is here home/johnny/.themes.  its hidden so you need to go home/yourname with file browser, then click view and view hidden files..:)  are you sure it goes there?  i found the other default themes here \usr\share\themes  good luck

---

### Post by Matt Yun on 2007-04-24
You actually don't need to unpack the theme file; Theme Manager will install directly from the *.tar.gz file, provided that the developer packed it properly.

However, if you have to manually unpack the theme file, do:

tar xvzf theme.tar.gz -C ~/.themes

---

### Post by johnny4north on 2007-04-25
thanks i was going to upgrade my theme tonite. :guitar:

---

### Post by Sethalos on 2007-04-25
Ok, so yeah, I think I was putting it into the wrong spot, it didn't work in the ~/.themes folder.  However, when I try to place it into the /user/share/themes folder, I get a permissions error.

So, obviously I'm missing something simple, but I'm pretty sure I have to enter ROOT to do this, so how do I do that?

Thanks.

Seth

---

