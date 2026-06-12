---
title: "Restrict Access for User using SCP or SFTP"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dplewis on 2007-04-21
I have an Ubuntu server (6.06) that I use as my file server at home. The server has openssh server installed on it.

My family would like to be able to download family pics. I've installed WinSCP at work, and I'm able to connect to the server. Only problem is when I'm in WinSCP:
[LIST=1]
[*]I'm able to access the root directory (makes sense since I'm the main user). How can I setup an account for my family to only access their home directory and the pictures directory?
[*]I can only use SCP, would sFTP be better?
[/LIST]

Since this is my main file server for home, I want the server to be as secure as possible. Not only from outside attacks, but from my Dad who isn't at all familiar with Linux.

Thanks,
David

---

### Post by rich.bradshaw on 2007-04-22
I think that a user can only modify things in their home file, so he can only read, not write those files. Remember that normally you have to use sudo to modify anything like that.

---

