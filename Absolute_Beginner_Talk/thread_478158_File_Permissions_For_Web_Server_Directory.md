---
title: "File Permissions For Web Server Directory"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by UbuNewbie123 on 2007-06-19
Let's say I have a user on my Ubuntu server called "sam".

I would like to share the folder "/httpdocs/" on my windows network so that I can easily copy and paste files into this folder for my web development work on my windows desktops.

What directory permissions should this folder have to allow only "sam" to have full access while leaving the other default permissions the same?

If I do a chmod on a folder, will the all the sub folders and files in it be changed as well?

---

### Post by Bachstelze on 2007-06-19
No. But you can use the -R switch to *chmod* if you want to change permissions recursively.

As for what the permissions should be, it depends what you want them to be for the other users on the system.

---

### Post by UbuNewbie123 on 2007-06-19
I want "sam" the Ubuntu user account to have all access rights to the folder, which group does he belong to? No one else on my windows server can access this folder unless they know sam's username/password.

---

### Post by Bachstelze on 2007-06-19
Then you should *chown*to sam and *chmod* to 700.

---

### Post by UbuNewbie123 on 2007-06-19
I am assuming owner = sam, the username I created during the installation of Ubuntu Server... I want that permission to a "7".

For group and others, I want them to read and execute but not change any of the files. So I guess that should be a "5".

Therefore, the permissions I should be setting is "755".

---

### Post by UbuNewbie123 on 2007-06-19
IF it is 700, will my apache server still be able to read it? I just know the owner has to be "7". Not sure about the rest.

---

### Post by UbuNewbie123 on 2007-06-19
I played around with the directory permissions and found that 747 worked best. I could access the directory on my windows network and write/edit stuff in it and also view the web pages in the browser. Any comments on this 747 permissions? I wonder if it is secure.

---

