---
title: "[SOLVED] 'BASIC' error in OpenOffice.org"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Gwasanaethau on 2007-10-26
Hi all,

Whenever I open a saved spreadsheet in OpenOffice or I try to save a brand new spreadsheet, a couple of dialogue boxes appear with error messages in them:
> Error loading BASIC of document
file:///home/mark/.openoffice.org2/user/basic/dialog.xlc/:
General Error.
General input/output error
and
> Error loading BASIC of document
file:///home/mark/.openoffice.org2/user/basic/dialog.xli/:
General Error.
General input/output error
[SIZE="1"](the two errors differ on the file name extension.)[/SIZE]

Does anyone know what's causing the error and whether it's terminal? I might have caused it by trying to backup and restore OpenOffice's preferences files in my home directory, if that's any help.

P.S. I tried 'sudo apt-get install openoffice.org-common openoffice.org-core openoffice.org --reinstall', but it didn't do anything.

EDIT: forgot to mention that I'm still using Feisty Fawn.

---

### Post by forestpixie on 2007-10-26
it appears that you need to rename a couple of files to start with before you delete them - I found what might help you here

[http://www.linuxquestions.org/questions/linux-software-2/openoffice-error-loading-basic-of-document-415702/](http://www.linuxquestions.org/questions/linux-software-2/openoffice-error-loading-basic-of-document-415702/)

which refers to this one - in particular the last post 
[http://www.8daysaweek.co.uk/forums/viewtopic.php?p=196](http://www.8daysaweek.co.uk/forums/viewtopic.php?p=196)

see if that helps

---

### Post by Gwasanaethau on 2007-10-26
Thanks - I gave those things a try. Unfortunately, they only generated additional errors in 'script.xlc' and 'script.xlb'. However, I don't seem to have 'dialog.xlc' or 'dialog.xli' at all, could this be the problem?

---

### Post by forestpixie on 2007-10-26
I don't know tbh - found those on a google search - have a look at the openoffice forums - they've helped me in the past

---

### Post by Gwasanaethau on 2007-10-26
Okie dokie, will do. Thanks for those suggestions anyway - they were certainly worth trying in any case.

---

### Post by Gwasanaethau on 2007-10-26
OK, fixed. Using the OpenOffice forums like forestpixie suggested, I found [this post]("http://www.oooforum.org/forum/viewtopic.phtml?t=64160"), which in turn links to the [OpenOffice handbook]("http://documentation.openoffice.org./manuals/OOo2.x/user_guide2_draft.pdf") (this is quite large). On page 455 (page 489 in evince) it details what needs to be done with a general error, specifically:
[LIST]
[*]Close any OpenOffice instances that are running,
[*]Go to '<where_OOo_is_installed>/presets/basic/'
[*]Copy 'script.xlc' and 'dialog.xlc' to '$HOME/.openoffice.org2/user/basic'
[*]Go to '<where_OOo_is_installed>/presets/basic/Standard'
[*]Copy 'script.xlb' and 'dialog.xlb' to '$HOME/.openoffice.org2/user/basic/Standard'
[/LIST]

In my case, I used the terminal and did:
```
cd /usr/lib/openoffice/presets/basic
cp dialog.xlc ~/.openoffice.org2/user/basic
cd Standard
cp dialog.xlb ~/.openoffice.org2/user/basic/Standard
```
This solved the problem! Yey! :)

---

### Post by forestpixie on 2007-10-26
glad to hear it

---

### Post by sd.chen on 2007-11-05
Works for me. Thanks for posting solution!

---

### Post by areayetee on 2008-01-31
wow simple and easy, that fixed me up real quick - you rock!:guitar:

---

### Post by zhaoc1 on 2008-02-12
Thanks a lot!~
:lolflag::lolflag::lolflag:

---

### Post by Gwasanaethau on 2008-02-16
No prob at all! Glad it helped you all out!

---

### Post by bmccorm2 on 2008-04-20
I had the same problem and this worked beautifully :)

Thanks again!

> **Gwasanaethau said:**
> OK, fixed. Using the OpenOffice forums like forestpixie suggested, I found [this post]("http://www.oooforum.org/forum/viewtopic.phtml?t=64160"), which in turn links to the [OpenOffice handbook]("http://documentation.openoffice.org./manuals/OOo2.x/user_guide2_draft.pdf") (this is quite large). On page 455 (page 489 in evince) it details what needs to be done with a general error, specifically:
[LIST]
[*]Close any OpenOffice instances that are running,
[*]Go to '<where_OOo_is_installed>/presets/basic/'
[*]Copy 'script.xlc' and 'dialog.xlc' to '$HOME/.openoffice.org2/user/basic'
[*]Go to '<where_OOo_is_installed>/presets/basic/Standard'
[*]Copy 'script.xlb' and 'dialog.xlb' to '$HOME/.openoffice.org2/user/basic/Standard'
[/LIST]

In my case, I used the terminal and did:
```
cd /usr/lib/openoffice/presets/basic
cp dialog.xlc ~/.openoffice.org2/user/basic
cd Standard
cp dialog.xlb ~/.openoffice.org2/user/basic/Standard
```
This solved the problem! Yey! :)

---

### Post by la_per on 2008-05-28
I had the same problem with both dialog.xlb and script.xlb since upgrading to Hardy. I followed the procedure above for both and it worked fine.

Thanks a lot !

---

