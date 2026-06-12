---
title: "safe to leave the shell open all the time?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-08
Okay, this might be a super-silly question, but it stems from my ignorance of the shell at this point in my Linux career :)

Is it safe to leave the shell open all the time? Does this strain the system at all, or are there any benefits to closing it and restarting it every now and then?

Thanks.

---

### Post by Brunellus on 2006-08-08
perfectly fine, unless it's a root shell.  it's a very bad idea to leave a root shell up and running all the time;  this is why we use sudo.

---

### Post by Arisna on 2006-08-08
It is safe as long as you aren't running it with root privileges when people you don't trust have access to the machine.  This isn't much of a concern because Ubuntu uses sudo by default rather than a root account, and those privileges expire after 15 minutes.

---

### Post by JohnJSal on 2006-08-08
Thanks! Call me a nerd, but there's just something cool about having the shell open all the time. In fact, I think I'll add it to my startup programs when I get home today. :)

---

### Post by Indras on 2006-08-08
I use yakuake, which has a drop-down shell, kind of like the terminal window in Quake.  Also, somewhere around here on the forums, I saw a howto on setting your shell as your wallpaper on your desktop.  Both options are very cool if you use it often.

---

### Post by Brunellus on 2006-08-08
> **JohnJSal said:**
> Thanks! Call me a nerd, but there's just something cool about having the shell open all the time. In fact, I think I'll add it to my startup programs when I get home today. :)
you can use a package named 'tilda' to do this for you.  it gives you a little terminal running on your desktop all the time.  You can fix it to be 'transparent' (really only pseudo transparent, i.e. showing your bg image...still, cool).  nice, especially if you have it running something in the background (like, say irssi)

---

### Post by taurus on 2006-08-08
I have two terminals (aterm) open automatically when I log in because I do everything from a terminal...

---

### Post by 23meg on 2006-08-08
You may also like [this trick]("http://www.ubuntuforums.org/showthread.php?t=81727").

---

### Post by JohnJSal on 2006-08-08
Awesome. I plan to read that as soon as I can escape the confines of my Windows work computer and get home to Ubuntu. :)

---

