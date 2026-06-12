---
title: "problem deleting exe files from trash"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by dynoweb on 2007-07-27
i cannot delete them from my trash can.... there seems to be a permission error. 
I have attached a screenshot of the error below. Please let me know what you think needs to be done to delete these exe files.

---

### Post by Rocket2DMn on 2007-07-27
You either need to delete them with root privileges or set yourself as the owner of the parent directories of that file.  If it is in your .wine folder, try
```
sudo chown -R yourusername ~/.wine
```
PS: What program/applet are you running to get those graphs in the panel?  I have conky, but it's not quite the same.

---

### Post by stchman on 2007-07-27
> **dynoweb said:**
> i cannot delete them from my trash can.... there seems to be a permission error. 
I have attached a screenshot of the error below. Please let me know what you think needs to be done to delete these exe files.

Try this:

sudo rm -f ~/.Trash/*

---

### Post by dynoweb on 2007-07-27
i found out the problem.... the permissions were not staying to what I had changed them to so I can delete them.

**Rocket2DMn:** I am using what i like to call human studio... a mix between Human Theme and Ubuntu Studio Theme.

---

### Post by Rocket2DMn on 2007-07-27
Good deal, man.  I've heard a lot of nice things about Ubuntu Studio, and although I'm not a big video/audio maker or editor, I think sometime I'll have to give it a try, just for kicks.  
Glad you got the problem fixed.

---

### Post by stchman on 2007-07-27
How did you put a Trash Can icon on your desktop?  Please tell?

---

### Post by Rocket2DMn on 2007-07-27
> **stchman said:**
> How did you put a Trash Can ison on your desktop?  Please tell?

This question came up just yesterday - [http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/add-the-trash-can-icon-to-your-ubuntu-desktop/)

---

