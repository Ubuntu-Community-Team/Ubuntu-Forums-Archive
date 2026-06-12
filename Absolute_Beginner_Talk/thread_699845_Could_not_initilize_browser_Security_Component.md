---
title: "Could not initilize browser Security Component"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-02-17
I seem to get this message when Firefox starts: [http://ubuntuforums.org/attachment.php?attachmentid=27517&d=1174016360](http://ubuntuforums.org/attachment.php?attachmentid=27517&d=1174016360)

What can be done to correct this, any ideas?

---

### Post by paultag on 2008-02-18
is there any terminal message, try running Firefox in a terminal ( applications --> accessory --> Terminal ) then type firefox into the command prompt. Post that here.

Also, GO SOX!

Cheers,
Tag

---

### Post by sports fan Matt on 2008-02-18
Will do, I downloaed swiftweasel and it seems to have solved it,but will run it as well

---

### Post by paultag on 2008-02-18
I think that it is an issue with the default configuration folder (~/.mozilla) and I need to know if its a directory permission issue or what

From the swiftweasel wiki:
```

Swiftweasel uses its own settings directory. The settings, including bookmarks, history, and extensions are imported from Mozilla Firefox the first time Swiftweasel runs.

```

I am about 80% sure that that is it.

Peace,

Tag

---

### Post by sports fan Matt on 2008-02-18
It could be..I purged the mozilla folder and havent tried to reinstall it since Swiftweasel is running well...

---

### Post by sports fan Matt on 2008-03-07
Im having this issue again..i threw out my Firefox 3.0 and the message still remans, and all nookmarks, extensions and themes are ok, but How can i stop that annoying message?

---

### Post by paultag on 2008-03-07
did you ever purge the dir?

---

