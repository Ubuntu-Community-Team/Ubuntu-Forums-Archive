---
title: "Chmod Directory"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by zhorty on 2005-10-26
Hello.
I have just installed apache2 on my server, but the www-root directory (Wich is /var/www/apache2-default) is read-only, and I can't delete or edit anything. I've tryed all those commands like those on [http://netsecurity.about.com/od/quicktips/qt/aaqtunixfile.htm](http://netsecurity.about.com/od/quicktips/qt/aaqtunixfile.htm) etc, but I can't get it to work. (Yes, i was root in the terminal when I tryed)

So how to I remove the "read-only" with chmod or any other commands?
Hope some of you can give a minute to a newbie :)

Thanks.
- Fredrik

---

### Post by LamB on 2005-10-26
i think its something like    sudo chmod +w directory

---

### Post by wylfing on 2005-10-26
Actually, the root web is just /var/www. As long as your apache server is not running "dmz" (i.e., out on the internet proper), you should be fine doing as LamB suggested. Open a terminal and issue this command:
```
sudo chmod +w /var/www
```

---

