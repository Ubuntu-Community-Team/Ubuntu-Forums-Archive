---
title: "How to load back up?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-01-31
Hello People,
The normal procedure to make any changes to any file is, first to back it up using the cp command to possibly a file in same directory named file_backup. Now, my question, I have backed and I have done some changes to the original file...but those changes havent worked. So how do I load the backup file back?
Thanks,
Linuxnovice.

---

### Post by munga_bill on 2006-01-31
> The normal procedure to make any changes to any file is, first to back it up using the cp command to possibly a file in same directory named file_backup. Now, my question, I have backed and I have done some changes to the original file...but those changes havent worked. So how do I load the backup file back?
Well, say I had a file called billsbizz, and I made a backup copy of it like this:
```
cp billsbizz billsbizz_bak
```
Then I go and make a mess of the billsbizz file and want to go back to where I started at the time the back-up copy was made, all I need to do is exactly the reverse to restore the file:
```
cp billsbizz_bak billsbizz
```
Isn't Linux wonderful ?   ;)

---

### Post by torf on 2006-01-31
Bah...munga_bill beat me to it so I edited out everything since it's already been stated above (quite nicely :) )

---

### Post by linuxnovice on 2006-02-01
Thankyou very much munga_bill....I realize now that my question was quite dumb :D
Linuxnovice.

---

