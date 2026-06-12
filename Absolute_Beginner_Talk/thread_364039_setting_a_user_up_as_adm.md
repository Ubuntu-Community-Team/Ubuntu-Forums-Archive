---
title: "setting a user up as adm"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by Starry on 2007-02-17
ok...so i am back to try and get my issues resolved once and for all PLEASE.

the issue i had with flash 9 not installing was i am not allowed to write to anything.  same with moving files that i wanted to with my font files.

with taurus' help yesterday i have gotten everything straightened out on how to do that and how to move the files that i need to for both my fonts AND flash.  the best option is to set my login as adm and admin.

the problem was when i logged out into recovery mode in debian 3.5 [7], the latest version i have, there was no admin for me to set my user on. [i have all those instructions] i just went on my own instincts and set up my user with write access to things i thought i might need [in order all i have write access to, new ones i added are in bold]

[B]root: x : 0 : startears
adm: x : 4 : startears[/B]
dialout: x : 20 : startears
cdrom: x : 24 : startears,hal
floppy: x : 25 : startears,hal
**sudo: x : 27 : startears**
video: x : 44
**Debian-exim: x : 102 : startears**
startears: x : 1000
**dirmngr: x : 105 : startears**

admin was the other one i was told to add my user name [startears] to but it wasn't in the list.

should i erase that startears: x : 1000 one in particular?  after i added myself to these and i tried to move [command mv] the files from my /home directory i got a permission denied error.  so what have i done wrong?  which of these write access' should i not have/not need?  is there another one that i do need instead?

for the record, i [startears] am listed as a user on my laptop not the root/admin because i didn't want to screw anything up in linux.  now that i want to do my own computer work is why i am setting myself up to be able to write things.

alright.  thats the whole story.  so if anyone can understand all that and give me an absolute answer in easy english [this is all new to me please remember that] i'll get out of your hair for awhile and be very appreciative of all the help you all have given to me on this [seemingly] idiotic problem i have been having.

---

### Post by Starry on 2007-02-17
bueller??

---

