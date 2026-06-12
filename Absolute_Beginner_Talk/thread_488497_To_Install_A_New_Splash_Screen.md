---
title: "To Install A New Splash Screen"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by tcoffeep on 2007-06-30
Hey all.

I've been trying to install new splash screen off of gnome-look.org, and it states that in order to run a specific screen, I need to edit the menu.lst :

> ind the paragraph about your current kernel version, and add the string

    vga=791

at the end of the kernel section, without modifying pre-existing values. 

Where exactly do I add this? I find the entire file confusing :S

---

### Post by toasterofirony on 2007-06-30
I'm not sure I can answer your question, but I could suggest something that might make your life easier for rejigging your splash screen in future: 

[startup manager]("http://www.gnomefiles.org/app.php?soft_id=2051")

---

### Post by tcoffeep on 2007-06-30
I followed your advice, and dl'ed the .deb package.

Upon attempting to install, what comes up is this :

> Could not download all required file

Please check your internet connection or installation medium.

V Details
--------------
Failed to lock /var/cache/apt/archives/lock

What's strange is I just finished installing frostwire using the deb installer, and I'm currently using the internet. :S Confusing.

---

### Post by tcoffeep on 2007-06-30
Never mind, I just needed to install imagemagick.

:) Thanks for your help (thumbs up)

---

