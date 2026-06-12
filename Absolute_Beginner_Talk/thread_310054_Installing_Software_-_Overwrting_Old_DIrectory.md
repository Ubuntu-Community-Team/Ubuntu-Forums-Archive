---
title: "Installing Software - Overwrting Old DIrectory?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by dercoss on 2006-11-30
I have downloaded Firefox 2.0 and have used the tar command which has given me a directory called "firefox". I want to copy it into /usr/lib and overwrite the existing firefox directory in that location, but I get a "cannot overwrite directory" when I use the mv command.

Am I doing this wrong in wanting to overwrite the existing installation? If not, how do I manage to overwrite the old version?

dc

---

### Post by dercoss on 2006-11-30
Could I be in trouble because I am using the mv command on a directory and not a file???

If that is the case, how do you move and overwrite a whole directory?

dc

---

### Post by anschelsc on 2006-11-30
no, try 
sudo apt-get update
sudo apt-get install firefox
that should work on Dapper or Edgy

---

### Post by dercoss on 2006-11-30
While what you suggest does seem to work, unfortunately it only updates the existing 1.5 version of Firefox. It doesn't get version 2.0. Is it possible to vary it a bit to do this?

dc

---

### Post by dercoss on 2006-12-01
I've managed to do what I intended by using the file broser (not sure if it's called that in Linux..) to rename the old Firefox installation directory (v1.5) and copying version 2 into the /usr/lib directory using the terminal. I then changed the path on the shortcut icon on desktop and it works fine...

dc

---

### Post by Bachstelze on 2006-12-01
This was not the right thing to do but if it works...

---

