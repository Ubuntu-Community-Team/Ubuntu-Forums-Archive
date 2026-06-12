---
title: "Nautilus Scripts"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by twoseids on 2006-02-10
This may be a dumb question, but hey, that's what "Absolute Beginner Talk" is for, right? \\:D/ 

I just attempted to put a script ([this one]("http://ubuntuforums.org/showpost.php?p=334545&postcount=1")) into my /home/.gnome2/nautilus-scripts folder. But when I right-click in Nautilus on a file, in order to run this script, the only two options are gedit-root and Open Terminal Here. The third (new) one doesn't show up.

What do I do to make this script visible? I did do **chmod 740 ~/.gnome2/nautilus-scripts** to make it executable, and the file type is script. But I must have missed something.

Thanks for any help!

---

### Post by joselin on 2006-02-10
You have to chmod 755 script_filename instead of folder that content the script.

Regards.

---

### Post by xmastree on 2006-02-10
well, I just c&p from that thread into a new file, set it to 740 and it appears in the list. I haven't tried to actually run it, but it does show up.

> I did do chmod 740 ~/.gnome2/nautilus-scripts
Hmm... I think that ought to be:
```
chmod 740 ~/.gnome2/nautilus-scripts~/.gnome2/nautilus-scripts/YourNewScript.sh
```

Edit: Damn, joselin, ya beat me to it... :-)

---

### Post by twoseids on 2006-02-10
[QUOTE=joselin]You have to chmod 755 script_filename instead of folder that content the script.

Regards.[/QUOTE]
Yes! That did the trick. Thanks very much!

---

