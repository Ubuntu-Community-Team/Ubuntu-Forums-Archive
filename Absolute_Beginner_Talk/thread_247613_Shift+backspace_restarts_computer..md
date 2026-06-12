---
title: "Shift+backspace restarts computer."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Rainz3 on 2006-08-30
For some reason on my desktop installation of ubuntu when logged into my sisters name if shift+backspace it restarts the computer. It doesnt do it when logged into my name but does on hers. I went through both our names keyboard shortcuts and disabled everything restart the computer and it still does it. Any ideas?

---

### Post by Rainz3 on 2006-08-31
Anyone have any advice or insite on why its doing this? I have tried in diffrent sessions(xgl,xfce,gnome,gome failsafe) and it still does it just on her name and the log in screen.

---

### Post by bruce89 on 2006-08-31
Is there any binding for log out in System>Preferences>Keyboard Shortcuts?

---

### Post by Rainz3 on 2006-08-31
I already went through all the keyboard shortcuts and disabled everything on each account.

---

### Post by Metacarpal on 2006-08-31
Did a little forum searching, and here's what I found:

Create a new text document (there's a text editor in Applications > Accessories if memory serves {trapped on a Winbox at work right now}).  Paste this in and save it to your home directory:
```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

Then right-click the file, and click the "Executable" check boxes.

Now you'll need to move the file into /usr/bin - the easiest way to do that will be through Terminal (as you need permissions to write to the directory):

```
sudo mv filename /usr/bin
```

Then go to your System menu > Preferences > Sessions > Starup programs and add your file to the list.

---

