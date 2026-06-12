---
title: "Typing sudo"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by queque on 2008-02-02
Hello,

I recently copied a directory file CU from another computer. Below is the output when I type "ls -l". But, I see that it is "root root". So, I need to type in "sudo" everytime I need to make changes. Is there a way to make is "usr usr" just like my other files? Also, why is it "root root". Thank you for your help.

-rw-r--r--  1 usr usr  720 2008-02-02 13:13 tr.txt
dr-xr-xr-x 48 root   root    4096 2008-02-02 13:29 CU
drwxr-xr-x  2 usr usr  4096 2008-02-02 01:50 Desktop
lrwxrwxrwx  1 usr usr    26 2008-02-02 00:52 Examples -> /usr/share/example-content
-rwx------  1 usr usr 13964 2008-02-01 03:58 abc.ods
drwxr-xr-x  3 usr usr  4096 2008-02-02 02:03 wireless

---

### Post by taurus on 2008-02-02
```
sudo chown -R usr:usr CU
sudo chmod -R 755 CU
ls -la 
```

---

### Post by Nythain on 2008-02-02
sudo chown usr:usr filename.whatever
should do the trick

and for teh explanation... its root root more than likely because you used sudo cp to copy, instead of just cp, or you logged in as root via su... moral of teh story, when you copy or mv files, new file gets owned by who did it

---

### Post by queque on 2008-02-02
Oh NICE. Thank you. It worked. Also, I see that some files, which are not executable (ex. .txt files) are colored green (which indicates that their executable permissions are on (-rwxr-xr-x). Does it mean that I can fix this problem by typing:
sudo chmod 644 files_name
to get (-rw-r--r--)?
Also, do I have to perform this "chown" everytime I transfer files from other computers? Thank you again for the help.

---

