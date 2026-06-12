---
title: "Strange Opera Message..."
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-10
I switch between Opera and Firefox and in Pera 9.5 I get this message : There was a problem initializing Opera Mail.

Not possible to run old Opera version with new Opera mail files.AccountManager Init failed
Engine Init() failed


I dont even remember setting up opera mail, how odd

---

### Post by TeaSwigger on 2008-03-11
No clue.

But if it keeps popping up you could try saving your bookmark file then deleting the profile folder, prompting it to make a new one, or starting it with a -nomail flag, like putting this in the exec line of the opera.desktop file

```
/usr/bin/opera -nomail
```

which I do, along with other unused features ( -nosession -notrayicon -disableinputmethods) on the odd chance it lightens the loadup at all. Luck :)

---

### Post by Joe Dinmore on 2008-03-11
I'm getting that msg with recent 9.5betas as well - probably because I haven't set up Opera mail at all.
 If you want the latest stable version of Opera, stick with v9.26.

---

