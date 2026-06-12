---
title: "How to use the same configuration in Windows and Ubuntu at the same time?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by tico on 2007-06-17
Hi,

I have many programs that I use in WinXP that I'd like to use in Ubuntu. They are already configured in Windows XP and the configuration files are in 
"Documents and Settings"\MYOWNUSER". This is the case of Firefox and Thunderbird. How could I use  in Ubuntu the same physical config files that I use in WinXP  (these in "Documents and Settings")? How could I use in Ubuntu the same INBOX/OUTBOX that I use in WinXP?

&#1616;&#1616;&#1616;&#1616;

---

### Post by Bluecircle on 2007-06-17
For Firefox and Thunderbird, you can simply copy the profiles folder under application data, then move it to the profiles folder in Ubuntu. The new profiles folders are:

Firefox:
/home/user/.mozilla/firefox/

Thunderbird:
/home/user/.mozilla-thunderbird/

Replace "user" with your user name. So simply copy the profile folders over and you will have all your mail, contacts, plugins, bookmarks, preferences, etc.

Edit: You will have to make sure "Show hidden files" is enabled so you can see the folders.

---

### Post by tico on 2007-06-17
Thanks, Bluecircle,

But I wouldn't like to copy the profile into Ubuntu. I'd like to use in Ubuntu the same files that are in "Documents and Settings (Windows XP). I probably need to say to Firefox, Thunderbird, Openoffice to use the files that are in "Documents and Settings). How could I do this?

Thanks.

---

### Post by dmfield on 2007-06-18
is your windows volume, FAT32, FAT16 or NTFS?

Can you see your existing windows system when you are using Ubuntu


It may be possible to do what you wish to do with some clever mounting of drives.. however in order to do this, you obviously need to be able to already "see" your Windows drives in Ubuntu.

As you may have noted in the previous reply, although the apps like Firefox, and Thunderbird look the same and perform the same tasks on Windows and Linux, they do in fact operate in slightly different ways "under the hood"

Hence the fiddling..

If its items like book marks in Firefox, which you wish to be the same, download Foxmarks from mozilla.com 

Also with your email, if your provider allows you to use imap instead of POP, any mails sent, or received when you use Thunderbird, will be identical in both systems...

Let me know what you wish to share, have similar between systems, and I may be able to help you with a different way...

---

### Post by vanadium on 2007-06-18
Links in Linux are extremely powerful and allow you to organise your system the way you want. Indeed, the approach is to create a link to the files in the Windows partition.
You can easily create a link using Nautilus.
* navigate to where the folder you want to link to is located.
* Right-click that folder, choose "Make link"
* Move the newly created link (just a file, called "Link to ...") to the new location in your file system where you want to use it.
* If you want the link to replace an existing folder (which is what you want for your goal), rename the existing folder (you could also delete it, but it is safer to rename it first, then delete it afterwards if all works well).
* Then rename the link to the original name of the folder you just renamed.

---

