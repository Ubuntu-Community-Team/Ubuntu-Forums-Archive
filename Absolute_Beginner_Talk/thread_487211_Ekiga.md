---
title: "Ekiga"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by superintelligentape on 2007-06-28
I recently tried to install Ekiga softphone software, but the installer froze so I had to force it to quit ever since ekiga doesnt open...

---

### Post by kpkeerthi on 2007-06-28
Try reinstalling...
```

sudo aptitude reinstall ekiga

```

---

### Post by superintelligentape on 2007-06-28
Nope still doesnt work it just ways starting ekiga sofphone on the bottom taskbar and then nothing opens

---

### Post by kpkeerthi on 2007-06-28
Start from the terminal. Open terminal and type ekiga. That way you could capture error messages, if any.

---

### Post by superintelligentape on 2007-06-28
Nothing happens when i type ekiga into the terminal..

---

### Post by kpkeerthi on 2007-06-28
Did it just exit without any error? Strange. I'm out of suggestions.

---

### Post by superintelligentape on 2007-06-28
do i just type in ekiga into the terminal? no sudo or somthing like that?

---

### Post by kpkeerthi on 2007-06-28
sudo is not required

---

### Post by superintelligentape on 2007-06-28
is there any way to go through that initial setup again?

---

### Post by kpkeerthi on 2007-06-28
Uninstall using...
```
sudo aptitude purge ekiga
```
And...
Delete the folder **.ekiga** from your home directory. I'm not in front of ubuntu right now. So not sure what the folder name exactly is. It should be a hidden file beginning with a dot.

And then install...
```
sudo aptitude install ekiga
```

---

### Post by superintelligentape on 2007-06-28
oops nevermind i rebooted and im in the initial setupagain

---

