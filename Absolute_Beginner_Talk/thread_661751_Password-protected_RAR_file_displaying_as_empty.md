---
title: "Password-protected RAR file displaying as empty"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by GepettoBR on 2008-01-08
I downloaded a password-protected RAR file via Azureus. I have the password. However, when I double-click it, Archive Manager does not prompt me with a password and shows an empty window, as if there were nothing in the archive. Likewise, when I click "Extract Here" from the right-click menu, it creates an empty folder. Xarchiver says "Archive format not recognized" and desn't even open the file.The file is 92.5MB in size, so even if it's corrupted it's not empty. 

Going Edit>Password in Archive Manager also doesn't work. I enter the password and click OK, no error is displayed, but the file is still treated as empty.

It also failed using the terminal
```
paulo@dragonfly:~$ cd ~/Downloads
paulo@dragonfly:~/Downloads$ unrar -p Andre Rieu - Live In New York 2007.rar

Enter password (will not be echoed): 

Reenter password: 


ERROR: Unknown option: paulo@dragonfly:~/Downloads$ 
paulo@dragonfly:~/Downloads$ 
```

Any ideas?

---

### Post by mali2297 on 2008-01-08
> **GepettoBR said:**
> 
```
paulo@dragonfly:~$ cd ~/Downloads
paulo@dragonfly:~/Downloads$ unrar -p Andre Rieu - Live In New York 2007.rar


Try
[CODE]
unrar e "Andre Rieu - Live In New York 2007.rar"

```
Note the double-quotes.

---

### Post by GepettoBR on 2008-01-08
> **mali2297 said:**
> Try
```

unrar e "Andre Rieu - Live In New York 2007.rar"

```
Note the double-quotes.

Different problem now: ```
paulo@dragonfly:~/Downloads$ unrar e "Andre Rieu - Live In New York 2007.rar"

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Andre Rieu - Live In New York 2007.rar is not RAR archive
No files to extract
```

Does that mean it's corrupted?

---

