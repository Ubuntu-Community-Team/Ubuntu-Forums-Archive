---
title: "SU permission denied!"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-17
Greetings all, I've struck another wall.
I ran a backup thru the 'simple backup config' app and changed the output to a new file called 'backup1' in my local files.
when I tried to access it I got 'PERMISSION DENIED'.
so I tried thru the terminal and got the same even with super user!:confused:
recently I've been getting 'authentication failed' errors in the terminal but the password is entered correctly (I've  been very careful about this), and oftentimes it seems to carry out the command anyway!? for the usual stuff like 'sudo apt-get' and so on it works just fine.
I can't find anything about this in the posts, howtos, wikis, etc,etc.
I've been downloading and trying to install lots of stuff without success so I may very well have blindly changed some setting or other.:rolleyes:
All help appreciated

---

### Post by adwait on 2006-10-17
Could you also post the output of
```
sudo ls -al
```

---

### Post by carloslosgrande on 2006-10-17
hi Adwait, I can certainly run that command but posting it here is beyond me. I keep getting the error 'invalid file' when I try to attach it here! I've been  having a LOT of trouble with this recently but thats another thread.
I'll have to snapshot it!
thanks for your help.

---

### Post by Ben Sprinkle on 2006-10-17
```

sudo su

```
Do that?

---

### Post by carloslosgrande on 2006-10-17
Hey, Goat Spirit, thanks.
that sure as shit worked! Is that something I should be doing all the time? Any idea why I need to do that with this? Is it the same answer for 'authentication failed' errors??
anyway thanks again!:D

---

### Post by monktbd on 2006-10-17
well sudo is only valid for the command right after.

when you wanted to change to the backup1 folder you did not preceed it with sudo. and the permissions of the backup1 folder only allow the owner (in this case root) to enter the folder with cd.

and if you want to post terminal output you dont need to use screenshots, just mark the wanted output and paste it into the reply box in your browser with a click on the middle mouse button and wrap the whole output in either quote or if it is a long output in code tags.

i never use sudo su because you dont need to be root for all the commands you give. it is good practise to only use root via sudo when it is necessary.

---

### Post by dillbertdabomb on 2006-10-17
gksudo nautilus

---

### Post by carloslosgrande on 2006-10-17
Hi Monktbd, actually I initially did use sudo to change directory for this after the usual method failed. sudo didn't work here - permission denied - was the error.
I've been trying to copy n paste but when i get to this screen there is no paste option available. I don't have a 3 button mouse and as I've just been reading - I guess its really handy with linux!:rolleyes: 
After quite a bit of reading I've got the message about using sudo carefully. Actually, I'm worried that my earlier impulsive actions may have stuffed up some configuration somewhere.
Anyway thanks for your reply and advice, appreciated!:-D

---

### Post by carloslosgrande on 2006-10-17
Hi Dilbertdabomb.
I just tried that and this is what I got.
I often get that 'authentication rejected' error but it still does whatever the command was. What is that??:confused: 
thanks for the command, its a new one for me and I need them!:rolleyes:

---

### Post by monktbd on 2006-10-17
> **carloslosgrande said:**
> I often get that 'authentication rejected' error but it still does whatever the command was. 

this is a problem of connecting the new nautilus to the session of gnome you are running.
this is actually nothing to worry about and it is normal to get it.

for pasting: usually clicking left and right button at the same time should have the same effect as the middle mouse.
i am sure there is a way to assign a keyboard shortcut to the middle mouseclick as well. i have no recipe for that right now though :).
edit: uhm actually ctrl-v should do it i guess because marking automatically copies it to the clipboard.  cannot test it right now though.

---

### Post by carloslosgrande on 2006-10-18
Hi Monk, actually I found that it was my userCP setting that I changed from standard to wysiwyg that caused the trouble with pasting to this screen. So now its back to standard its ok!;)

---

### Post by Ben Sprinkle on 2006-10-19
Glad I can help.
sudo su=>
Means...
Super user and do: switch user/super user
:)

After you jump into super user mode you do not need to type sudo for every command, if not in super user, then you do. :)

---

### Post by carloslosgrande on 2006-10-19
Hi GoatSpirit, sorry to take so long to get back. If I'm the superuser thru this command 'sudo su' must I type 'exit' to change back or does it time out like sudo

---

