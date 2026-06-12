---
title: "backtrack latest r2 need file and directory recovery with full names intact."
date: 2012-03-22
forum: Any Other OS
---

### Post by fiddlebum on 2012-03-22
i have an external backup drive.  it had a folder i deleted within a subfolder i later deleted and i need the foremost folder and the innermost folder recovered with full filenames using release candidate 2
partition has not been erased
and no data has been written to it
its using ext4
ii need all data recovered preferable with same directory and filename structure
i'm broke i cannot offer anyone money for help
its all sorts of precious things that i'd never ordinarily get back
like the only photo i have when i was 18 years old

will donate small wireless-n linux compatible usb dongle for solution if required.  definitely will donate it if solved soon.  

thank you.

---

### Post by winh8r on 2012-03-22
You can use testdisk
```

sudo apt-get install testdisk
```

run in terminal

```
sudo testdisk
```

select the drive/partition where the files are

search

enter P to view files in appropriate directory

deleted files will show up in [COLOR="Red"]red[/COLOR] text

highlight them and hit C to copy to named destination.

more info here :

[http://www.cgsecurity.org/]("http://www.cgsecurity.org/")


Hope this helps.


ps. The info is free, just like the software!!!

---

