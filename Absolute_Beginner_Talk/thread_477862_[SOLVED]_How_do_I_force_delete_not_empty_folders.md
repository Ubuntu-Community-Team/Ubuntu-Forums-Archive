---
title: "[SOLVED] How do I force delete not empty folders?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by RonB123123 on 2007-06-18
How do I force delete not empty folders?

I recently installed a new version of pidgin by compiling it from its source, but I'm having a problem deleting one of its folders. This is what I get this message.

> 
Cannot move "/home/rona....2/doc-pak" to the trash because you do not have permissions to change it or its parent folder.


Do I need to chmod the folder so I can delete it? If so, how?

---

### Post by nymphaeles on 2007-06-18
use sudo to assume root priviledges.

---

### Post by RonB123123 on 2007-06-18
It doesn't work. When I run this command.

sudo rmdir doc-pak

I get this quote.

rmdir: doc-pak: Directory not empty

---

### Post by dreadlord_chris on 2007-06-18
> **RonTheCon said:**
> How do I force delete not empty folders?

I recently installed a new version of pidgin by compiling it from its source, but I'm having a problem deleting one of its folders. This is what I get this message.



Do I need to chmod the folder so I can delete it? If so, how?

probably just easier to **sudo** the move command - or open nautilus as *root*:
```

kdesu nautilus

```
and delete the offending folders from there.
Just be carefull about what you delete

---

### Post by RonB123123 on 2007-06-18
Thanks it worked! 

I had to use

"sudo nautilus" 

because I have ubuntu not kubuntu. :)

---

### Post by 5-HT on 2007-06-18
> **RonTheCon said:**
> It doesn't work. When I run this command.

sudo rmdir doc-pak

I get this quote.

rmdir: doc-pak: Directory not empty

rmdir only works on empty directories.

You can delete non-empty directories with  'rm -f'
To force the removal (no prompt) it becomes 'rm -rf'
If you do not have privileges to remove the directory, you will need to prefix the command with 'sudo'. 
[B]
NOTE: Be really careful with the -rf flag for rm under root privileges as you can delete your whole filesystem if you're not being careful.[/B]

---

### Post by dreadlord_chris on 2007-06-18
> **RonTheCon said:**
> Thanks it worked! 

I had to use

"sudo nautilus" 

because I have ubuntu not kubuntu. :)

lol.... sorry - I actually meant **gksudo**

---

### Post by nickburns on 2007-06-18
the easy way is 

sudo rm -R folder/

---

