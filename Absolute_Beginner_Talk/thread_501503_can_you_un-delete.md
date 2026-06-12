---
title: "can you un-delete?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by miqmaq on 2007-07-15
I seem to have deleted a file in the "Deleted items Folder" is there any way of getting it back?.

In Windows XP there are any number of utilities to help you recover a deleted item, or if you wish to delete them so that you can never get them back, my question is are there similar utilities for Ubuntu?.

thanks.

---

### Post by bapoumba on 2007-07-15
How did you delete the file ?

---

### Post by Wiebelhaus on 2007-07-15
lol , I cleaned out my trash can the other day and there was like 20,000 files in there.....

but , if you didn't clean out the trash can yes , you can just retrieve it from there , if you did flush out the trash can , I have no clue.

---

### Post by miqmaq on 2007-07-15
well i can only assume that one of my children: enough said, i left the PC on when i went for breakfast when i got back on the file i had been working on had gone, asked the kids they no nothing about it, i'm just assuming that they used the deleted items folder, sorry but i can't be more specific about what happened.

Thanks Mick

---

### Post by bapoumba on 2007-07-15
So then yes, look in your trash folder.

You can also open a terminal, and run:
```
ls ~/.Trash
```
see if the file is listed there.

I just asked because if you had deleted with "rm", that would have been pretty definitive.

---

### Post by miqmaq on 2007-07-15
looked in delete folder, and thank God it was there.

i have never come across that command before 1s ~/.Trash, as i am so new to Ubuntu there are a lot of commands i don't know, but i tried that one in the terminal and it didn't know it either, also i don't know what a "rm" is/are?.

but thank you all for the help.
cheers Mick.

---

### Post by Outrunner on 2007-07-15
```
ls
```

It's a lowercase L not a 1(one) and it's used to list files in a directory.

And the 

```
rm
```(remove) command is used to delete files.

---

### Post by Majorix on 2007-07-15
You can also access the trash by clicking its icon in the lower right corner, if you like things visual.

rm is used to remove a file without sending it to the trash: Completely lost.

---

### Post by miqmaq on 2007-07-15
thanks for the info on the commands.

but how do you use the "rm" exactly??.

Cheers Mick

---

### Post by Majorix on 2007-07-15
Just do
```
rm filename
```

---

### Post by miqmaq on 2007-07-15
thanks Majorix, 

i have only been using Ubuntu for a little while, and it's been a steep learning curve.

Thanks again Mick

---

### Post by Outrunner on 2007-07-15
Just thought I'd let you know about the 'rm' command, if you want to delete a whole directory, you have to use 'rm -r'.

```
rm -r ~/dir_name_here
```

Also if you're ever interested in what a command does, you can type

```
man commnd
```

(man stands for manual)

---

### Post by rax_m on 2007-07-15
Just thought you should note that if you use rm to delete files they are NOT placed into your trash can and will be a lot harder to recover!

---

