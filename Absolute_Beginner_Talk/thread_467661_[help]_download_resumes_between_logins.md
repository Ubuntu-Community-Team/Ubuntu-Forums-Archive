---
title: "[help] download resumes between logins"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-07
Hi,

I'm noticing that I can do pause and resume during
downloads in firefox.

Can I do the same between logins/outs?  I'd like to be
able to resume any paused downloads even after I log
out and log in to the system, including system restarts.

I'm using ce 3.2 (christian edition 3.2)

Thanks.

---

### Post by yabbadabbadont on 2007-06-08
I've never trusted that function in firefox myself.  Try it out on some unimportant download and see if it works.  Or you could copy the URL to the file you wish to download and then use the wget command in a terminal window to get the file.  ```
wget http://www.somesite.com/some/file/path/somefile
```  If you need to stop, you can hit control-c to interrupt the download.  To resume it, run (in the same directory as the partially downloaded file): ```
wget --continue http://www.somesite.com/some/file/path/somefile
```

---

### Post by pcandpc on 2007-06-09
Thanks.

Will it (wget) also work in between system starts, though?

---

### Post by Bachstelze on 2007-06-09
Yes. If you like a graphical interface, you can use gwget :

```
sudo apt-get install gwget
```

Tip : the FlashGot extension to Firefox makes it very easy to download files with gwget from Firefox :)

---

