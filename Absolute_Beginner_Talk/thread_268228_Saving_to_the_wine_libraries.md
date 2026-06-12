---
title: "Saving to the wine libraries"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-29
I'm trying to install something called BwGen. It is written for Windows but in the FAQ it says it will work if I have wine installed (which I do). Will somebody please help me through the download and install process? Here is the site Im downloading from:
[http://www.bwgen.com/download.htm](http://www.bwgen.com/download.htm)

---

### Post by ewl1217 on 2006-09-29
First, download the installer and open the terminal. Then navigate to the folder you downloaded it to. Let's say that your username is user and you saved it to the desktop. You would type
```
cd /home/user/Desktop
```
Then use the command
```
ls
```
to make sure that the file is actually there. Then run the command
```
wine bwgen31.exe
```
If all goes well, then it should install properly. Then navigate to Wine's fake c drive with (replace user wih your username)
```
cd /home/user/.wine/drive_c
```
Then do some hunting around for the executable with ls and use cd to navigate through the folders. Then run it with the following command:
```
wine program.exe
```
Just replace program.exe with the executable's name. Let us know if you need any help.

---

### Post by voodoonirvana on 2006-09-29
> **ewl1217 said:**
> First, download the installer and open the terminal. Then navigate to the folder you downloaded it to. Let's say that your username is user and you saved it to the desktop. You would type
```
cd /home/user/Desktop
```
Then use the command
```
ls
```
to make sure that the file is actually there. Then run the command
```
wine bwgen31.exe
```
If all goes well, then it should install properly. Then navigate to Wine's fake c drive with (replace user wih your username)
```
cd /home/user/.wine/drive_c
```
Then do some hunting around for the executable with ls and use cd to navigate through the folders. Then run it with the following command:
```
wine program.exe
```
Just replace program.exe with the executable's name. Let us know if you need any help.


Okay, so far I've gotten the thing installed. Now Im just confused about what you said about hunting around for the executable. Would that be in the usr/bin? the usr/lib? Didn't I download the .exe in the first place?

---

### Post by voodoonirvana on 2006-09-29
Ok, how do I get into the "Program Files" using "cd"?

---

### Post by ewl1217 on 2006-09-29
Just input the following command (assuming you're in drive_c):
```
cd Program\ Files
```
Just remember that cd uses the syntax "cd directory_you_want_to_move_to". You'll get used to it. The only exception is with certain characters, such as spaces, which you must put a \ before (like in this example). I probably should have mentioned that earlier...

---

### Post by _duncan_ on 2006-09-29
Guess what? I was going to hunt for a wiki on how to use wine. Then I chanced upon this thread, Tried it on an old vb6 program I wrote years ago. IT WORKED PERFECTLY!

Thank you ewl1217 for sharing your knowledge, and voodoonirvana for starting this thread.

---

