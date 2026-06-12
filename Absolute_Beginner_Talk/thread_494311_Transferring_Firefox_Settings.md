---
title: "Transferring Firefox Settings?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Kilrain on 2007-07-06
I'm going to be getting a new computer soon which I'll be installing ubuntu on.  I have an external hard drive with which to transfer my files, and was wondering if there was a way to transfer my firefox settings over as well (such as bookmarks, saved passwords, add-ons, etc.).  Thanks.

---

### Post by tartarian on 2007-07-06
I'm not sure about the add-ons 
but you should be able to transfer your bookmarks
There's a folder in application data on windows which stores the URL's of your bookmarks
The same applies to firefox on linux, except i think its in the home folder something like .firefox
I presume that if you copied and pasted the folder contents then your bookmarks would show up
I've never actually tried that though ;)

---

### Post by robertc36 on 2007-07-06
Take a look at this thread
[http://groups.google.com/group/Firefox-Users/browse_thread/thread/a85e568feba76f28](http://groups.google.com/group/Firefox-Users/browse_thread/thread/a85e568feba76f28)

ps i just googled it

---

### Post by por100pre1 on 2007-07-06
I use Grsync to backup my /home/user/ folder easily.

---

### Post by Aelfric5578 on 2007-07-06
> **tartarian said:**
> I'm not sure about the add-ons 
but you should be able to transfer your bookmarks
There's a folder in application data on windows which stores the URL's of your bookmarks
The same applies to firefox on linux, except i think its in the home folder something like .firefox
I presume that if you copied and pasted the folder contents then your bookmarks would show up
I've never actually tried that though ;)

You can in fact copy all of your Firefox settings by copying the contents of one profile folder into another.

In Windows, the default location for your Firefox profile is: C:\Documents and Settings\[User Name]\Application Data\Mozilla\Firefox\Profiles\

In Ubuntu, the default location is: ~/.mozilla/firefox/

There will be one or more folders for each profile profiles.  Copy the contents of whichever profile you want to preserve from one machine to the other.  This will preserve bookmarks, extensions, customizations, etc.  When you first start Firefox after doing this, it will check the newly installed extensions for compatibility.  Keep in mind that this will completely replace your profile on the other machine.

Alternatively, you can examie your profile and see exactly what you want to preserve.  Then you can try to merge the old with the new.  I am not sure if there is any automated way to merge two profiles, but it should be doable with a bit of selective copying and pasting.

---

