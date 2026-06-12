---
title: "What to do when program won't run?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-26
I downloaded pSX, an emulator. It works fine on my desktop. Using the same steps, it won't run on my eeePC.

 When I click it nothing happens and when I navigate to its directory and run pSX, bash says it's not a command.  If I click on Properties in the GUI and go down to the check mark that says 'make executable' it has a little black dash in it, when I click a checkmark appears for like a half a second and then disappears. But Properties says that it's an execuable  binary file.

The program is on an SD card, is that the problem?

---

### Post by spupy on 2008-03-26
First, you can make it executable in bash:
```
chmod +x file
```
And when running it make sure you have "./" before the command. Because it is possible that "." - the current directory, is not in your $PATH.

But i think it is very possible that the card is mounted with no executable flag, so to say - you can't execute files **from** it.
To check that statement, create a simple script on the card:
```
#!/bin/bash
echo "It is working"
```
"Chmod +x" it and try to run it off the SD card. But i bet it wont run.

---

### Post by BetterSense on 2008-03-26
I already knew to chmod it, but I had forgotten the ./. It's running, but not working properly, but that's another thread. Thank you.

---

