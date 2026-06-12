---
title: "[SOLVED] How do I copy files off of a remote system to my home pc?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by chaoswings on 2007-09-13
Here's the deal my school makes me use "telnet <address here>" which I type in the terminal

So I connect fine to the school's system. what I want to know is what is the command to copy files off of the remote system to my home pc and vice versa?

cp 1basics ~

doesn't work it copies the file to the home directory on the school's server I want to download it to my pc at home

how do I do that?

Thank you in advance

---

### Post by mustali on 2007-09-13
telnet does not allow file transfers.

To download files, you can try using ftp <address here> and log in using your normal login and password. If an ftp server is running on the remote computer and is accepting user connections, you should be able to login through ftp.

After connecting through ftp, most likely you will be in your home directory on the remote machine. use the 'get' command to download the file.```

get filename
```

to upload a file:
```
put filename
```

HTH

---

### Post by chaoswings on 2007-09-13
That worked thank you

---

