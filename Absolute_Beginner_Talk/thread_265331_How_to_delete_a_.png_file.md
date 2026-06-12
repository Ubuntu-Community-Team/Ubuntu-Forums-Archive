---
title: "How to delete a .png file"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-09-25
I am not able to remove or delete 4 .png files from the Trash directory.
Is there a way to delete these files ?
  
The files are links to files in another directory that have been deleted.

In other words  how do you delete link files?

Thanks

---

### Post by henriquemaia on 2006-09-25
Most likely, you have a permission problem on those files. 

If you're not afraid of the terminal, open one (Applications > Accessories > Terminal) and then type:

```
chown -Rv **your_user_name** ~/.Trash
```What this command will do is restore to your ownership all the files on the folder .Trash (where the trash is kept). You'll see what is happening to the files on the trash folder. After the command ends this, try deleting again those files from your trash. Maybe that will do it.

---

### Post by kent41 on 2006-09-25
I tried that command and it showed that I was already file owner and I had all priveliges.

I could not delete the files.

I think the problems is the file is a LINK to a deleted file. I need some way to override the link problem.

---

### Post by henriquemaia on 2006-09-25
You can remove them with sudo.

On the terminal, type:

```
sudo rm ~/.Trash/name_of_the_files_you_want_to_delete.png
```

---

### Post by henriquemaia on 2006-09-25
You can also do this more visually, with nautilus. 

For that, you type on a terminal:

```
sudo nautilus ~/.Trash
```Then delete the files you want.


ps: on my first post, I forgot to type **sudo** before the command **chown**. My appologies.

---

### Post by kent41 on 2006-09-25
Thanks for the help.

I found another way to delete the link files.

1) I used the editor to create a file with the original name in the original      file directory.

2) next I deleted the Link file in the Trash Directory.

3) next I deleted the file the link pointed to.

  But it worked :-D :-D

---

