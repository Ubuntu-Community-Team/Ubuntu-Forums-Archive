---
title: "Need to change folder permissions to enable spell checker library"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by john262 on 2006-11-22
I need to enable read write and execute permissions for the /usr/lib/mozilla-firefox/extensions folder. I have been reading other posts on this subject and various things that I am supposed to enter at the command prompt in order to do this but I must be doing something wrong because no matter what I try I still get the message that I am not the owner and I cannot change permissions. But I need to do this so that the Spellbound spell checker for Firefox 1.5 will work.

Can someone please help? Could you please just tell me exactly what to enter at the command line so I can paste it in there? Thanks a lot.

---

### Post by Derek Tomes on 2006-11-22
I'm new here. I have been using Linux for almost a whole day, so you may want to ignore this:

try adding "sudo " (without the quotes) before the commands you issue (sudo="super user do"). That should issue the command as the super user.

I think :???:

---

### Post by john262 on 2006-11-22
Thanks my friend from New Zealand, but I have already been using sudo. It's something else I'm doing wrong. Hopefully someone else will weigh in here. I'll check back in the morning because I'm going to bed now.

---

### Post by Carlos Santiago on 2006-11-22
You should not change the permissions of the folder, it opens an unsecure door. 

Are you an Administrator user?

If you are, just type (in order to copy the file to that folder)
#sudo cp <extention_file> /usr/lib/mozilla-firefox/extensions
and then type your pass when asked

If you are not an Admin, you can also copy the extensions to your personal mozilla folder (that should be in <home>/.mozilla-firefox)

---

### Post by Rajiv_Nair on 2006-11-22
run 
sudo nautilus 
from ur terminal window..then in the file browser dat pops up u'll find that ur able to chng permissions to each and every drive/folder:)

---

### Post by john262 on 2006-11-22
Thanks Rajiv. That worked.

---

### Post by encikraju on 2006-12-03
hye, i have the same problem. i can't write the partition/folders.
it is read only and the owner belongs to root.
what should i do? change the file permissions or change the owner?
the situations is like the attachments.
i've tried gksudo nautilus and still i can't navigate to /media/sda3 to change the permission.
i've tried the chmod but nothings change.

x0x@x0x:~$ sudo chmod a+w /media/sda3/
chmod: changing permissions of `/media/sda3/': Read-only file system

really2 need helps...

---

