---
title: "Windows network SMB urgent plz"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-11-07
i made a shared folder in my ubuntu that can be accessible thru windows desktop, while am trying to access the folder in windows it ask for user name and password, am providing  my login user with the password (also the same sudo password) but it re ask for the username and password ???

---

### Post by ericesque on 2007-11-07
you need to create a user in the SMB group or add your username to that group.  I just ran into this the other day.  Let me see if I can find the thread that helped me.

---

### Post by ericesque on 2007-11-07
This should get you rockin:

Time to add yourself as an samba user.

NOTE: You will be asked for a password - make sure you use the same as you use for login!



```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```

Also, don't forget to grant read/write access to the folder that you are sharing


```
sudo chmod 777 /path/to/shared/folder
```

---

### Post by ericesque on 2007-11-07
oh, I should clearify that your SMB password is a separate credential.  So you don't have to use the same password as you use to login-- that's just for simplicity's sake.

---

### Post by akkad on 2007-11-07
am verryyyyy thankful , simple and totally the desired behavior, i wanted my user to be under SMB not to create new user, thnx worked perfectly

---

### Post by ericesque on 2007-11-07
I have to pat myself on the back for this one.  I think the answer was posted in about 5 min from the original post :)  

*does a little dance*

---

