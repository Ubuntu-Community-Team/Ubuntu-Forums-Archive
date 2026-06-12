---
title: "Help with Users and Groups"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-10-24
Either the whole Users and Groups thing is incredibly complicated, or I'm a complete idiot. I bet I can guess which it is! I'm very confused by it, and I need help.

...anyway, let me give a little back story. If I can help to explain what I'm trying to do, perhaps you can help me figure out how to do it.

I just installed Gutsy on my mother's machine. She has two kids in the house; not only does she want to have separate logins for each of them and for herself, but she wants them not to have administrative privileges and not to have access to her home folder. Additionally, she wants to make it so that, although they can't access her home folder, she can access theirs. Also, on occasion, there may be a program that she'd like to have access to but which she wouldn't want the kids to access, so she'd want the program to show up in her Applications menu but not theirs.

I tried a sort of trial-and-error thing with System>Administration>Users and Groups, but no matter what I did, when I logged in as one of the kids, we could access her home folder. I got confused and frustrated and just gave up.

I guess what it really boils down to is that I don't fully understand the concept of a "group," and I don't know what it's for. A whole list shows up under "groups," and I have no idea if I should/shouldn't be using them, or why I'd want to/wouldn't want to.

Any help, please? If I can't make this happen, she'll want to revert to a Windows OS for the (what seems to be) superior administrative privileges, but I really don't want her to do that, as you can imagine.

Thank you!

---

### Post by alan34 on 2007-10-24
In a teminal

cd /home

chmod go-r "the name of your mum directory"

This takes away read from "group" and "others" on the computer do

ls -l before and after

Cheers Alan

Ps  everybody who is a user on the pc is also a member of a group of the same name

eg I am user alan a member of the group alan so your mums kids as users will also
be members of your mothers group the command above takes away read privlages
from the group. Look in /etc/group in a terminal to see what I mean

less /etc/group

You can edit this file but make a backup first just delete the kids names from the
end of your mothers group (may be at the end of the group "user")

sudo cp /etc/group /etc/group_backup
sudo gedit /etc/group

---

### Post by doctorbighands on 2007-10-24
Also, in all of my trial and error, I noticed that when I delete a user from Users and Groups, ubuntu retains a home file in that user's name. Is there ANY way to delete that file?

---

### Post by yabbies on 2007-10-24
you have to delete those manually

open a terminal and 

```
rm -rf directory
```

the -r stands for recursive so that it deletes anything within the directory
and the -f is for force which is forcing the delete

---

### Post by yabbies on 2007-10-24
also to explain a bit better
when you give the ls -l command
it gives you the permissions of the file or directory or whatever you are looking at

such as you would get

-rwxrw-r--    2 username usergroup 874637582 2007-10-24 15:31 file

the very beginning is what you are looking for

it tells you the usership of the file

(-) is the type of file, it would be a d if its a directory like in your case

(rwx) is the user permissions this says that the user can (r)ead (w)rite and e(x)ecute the file

(rw-) is the current groups permissions the can (r)ead (w)rite but not execute the file therefor it is a dash (-)

(r--) is everyone else, all other users and groups so all anyone else can do is (r)ead the file.


hope this helps in explaining a bit more

ooops forgot to say that directories are different
(x) indicates that the user can access the directory if there is no (x) then the used will be given a "access denied"

---

### Post by doctorbighands on 2007-10-24
Okay, I have it just about how she wants it. There's just one other thing:

I used "alacarte" to remove the icons for programs she didn't want the kids accessing. The problem is that you can right-click on Applications, then click "edit menus," and alacarte pops up. Obviously, they could put back what's been taken away.

The question is, then, can I make it so that they can't access alacarte so easily (preferably by making it an administrative thing so that a password is required)?

---

