---
title: "&quot;Move to trash&quot; not working?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2007-10-30
Hi everyone,

I've got a bit of a mystery: when I right-click on a file in Nautilus and select "move to trash" the file disappears but is not moved to the trash(!). Where are these files going?

Thanks in advance!

Plinydogg

---

### Post by misfitpierce on 2007-10-30
You sure they are not inside trash but the trash icon is not changing to show something inside it? Try restart then try throwing something away.

---

### Post by philinux on 2007-10-30
Remove the trash applet from the panel and then add it back.

---

### Post by reza81 on 2007-10-30
> **philinux said:**
> Remove the trash applet from the panel and then add it back.

Yes, I had this once to. Do the above & it properly will wor just fine :D

---

### Post by plinydogg on 2007-10-30
misfitpierce: Yes, I am sure. I opened up trash to see if it was there and it wasn't. 

philinux and reza81: I will try this as soon as I get home this evening and if it works I'll mark this thread as solved. 

So, I wonder where those files go if not to trash???

Thanks everyone for your help!

---

### Post by plinydogg on 2007-10-30
I removed it and then readded it but it still isn't working! Oh well, I'll just [shift] + [delete] from now on.

---

### Post by FXEF on 2007-10-30
> **plinydogg said:**
> I removed it and then readded it but it still isn't working! Oh well, I'll just [shift] + [delete] from now on.


To see what is in your Trash:
Open a Terminal window and use these commands.
Use the cd  command to move to the .Trash folder.
earth:~$ cd .Trash

Then use the ls command to see what is inside of the .Trash folder.
earth:~/.Trash$ ls

This will tell you if the files are going to the .Trash folder. If you can see files listed using this method and not with the GUI Trash then most likely the Trash GUI will need to be repaired.

Note: the .Trash folder has a period as the first character and an uppercase T letter.

---

### Post by plinydogg on 2007-10-30
Thanks FXEF! However, ls doesn't show anything in the directory! I am reallly curious about what is happening to these deleted files :)

---

### Post by tuxalot on 2008-02-23
Same problem here...applet in the top bar is working properly (shows items in it when not empty), but the trash icon on the desktop is not changing to indicate it is not empty.  If I double click the desktop icon, it shows the contents.

---

### Post by plinydogg on 2008-02-23
I'm still afflicted by this problem. It appears that we're in a distinct minority as not many people appear to experience this issue. 

Let me know if you fix it =)

---

