---
title: "&quot;Too many open files&quot; error preventing me from opening things"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by HelloGopher on 2008-01-07
Hello :) Often it seems that Ubuntu freezes up in a peculiar way: when I try to open music, the icons for the files just turn into something that looks like a page, the properties for any sort of document will list "unknown" as the type for anything (text, PDF, mp3, etc), when I try to open folders it will say "Sorry, can't display the contents of [Folder]", when I try to double click on shortcuts it will say "Too many files open", and I basically have to reboot before I can do anything again. 

It seems to occur at random. 

How do I fix this?

---

### Post by ghostdog74 on 2008-01-08
the next time you have such problems, see if you can find out anything by issuing the lsof command.

---

### Post by Yarrgovich on 2008-02-18
Any useful responses other than "use lsof" available?

Saying "use lsof" is meaningless. I try the command and get a list of semi-cryptic items that is too long to be fully displayed in the terminal window (many, probably most, are lost out the top).

Googling lsof provides nothing that I can make heads or tails of.
Man lsof is even more bothersome, considering most of the search results from Google return the content but without being limited to the terminal.

All of my searching for a solution to this problem points to the same (unanswered or otherwise useless) forum posts or talk about Confluence.

On a Confluence site, at [http://confluence.atlassian.com/display/DOC/Fix+'Too+many+open+files'+error+on+Linux+by+increasing+filehandles](http://confluence.atlassian.com/display/DOC/Fix+'Too+many+open+files'+error+on+Linux+by+increasing+filehandles)

It says to edit the sysctl.conf file, but when I try to save the file, it refuses to let me save it because of a lack of permissions. 

So... Any suggestions for people who are not Linux wizards? And no, "Google it" is not a valid response, considering I'VE BEEN ******* GOOGLING IT SINCE IT FIRST HAPPENED TO ME and it has returned nothing that I and my Windows-atrophied brain can make sense of.

---

### Post by erginemr on 2008-02-19
Try "**sudo lsof | less**" instead. :lolflag: No really, it gets rid of the permission erros and allows you to view the list of open files page by page. But it is not very helpful either considering that the list is huge.

Following tricks are the ones I can think of:

1. To apply 
> Run the command sysctl -a. If this is less than 200000, increase the number of file handles by editing /etc/sysctl.conf and changing the property fs.file-max to 200000. If there isn't a value set already for this property, you need to add the line fs.file-max=200000.
from the link you gave, you need to use sudo / gksudo to get root permissions. So;
```
gksudo gedit /etc/sysctl.conf
```
will allow you to edit the file. And instead of using "**sysctl -a**", using "**sysctl -a | grep fs.file-max**" will be a better alternative in that it will just give you the information you require. 

**However, I still recommend you to try the 3rd item below, before messing with system variables.**

2. It can be a missing or non-working memory swap system. Post the output of
```
sudo fdisk -l
```
which will list the hard drives in use and also the size and other details of the swap file. Don't worry, it will not format your hard drive.

3. **Last but not least, if this problem occurs only when you try to view a directory full of music files:**

Nautilus (Gnome's file manager) lets the user preview all music files when s/he hovers the mouse on it. However, this may cause a "too many open files" error when the directory has hundreds of music files. 

To disable text, music and image previewing (which is both useless and system resource hog in my opinion), you should enter the setting in the Nautilus menu and disable all previews as illustrated in the attachment below:

---

### Post by Yarrgovich on 2008-02-19
> **erginemr said:**
> 3. **Last but not least, if this problem occurs only when you try to view a directory full of music files:**

...

To disable ... image previewing

I do a lot of amateur photography and video editing, and the folders I use for these contain some 27,000 items. Such an issue never came up under Windows, so it hadn't even dawned on me that this may be an issue on Linux.

I'll try disabling the previews before doing anything else, and hopefully the issue will be resolved.

Thank you very much for your info! None of my searches had said anything about previews.

---

