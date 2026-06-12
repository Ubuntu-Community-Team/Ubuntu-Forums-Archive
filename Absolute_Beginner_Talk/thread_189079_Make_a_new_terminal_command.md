---
title: "Make a new terminal command"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by TrendyDark on 2006-06-04
How would I make a new command for the terminal, specifically to launch and application?

---

### Post by kaamos on 2006-06-04
Applications->Accessories->Terminal
```
nano nameofcommand
```
Then insert the lines you wish to execute and save the file. Then
```
chmod +x nameofcommand
```
this makes the file executable. Finally move the file somewhere in your PATH, for example
```
sudo mv nameofcommand /usr/local/bin
```

---

### Post by TrendyDark on 2006-06-04
Thanks, needed to install Flock with a command and such lol. Big help!

---

