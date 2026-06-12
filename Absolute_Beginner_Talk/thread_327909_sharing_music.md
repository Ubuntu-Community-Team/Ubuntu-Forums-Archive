---
title: "sharing music"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2006-12-30
I want to share a common folder containing mp3 files between two separate user accounts on one machine.  What do I need to do?

---

### Post by Jorge32 on 2006-12-30
Try changing the permissions on one user about the folder of the other user. Use:
```
gksudo nautilus
```
find the folder, right click and on properties, permissions, and then read  and write 
Does it works?

---

### Post by jasonsexton on 2006-12-30
no it did not

---

### Post by jasonsexton on 2006-12-30
when I log in as the other user it says I do not have permissions

---

### Post by Jorge32 on 2006-12-30
that's what ```
gksudo nautius
``` is used for. With this you will enter as root, or if you like to call it this way as an "administrator" so, there you would have the chance to change those permissions, select the folder and change the permissions. You did it this way?

---

### Post by jasonsexton on 2006-12-30
when I log in as the other user it says I do not have permissions

---

### Post by jasonsexton on 2006-12-30
sorry about the last double post
yes, I used 

gksudo nautius
and I can't access the files
I can see them
but they have locks on them

---

### Post by Jorge32 on 2006-12-30
:-k Uhm usually when you enter as root you're able to change the permissions by this steps. I'll try to be clearer this time.
Select the folder:
then right click>properties>permissions
Then acces: Read and write
Group: leave it like that
Acces: Read and write
Others: read and write

If this sill not working for you, or you already did that, I am sorry I don't know the solution...

---

### Post by jasonsexton on 2006-12-30
does it matter where I have this folder stored?
it's sitting on the desktop

---

### Post by jasonsexton on 2006-12-30
ok, I think I see what's going on

so I have over 500 artist folders within a folder called mp3's
do I have to go to each and every folder an allocate permissions
it seemed to work when I tried one
 
there has to be a way to apply permissions to a direcory and all sub-directories with one command right?

---

### Post by sardion on 2006-12-30
pop open a terminal and do:

sudo chmod -R a+rx /PATH/TO/SHARED/FOLDER

its quick and dirty but it will work

(make it a+rwx if you need write permission)

but bear in mind this opens access to that folder to *all* users on that machine (if its just you with 2 accounts then don't worry about it)

---

### Post by jasonsexton on 2006-12-30
thanks
I'll try that in the a.m.
tired must sleep

---

### Post by 3rdalbum on 2006-12-30
The folder containing the MP3s should be in an area that both users can access.

The desktop of one of the users is not a good place, because one user cannot see any files that are on the desktop of another user.

I approached and solved this problem myself. Put your MP3s folder directly in the root file system. So you'd have /Music, which contains all your albums. Run the command given above on /Music and then all your computer's users will be rocking out to your tunes!

---

