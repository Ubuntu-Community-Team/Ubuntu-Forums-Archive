---
title: "Firestarter: Start automatically"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-09-12
Hello! I recently installed firestarter. And on the firestarter FAQ page, I saw a way to have firestarter start automatically on log-on.

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

However, it requires editing the /etc/sudoers file. When i try to open it with the default text editor, I get the error message, "Could not add application to the application database."

If someone could guide me on how edit the sudoers file, it would be greatly appreciated! From what I've read so far, editing the sudoers file can be dangerous.

Thanks!

---

### Post by p_quarles on 2007-09-12
It *can* be dangerous, but if you follow the instructions there it will be fine. To open the file, press alt-F2 and type the following command:
```
gksudo gedit /etc/sudoers
```

---

### Post by mali2297 on 2007-09-12
From [the official documentation]("https://help.ubuntu.com/7.04/internet/C/networking.html#networking-firestarter"):
> 
After it is installed, run Applications &#8594; System Tools &#8594; Firestarter to configure your firewall. The firewall will now start in the background when your computer starts.

Of course, you might already know that.

---

### Post by Odd-rationale on 2007-09-12
Thanks for your response!

I can now open the file but I can't save the file. I get this error message:

"You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again."

Also in the code given in the FAQ, is there a space after the "=" and after the ":"?

Thanks again!

---

### Post by ubuntukerala1980 on 2007-09-12
As i know firestarter starts runing from boot up. 
You are just trying to start gui

---

### Post by p_quarles on 2007-09-12
That's odd. Type this:
```
ls -l /etc
```
Find the line for /etc/sudoers, and paste it here.

---

### Post by por100pre1 on 2007-09-12
It is not necessary to keep Firestarter running in the system tray. To run Firestarter like that is a security breach. Run it and close it, the firewall will start when you login to session. Firestarter is not the firewall itself, it's just a GUI to setup the firewall.

This is the command to edit sudoers if you wanna do it anyway:

```
export EDITOR=gedit && sudo visudo
```

---

### Post by Odd-rationale on 2007-09-12
Here it is:

```
-r--r-----   1 root     root          403   2007-09-10 10:54 sudoers
```

---

### Post by Element.Ren on 2007-09-12
open a terminal and do this:

```
sudo chmod +w /etc/sudoers
```

and then 

```
gksudo gedit /etc/sudoers
```

you can save the file.

---

### Post by p_quarles on 2007-09-12
I just did a little more reading, and I found out that changing permissions on sudoers is *not* the way to do this (sorry to mislead). The proper way to this is from the command line:
```
sudo visudo /etc/sudoers
```
This will bring the Vi text editor, which can be difficult for beginners, but here's what you do:
1) scroll down to the "users" category
2) press "i"
3) type the new line
4) press "esc"
5) type the following:
```
:wq
```
And voila! This is the best way to edit the file.

---

### Post by Odd-rationale on 2007-09-12
I'm really sorry, but system does not seem to want to cooperate!

Instead of pulling up vi, I get this message:

```
sudo: /etc/sudoers is mode 0640, should be 0440
```

Again, I really appreciate your help!

---

### Post by p_quarles on 2007-09-12
Did you already change permissions using chmod? If so, that's the problem. To fix it, type:
```
sudo chmod 440 /etc/sudoers
```
and it will be back to what it was.

---

### Post by Odd-rationale on 2007-09-12
Can't even do that. Get the same message.

---

### Post by por100pre1 on 2007-09-12
I previously posted the command to edit sudoers. It is very risky to edit sudoers otherwise!

---

### Post by p_quarles on 2007-09-12
> **Odd-rationale said:**
> Can't even do that. Get the same message.
You get exactly the same message? As in "/etc/sudoers is mode 0640, should be 0440"?

Okay, it's early in the morning here, so my apologies -- the original command should have been:
```
sudo visudo -f /etc/sudoers
```Try that first. If that doesn't work, we'll see if invoking a root shell allows you to chmod the file to what it's supposed to be.

EDIT: @por100pre1: I missed your post, and you're right. Like I said, early in the morning here. D'oh.

---

