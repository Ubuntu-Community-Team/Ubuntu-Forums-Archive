---
title: "I think I chmodded my root!"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by AJL on 2006-07-05
ok, complete noob here so give me a little slack (please)

i was trying to change the permissions of a file that is in root, and i think i changed the permissions of the actual root directory.  

so, how do i change them back

and what should they be set to?

thanks so much

---

### Post by taurus on 2006-07-05
If it's a directory, you just change it back to something like
```

sudo chmod 755 <directory name>

```

---

### Post by AJL on 2006-07-05
well, the main problem is that gnome won't let me log in since it doesn't have permissions....or something to that effect.  

so i guess i should add that to the list...

how to get to a prompt of some kind
how to undo the dumbschitt i did.

thanks again everyone

---

### Post by AJL on 2006-07-05
clarification:  i can log in, accepts user/pass, but it just freezes there then throws the permission error message.

---

### Post by taurus on 2006-07-05
Wait for the system to finish booting, until you see the GUI login screen.  Then press <Ctrl><Alt>F2 to get into a console.  Log in and run that command again...

---

