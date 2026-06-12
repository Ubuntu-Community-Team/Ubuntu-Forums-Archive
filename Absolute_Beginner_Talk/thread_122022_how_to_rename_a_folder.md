---
title: "how to rename a folder?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by sallam on 2006-01-26
what is the command to rename a folde rplease? the 'rename' option when I right-click is dimmed. I looked a lot and cant seem to find the answer.

Also, If there is a page listing these terminal commands, please give me its link here

---

### Post by poseidon123 on 2006-01-26
Move should do the job.[If I am understanding correctly what u trying to say]

$mv older_folder_name new_folder_name

---

### Post by MartinG on 2006-01-26
[QUOTE=sallam]what is the command to rename a folde rplease? the 'rename' option when I right-click is dimmed. I looked a lot and cant seem to find the answer.

Also, If there is a page listing these terminal commands, please give me its link here[/QUOTE]As poseidon123 says, <mv> is the usual command.  If the option is dimmed in the file manger it's probably because you don't have write permission?  In which case <sudo mv> is your friend!

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by simplyw00x on 2006-01-26
[http://www.ss64.com/bash/](http://www.ss64.com/bash/) is a list of many (all?) terminal commands in linux, and as previosuly stated the linux rename command is 'mv'. If the option is greyed out in nautilus then it may well be a permissions issue in which case you'll have to do 'sudo mv xxxxxxxxx etc' and type your password.

---

