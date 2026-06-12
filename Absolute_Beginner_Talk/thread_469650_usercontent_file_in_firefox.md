---
title: "usercontent file in firefox"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by capre91 on 2007-06-10
Hi all, how do I set up a usercontent.css file in firefox? I am using ubuntu 7.04.

I got into the usercontent-example.css file, made a change to it, then tried to save it as usercontent.css...it gave me an error and would not save...can anyone help me?

Thanks, 
Tony

---

### Post by Eric_Jardas on 2007-06-10
You don't have the permission to save the file. Open your terminal and write:
```
sudo gedit ~/.mozilla/firefox/*/chrome/userContent-example.css
```

Make the changes and save.

---

### Post by capre91 on 2007-06-10
Eric, it is working...thank you for the quick reply and for the help.

Tony

---

### Post by liquidcross on 2007-11-09
I've tried this, and it didn't work. I get a "file not found" error. I even tried copying a custom userContent.css file to /etc/firefox/profile/chrome, and that didn't work. What's really strange is that while the file is visible in the folder if I open it, the file does *not* show up in search results, as if it doesn't exist! Any thoughts? (I'm running 7.10, btw.)

---

