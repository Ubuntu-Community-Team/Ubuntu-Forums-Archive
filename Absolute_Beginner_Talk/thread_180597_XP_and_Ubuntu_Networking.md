---
title: "XP and Ubuntu Networking"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-22
When I started ubuntu about a week ago there where lots of similar threads, tonight I can't find any!:( 

I'm trying to network my Ubuntu machine to the other 3 XP machines on the network. We run a Workgroup. I have installed Samba and followed the unofficial guide on setting it up. The main problem I have is that the windows machines bring up a login screen whenever they try to access my machine and I have no idea how to get past this. I have created user accounts identical to the computer and user names on the XP machines as I read that this helps somewhere on the forum but to no avail. Yesterday I could still access the windows machines from Ubuntu but it seems that my meddling has worsened the problem. I did backup the samba config file so a fresh start is hopefully not impossible. If anybody can give advice or point me to a usefull thread or url it would be greatly appreciated!

---

### Post by zerhacke on 2006-05-22
It's not covered in many of the Samba tutorials I've seen, so I'll put it here.

Did you add the user to samba using samba's add user utility?

```
smbpasswd -a username
```

Where username is the name of the user you want to add - make the username identical to the general system user you created.  After you input that line it will ask you for a password.  Type it in, hit enter, repeat.  Then try accessing the Samba share from your XP box.

---

### Post by skinnygmg on 2006-05-22
did you give the xp usernames access to any folders using samba "share folder" util?  what are the access rights on the folders your trying to view?

---

### Post by RudolfMDLT on 2006-05-22
Thank you very very very much! :D 

I love it when I struggle for days:confused:  and 1 minute after I post someone solves my problem with a one liner!  Thanks zerhacke! It did the trick!

---

