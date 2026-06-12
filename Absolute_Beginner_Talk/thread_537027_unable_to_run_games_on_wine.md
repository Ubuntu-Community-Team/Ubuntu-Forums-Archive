---
title: "unable to run games on wine"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-28
hi , i have installed flatout 2 using wine . but when i click its icon , nothing happens , game wont start , 

ok i am getting this error

daman@Ultimate:~$ wine flatout2
wine: could not load L"c:\\windows\\system32\\flatout2.exe": Module not found
daman@Ultimate:~$
__________________

---

### Post by WebSiteGuru on 2007-08-28
> **damansandhu said:**
> hi , i have installed flatout 2 using wine . but when i click its icon , nothing happens , game wont start , 

ok i am getting this error

daman@Ultimate:~$ wine flatout2
wine: could not load L"c:\\windows\\system32\\flatout2.exe": Module not found
daman@Ultimate:~$
__________________

Look at the error, you are trying to run it from Windows\system32 folder.

Try going to the folder and right click and run with wine.

---

### Post by damansandhu on 2007-08-28
when i go to game folder and try to open with it wine , it still wont open.

---

### Post by WebSiteGuru on 2007-08-28
> **damansandhu said:**
> when i go to game folder and try to open with it wine , it still wont open.

Did it give you any other messages? Also check out the Link below my sig Subject: [Stuffs I've learned about Wine]
. It might help you get the game running.

---

### Post by damansandhu on 2007-08-28
nope

---

### Post by WebSiteGuru on 2007-08-28
Looks here!
> **WebSiteGuru said:**
> Also check out the Link below my sig Subject: [Stuffs I've learned about Wine]. It might help you get the game running.

---

### Post by damansandhu on 2007-08-28
yea , i see , but its a little complicated for me , can you write solution here in easy words , 

and i have to sleep , its 11:36 pm , bye man

---

### Post by WebSiteGuru on 2007-08-28
> **damansandhu said:**
> yea , i see , but its a little complicated for me , can you write solution here in easy words , 

and i have to sleep , its 11:36 pm , bye man


Not my thread, But those are the steps you need to do.

Nite Nite, Dont let the bed bugs bite. :D ZZZZZZZzzzzzzzzzzzzzzzzz

---

### Post by Daveth on 2007-08-28
go to the game folder in the .wine folder in your home directory, open a terminal and type 

```
wine flatout2.exe
```

then tell us what happens, or does not.....

---

### Post by damansandhu on 2007-08-28
same thing hapened. 

daman@Ultimate:~$ wine flatout2.exe
wine: could not load L"c:\\windows\\system32\\flatout2.exe": Module not found
daman@Ultimate:~$

---

### Post by Hobo Joe on 2007-08-28
Try running it like this:(I'm just guessing the file tree, you'll have to put in the right one)
```

wine /.wine/drive_c/Program\ Files/Flatout\ 2/flatout2.exe

```

In front of any spaces, you need a backslash, as you can see above. Alternatively, you can put the file/folder around quotes, like /"Program Files"/

---

### Post by splintercellguy on 2007-08-28
You did cd to the folder in ~/.wine amirite? Do:

wine "C:\Path\To\Game.exe" (with quotes)

---

### Post by damansandhu on 2007-09-01
daman@Ultimate:~$ wine /.wine/drive_c/Program Files/Empire Interactive/FlatOut2
wine: cannot find '/.wine/drive_c/Program'
daman@Ultimate:~$

i can run winamp on wine , then why flatout2 is not working?

---

