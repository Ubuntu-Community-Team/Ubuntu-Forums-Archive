---
title: "vsftpd won't allow uploading"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by quicksilver1234 on 2007-04-22
Hello All.
I have having a frustrating time getting my ftp to work.
I have vsftpd installed.

I cannot upload to the server or make folders. 
However, I can see all the folder structures and download anything from anywhere, all I want.

Two questions
1) How do I turn on the ability for a user account to upload?  What do I  need to know to troubleshoot this problem?

2) I'd like to have a single user account be allowed to FTP and then, only from that user's home dir. Any thoughts on how I set that up?

Thanks

---

### Post by quicksilver1234 on 2007-04-22
I got part of it.:) 
I searched under other keywords and found this....

```
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
```

I uncommented the line and it works.
I had not uncommented it before because it sounded dangerous to allow ANY form of FTP write command.
Why the hell don't they change the documentation to say to "you need this to be able to upload." instead of that other cryptic scary statement.

Any idea on the other question, how to lock out users and only have a single user have access their root dir?

---

### Post by mhansen on 2007-04-22
There are more options available than the ones in the default config file...this will explain it better than I can:

[http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html)


You can also man 5 vsftpd.conf


Regards,
Mike

---

