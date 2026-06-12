---
title: "Add User to which Groups"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Brad_au on 2008-01-17
Can anyone point me to a concise summary of what access to each (secondary) user group allows?

I'm trying to setup a locked down user account which allows internet browsing over a lan router but nothing else. Any thoughts as to the minimum groups that this would require?

Many thanks,

B

---

### Post by Nano Geek on 2008-01-17
In **Users and Groups**, click on the user you want to edit, click on **Properties**, and click on **User Privileges**. 

The main thing you want to uncheck I believe is **Administer the System**. 
After that just uncheck what ever you don't want them doing.

---

### Post by Brad_au on 2008-01-18
Thanks for the help.

I forgot to mention I'm running kubuntu. In System Settings, I can find User Management, but I can't find any properties for users. If I click Modify it brings up a screen where you can set the secondary groups, but no Privileges. This is what I want to set.

Apologies, if I'm missing something obvious.

---

### Post by Nano Geek on 2008-01-18
Oh, sorry. I assumed that you are using GNOME. 

Give me a little bit to see how you do it in KDE.

---

### Post by Nano Geek on 2008-01-19
Looking through it, I'd say you would want to remove them from the **admin** and the **root** groups. 

I think that will keep them from doing any administrative stuff. But it will still let them change the wallpaper and browse the web.

---

