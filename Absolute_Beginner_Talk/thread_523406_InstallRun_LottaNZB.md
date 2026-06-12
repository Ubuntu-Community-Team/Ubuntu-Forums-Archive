---
title: "Install/Run LottaNZB"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2007-08-11
[Noob_Question]
So I have HellaNZB working, and I downloaded LottaNZB, but I don't know how to get it running. Where do I put all those files? Any support will be appreciated.
[/Noob_Question]

---

### Post by felicity on 2007-08-11
You can run it from the folder it's in by entering the folder in a terminal and typing ```
./lotta.py
``` 
You might try that first and see if you want to keep it. If you do, you might move the folder somewhere like /opt

---

### Post by AegisTalons on 2007-08-11
So I extracted it from the archive and cd into the folder. I then typed "./lotta.py" I got this as the output:

[email]alex@LIQUIDCOOLED:~/Desktop/LottaNZB-0.0.1a5.tar.bz[/email]2_FILES$ ./lotta.py 
Parsed preferences
HellaNZB preferences parsed
Preferences loaded okay
sh: hellanzb.py: not found
Connected..
Error while getting server status! Maybe hellaNZB has shut down
Traceback (most recent call last):
  File "./lotta.py", line 672, in <module>
    client = GUI()
  File "./lotta.py", line 76, in __init__
    self.getStatus()
  File "./lotta.py", line 345, in getStatus
    if self.mystatus['currently_downloading'] != self.downloadingBuffer:
AttributeError: 'GUI' object has no attribute 'mystatus'

---

### Post by felicity on 2007-08-11
Was hellanzb running when you tried to run lottanzb?

---

### Post by AegisTalons on 2007-08-11
HellaNZB is not running. Any ideas?

---

### Post by felicity on 2007-08-11
It should be running for lottanzb to work correctly. Lottanzb is just a gui for hellanzb.

---

### Post by AegisTalons on 2007-08-11
Well that fixed it, I thought if I ran LottaNZB it would automatically run HellaNZB. Apparrently that is not the case. Thanks again for you help.

---

### Post by felicity on 2007-08-11
No worries, I thought that too the first time I ran it. Have fun :)

---

