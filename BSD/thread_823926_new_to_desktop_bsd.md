---
title: "new to desktop bsd"
date: 2008-06-09
forum: BSD
---

### Post by cmay on 2008-06-09
hi .
i am new to free bsd. installed it this morning and i was getting my upgrades just now. i checked security and i found 14 packages i was adwised to uinstall. now this i do not know how to do as of this moment. i figured out how to get portsnap working after ten minuttes but i cant for the life of me find out how to uninstall the (security)affekted packages .
i googled and tried to read the docs on my desktop but still ?
anyone here can help?
i would be very gratefull.

btw i like the looks and feel of the bsd so far other than this slight problem. i cant wait to have this all configured and running to my liking.
thanks alot for any adwise or pointers in the right direction.

---

### Post by techmarks on 2008-06-09
If you're just trying to remove the package, use pkg_delete,
for example;

```
# pkg_delete lsof-4.57
```

If it informs you the package has dependencies and cannot be deleted, you still want to get rid of it use the -f option

```
# pkg_delete -f lsof-4.57
```


that will force the deletion.

---

### Post by cmay on 2008-06-09
hi .
thanks for the reply.
can i please ask one more question.
when you type who in the terminal is it supposed to show two logged in users. that is root and your username. 
root still loggen in and youruser name still logged in. 
i was reading the docs again searhcing for the answer for this
 while i noticed  the pop up saying my ip adress suddenly changed. 
i did not run as root user at the time i am pretty sure of that.
thanks again.

---

### Post by techmarks on 2008-06-09
try doing the 'w' command, that ones tells who is logged in and what 
they are doing.

I think you'll see the two users when you have X running and 
if you look under what that one is doing it should say xinit.

---

### Post by cmay on 2008-06-10
hi.
thanks for the reply.
i logged out last night and tried again this morning whit who and last.
it seems there was a lot of root logins but when i i did who there was only me listed.
 do you think i have not logged out from the portsnap terminal.
w tells me nothing here this morning. it only shows my username.

my internet on that machine is for some reason totally messed up and it has to do whit something the internet provider did when they was replacing some cables here in the city they tell me. its connection on and of and then random connections trying to be made. its annoying becouse i cant rely on getting on the internet at all. maybe its something to do whit it.

thanks for the time you spend on me.
i am very happy whit this help .

---

