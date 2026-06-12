---
title: "[SOLVED] How do you remove items from the Application Menu??"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-22
I have carried out a search for this and read old posts regarding this with no luck.

In the Applications menu I have the entry WINE ----> PROGRAMS................ then my list

Now after this I have a few programs that I would like to remove from the list.

I have already used the WINE software installer which has removed the content, but am stuck with these names in the menu still.

Any help?

---

### Post by Vadi on 2007-08-22
Right click on the word 'Applications', and select 'Edit Menus'. Then scroll down, click the arrow that's pointing > beside Wine to have it point v instead, repeat the same for programs.

Though after that, the only way I know of is to uncheck every item in a folder and then the folder will dissapear automatically. I don't know how to delete the folders yet :/

---

### Post by chrome307 on 2007-08-22
[IMG]http://img20.imageshack.us/img20/6915/sampleea1.jpg[/IMG]

---

### Post by notwen on 2007-08-22
Are you able to click the arrow along-side of Programs in the left frame to create a drop-down list below Programs and force the contents of Programs to be shown in the right frame?  I'm currently at work and cannot verify this can be done.  Good luck w/ this issue. =]

---

### Post by CowzRule on 2007-08-22
[IMG]http://i18.tinypic.com/624p99v.png[/IMG]

Click the arrow next to Wine in the left column. That will open your Programs sub folder. Then in the right hand column just right click and select Delete to remove the item or just uncheck the box to make it not show in the menu.

---

### Post by mysticmatrix on 2007-08-22
Navigate to directory shown in screenshot. (/home/<user name>/.local/share/applications)

Then Go inside Wine Folder and Delete any shortcut you like.

EDIT: This is not the RECOMMENDED METHOD. Please be careful before you delete a file. Better would be to cut file, leave it on desktop and see if nothing else is screwed up.

---

### Post by chrome307 on 2007-08-22
Thank you very much guys, I did as suggested and it worked :)

---

### Post by Vadi on 2007-08-22
Now click 'Thread Tools' at the top and 'Mark thread as solved' ;)

---

