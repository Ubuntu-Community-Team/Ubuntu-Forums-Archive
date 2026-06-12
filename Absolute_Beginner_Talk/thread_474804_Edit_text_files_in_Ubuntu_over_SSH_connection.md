---
title: "Edit text files in Ubuntu over SSH connection"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by brobertsleo on 2007-06-15
I set up a LAMP server yesterday and have it set up so that I can remote connect to the computer using OpenSSH, the connection works, but I need to edit a text file and when I type the command "sudo gedit <path>" it displays an error saying that it cannot open the display. Does anyone have any ideas?

---

### Post by Malibu Illusion on 2007-06-15
> **brobertsleo said:**
> I set up a LAMP server yesterday and have it set up so that I can remote connect to the computer using OpenSSH, the connection works, but I need to edit a text file and when I type the command "sudo gedit <path>" it displays an error saying that it cannot open the display. Does anyone have any ideas?

SSH is a command-line interface.  gedit is a graphical program.  Type something like:

```
vi file
```
or
```
nano file
```

Assuming you have either of these editors installed.  This will allow you to edit it from the command line.  I personally favor vi for editing files like this, however it requires a bit of knowledge about the shortcuts and how to operate it correctly.

---

### Post by Tomosaur on 2007-06-15
Any SSH client worth its salt has the ability to do X forwarding (obviously, you need X enabled on the client computer!), but the actual method to enable it may be different depending on your SSH client. Easiest solution is to just refer to your SSH software's documentation (man ssh), which should tell you what you need to know.

However, it's much quicker and easier to just use a command line editor, like Malibu pointed out. X forwarding is generally a slow operation.

---

### Post by brobertsleo on 2007-06-15
Can I download the editors for windows?

---

### Post by Malibu Illusion on 2007-06-15
I'd definitely say it's not worth setting up x forwarding just for text editing; the command line is more than capable and preferable.

You don't need to install any editors as they execute server-side.  You have the ability to edit the files within the command line itself.

---

### Post by Tomosaur on 2007-06-15
> **brobertsleo said:**
> Can I download the editors for windows?

With Cygwin, yes, but if you're accessing an Ubuntu box from Windows over SSH, then you do not need to do this. The program is run at the Ubuntu end - the file does not get transferred to the client machine.

---

### Post by brobertsleo on 2007-06-15
Thx everyone, everything worked out fine. I really appreciate all your help.

---

