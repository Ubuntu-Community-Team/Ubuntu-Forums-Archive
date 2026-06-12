---
title: "Urgent: I did something really stupid with firefox... help?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by inktri on 2008-01-02
I typed about:config in the address bar and edited the layout.css.dpi value from -1 to 87231

Now my firefox can't load. I know I have to edit some file, where is it though?

Thank you!

---

### Post by bump_ on 2008-01-02
So firefox does not open at all? If no, then I do not beleive you can fix it as it is. 

Try to uninstall and reinstall firefox like this:

```
sudo apt-get remove firefox

sudo apt-get install firefox
```

I am not sure if that will help but it is worth a try.

---

### Post by kestrel1 on 2008-01-02
Second line should read

```
sudo apt-get install firefox
```

---

### Post by bump_ on 2008-01-02
> Second line should read

Code:
sudo apt-get install firefox

oops, I will fix it in the post

---

### Post by chewearn on 2008-01-02
There is no need to take such drastic measure.  Look for a file called "prefs.js" in /home/<user>/.mozilla/firefox/<randomchar>.default/

<user> your username
<randomchar> just that, some random character; there should be only one directory; unless you have created a few profiles

Open prefs.js in a text editor, search for layout.css.dpi, and delete the entire line.

---

