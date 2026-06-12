---
title: "firefox profile folder"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Adolphian on 2008-03-28
how do i access it, i need to change something.

ubuntu 7.10

---

### Post by munkyeetr on 2008-03-28
In your /home directory:

~/.mozilla/firefox

---

### Post by Adolphian on 2008-03-28
ok i feel pretty damn dumb right now.

but i dont really understand how to get there because i dont see a mozilla folder in my home..... :(

when i type that into terminal it tells me its a directory, and i know it is, but i dont know how to get there...

total newb.

---

### Post by Ardrias on 2008-03-28
Open a terminal.

```
cd .mozilla/firefox/*/
```

And there you are!

Or if you're using Nautilus to browse, press CTRL+H to show hidden (dot) files.

---

### Post by Adolphian on 2008-03-28
it was hidden, thank you.

---

### Post by hyper_ch on 2008-03-28
A file or folder starting with a "." is hidden... either use the terminal with

```

ls -al

```

or set your file manager to show hidden files/folders.

---

