---
title: "Isn't /etc/skel/ be copied automatically in the process of creating a new account"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by henry0712 on 2007-04-14
Hello, When I created a new user account by 'useradd' command, I found that there was the directory of new account. 

I thought the default directory and default startup files for a new account were created automatically. Are they all setup manully, aren't they?

thanks.

---

### Post by PilotJLR on 2007-04-14
Try this:

```

sudo useradd -d /home/newuser -m newuser
sudo passwd newuser

```

where "newuser" is, of course, the new user name.

---

