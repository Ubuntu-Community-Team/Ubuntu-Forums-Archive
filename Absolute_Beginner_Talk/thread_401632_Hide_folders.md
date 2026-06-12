---
title: "Hide folders?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-04-04
Is there a way to make folders that I don't want to see in my home folder (but yet have to be there) hidden? Like when you click "show hidden" then they would appear.

---

### Post by drs305 on 2007-04-04
If you preface the filename with a period, it becomes hidden  (e.g. mystuff >>  .mystuff).  In Nautilus, these files are hidden by default but you have the option of viewing them with View, Hidden Files. However, if they HAVE to be there, you may not be allowed to change the name for them to still work with whatever app is requiring them...

---

### Post by Ripfox on 2007-04-04
Cool works good, is there anyway to get rid of the "Desktop" folder in the home folder, as I do not use it, or is this part of the way Nautilus handles the desktop?

---

### Post by h0bbe on 2007-05-06
Is it possible to hide folders (and files) without changing their name to .mystuff using a period?

---

### Post by Ripfox on 2007-05-06
Not that I have found

---

### Post by sabrewolf2006 on 2007-05-06
> **ripfox said:**
> Cool works good, is there anyway to get rid of the "Desktop" folder in the home folder, as I do not use it, or is this part of the way Nautilus handles the desktop?

Yes there is a way, if you have gconf-editor installed you can navigate your way to /apps/nautilus/preferences/ and there is a key called 'desktop is home dir' set it to true and voila! No more desktop folder :) (well, ok, you'll need to delete the Desktop folder.. but your desktop will now be your home directory rather than an extra folder)

Hope this helps

---

### Post by richard.stallman on 2008-02-21
> **sabrewolf2006 said:**
> Yes there is a way, if you have gconf-editor installed you can navigate your way to /apps/nautilus/preferences/ and there is a key called 'desktop is home dir' set it to true and voila! No more desktop folder :) (well, ok, you'll need to delete the Desktop folder.. but your desktop will now be your home directory rather than an extra folder)

Hope this helps

good post!!! keep it up

---

### Post by ahawesome on 2008-02-27
If you want to hide files and folders without renaming them:

[LIST=1]
[*]Create a file named ".hidden" (without the quotes, of course) in the directory containing the files/folders you want to hide
[*]If you can't see the file, press Control-H or go to View->Show Hidden Files
[*]Open up the file in the text editor (I had to do this as root for some reason, you may not need to)
[*]Add the name of a file or folder you want to hide
[*]Save the file, exit the text editor, and open or refresh Nautilus (F5)
[*]You should not be able to see the file or folder
[/LIST]

Hope this helps!

---

### Post by Ripfox on 2008-02-28
Very interesting.

---

### Post by seventhc on 2008-02-28
If your desktop is the home dir, wouldn't that look messy ??? Or am I missing or misunderstanding something?

---

### Post by h0bbe on 2008-07-23
> **ahawesome said:**
> If you want to hide files and folders without renaming them:

[LIST=1]
[*]Create a file named ".hidden" (without the quotes, of course) in the directory containing the files/folders you want to hide
[*]If you can't see the file, press Control-H or go to View->Show Hidden Files
[*]Open up the file in the text editor (I had to do this as root for some reason, you may not need to)
[*]Add the name of a file or folder you want to hide
[*]Save the file, exit the text editor, and open or refresh Nautilus (F5)
[*]You should not be able to see the file or folder
[/LIST]

Hope this helps!

Does this work in xubuntu aswell?

---

### Post by ahawesome on 2008-07-23
Actually, I'm not sure. Xubuntu uses a different file manager (Thunar instead of Nautilus). You might need to try it out to see. I'll try to find more info.

---

### Post by ahawesome on 2008-07-23
According to [this]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/110521"), the technique I mentioned doesn't work in Thunar. The bug states that it didn't work in Feisty or Hardy. I guess this means that it is safe to assume that it doesn't work in Gutsy either. In short, it won't work in Xubuntu. Maybe you should try getting Nautilus from the repos (sudo apt-get install nautilus, I bet).

---

### Post by h0bbe on 2008-07-24
Thanks ahawesome!!

---

### Post by Ripfox on 2008-07-24
But what if I don't want my desktop to be home

---

