---
title: "Problem creating new group"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-06-02
I'm trying to install a game for my son, and during setup this game is added to a group called games.

So that we can run it, I've tried to create a group - I open "users and groups", enter password, and enter the group name, tick all users (as I want them all to be in the group), and click OK. But access is still denied, and the group simply isn't there when i re-open the dialogue box. When I try to repeat adding a group, the next available group number is the same - so it obviously isn't being created.

I'm going wrong somewhere, but I can't see where!

TIA for any advice. My advice is never install games - it can't be done! :)

I've just been googling on this - can a user only belong to one group? So I can't add current users (who are already created in their own group) to a new group?

---

### Post by kevdog on 2007-06-02
There is probably more than one way to do this but first take a look at the file:

/etc/group

This will list all the groups available on your computer.  Look specifically for the games group and see if there are any users attached.  It may look something like:

games:x:107:joe,dad

In this example joe and dad are members of the group games.
To add members to this group do either of the following:

Using the console:
```

sudo adduser user group

```

For some reason if everything else fails, just manually edit the /etc/group file, and add the user manually onto the group:

sudo gedit /etc/group
Find the line, and then just add the user.

That should be about it.  Adding users must be done with root privledges.

---

### Post by blueturtl on 2007-06-02
edit: What the above user said, I'm a slow typer. :)

Users can belong to multiple groups. Can't really say why the graphical tool isn't working for you.

In that light I recommend trying the actual commands in the terminal:

You can locate the terminal in the applications submenu.
After that type the command 'sudo groupadd games' (this will create the group games)
Then type 'sudo useradd -g games timmy' (this adds the user timmy to the group games)

This approach has the advantage that should something go wrong an error message ought to be printed for further analysis.

More information on each command can be acquired by typing 'man commandname' into the terminal (use arrows to scroll, q to close the manual).

---

### Post by freesitebuilder on 2007-06-02
When I checked the /etc/group file, it shows up OK, with the users. But it still doesn't show in the GUI dialogue box - at least I know I'm not going completely mad!

I still can't run the program, despite changinf permissions thro the terminal - I'll have to try it again tomorrow when my brain isn't so numb! 

Thanks :)

---

### Post by zvacet on 2007-06-02
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

