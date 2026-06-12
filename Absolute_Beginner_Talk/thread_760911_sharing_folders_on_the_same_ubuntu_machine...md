---
title: "sharing folders on the same ubuntu machine.."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by sneeks on 2008-04-20
i am trying to share my music folder to other users on my Ubuntu box,but to no avail,it's just sharing on the same machine so no networking involved.
when another user logs on and gos to the music folder its just empty.
i know im being really stupid here so help me out guy's....
sneeks.

---

### Post by otrojake on 2008-04-20
I'm not in front of my Ubuntu box right now, so I can't tool around with the commands exactly to remember how they work, but here's what I would do...

Create a group called "music" by doing

```
sudo addgroup music
```

Then add each user into that group by doing...

```
sudo adduser "user" music
```
substituting each user name in place of "user" (no quotes).

```
sudo chown -R <owner>:music /"directory_of_the_folder_to_be_shared"
```

Then...

```
sudo chmod -R 775 /"directory_of_the_folder_to_be_shared"
``` if you want them to be able to add or remove music to/from the folder

or
```
sudo chmod -R 755 /"directory_of_the_folder_to_be_shared"
``` if you don't want them to add/remove music from the folder.  Again without quotes.  You might have to log out and back in for the changes to take effect.  That's the best I can remember right now off the top of my head for how to do this.  If anyone knows a better way, go ahead and correct me. :)

EDIT:  Thanks Oldsoldier.  It's hard for me to remember all this stuff off the top of my head without it in front of me.

---

### Post by Oldsoldier2003 on 2008-04-20
dont forget you need to chown the music directory to allow the music group access

```
sudo chown <owner>:music /path/to/shared/folder
```

---

### Post by sneeks on 2008-04-21
mnnnn,is there no easier way,i suppose not.
under dir to shared,would i replace it with music or each individual folder as i have a lot of stuff??

---

### Post by otrojake on 2008-04-23
You don't have to do it to each individual folder, just to your music folder.  But, since I wasn't at my machine when I typed the first post, I forgot a very important option in those commands.

I edited above too, but I'll post it here too.  Make sure when you do the chown and chmod commands, you use the -R (make sure the R is capitalized) option.  Like so...

```
sudo chown -R <owner>:music /"directory_of_the_folder_to_be_shared"
``` 

for read-write

```
sudo chmod -R 775 /"directory_of_the_folder_to_be_shared"
``` for read-only

```
sudo chmod -R 755 /"directory_of_the_folder_to_be_shared"
```

If you've already run those commands, just run them again.  It won't mess anything up.  If you run into any other issues, let us know! :)

---

