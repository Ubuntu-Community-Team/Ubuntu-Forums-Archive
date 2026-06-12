---
title: "SAMBA/Folder Permissions Questions"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by wicked711 on 2007-01-28
Hi Guys,

Have just installed Ubuntu, and trying to implement a file sharing solution for my small office, basically have a few different folders that only certain users/groups can access, note that all these folders are shared under a samba share on the Ubuntu box, eg:

Group1 can access Folder1
Group2 can access Folder2

i have each folder set to chmod 770 respective to their group, ie Group1 owns Folder1 and Group2 owns Folder2.

Samba seems to be working great, i can access the shares from my other Win boxes, and permissions seem to work, i.e a Group1 members can access Folder1 but can't access Folder2.

Here is where i run into problems, Group1 users can still DELETE and RENAME the share Folder belonging to a different Group (i.e Folder2), i can seem to make a workaround for the DELETE issue by having at least 1 file within the folder which seems to prevent non-authorised users to delete the main share folder, but the renaming the folder still works for un-authorised users.

I've got each windows user added as a system user and also added them into the SAMBA userslist via smbpasswd, so authenticating seems OK.

Is there something i'm doing incorrectly? Or another way to implement this?

Another thing i'm curious about is  the "valid users =" field in the smb.conf file, eg:

[Share Files]
path = /home/samba/shared/
comment = Shared folders
read only = No
valid users = user1, user2, user3

I've tried using this field, and when network browsing through as user4 on a Win PC, i can still see the above share, it doesn't seem to have any use?

Cheers for any advice!

---

### Post by Koybe on 2007-01-28
I'm not sure of what you made.

Could you put here the permissions on the two shared folders, and the smb.conf section concerning both?

You can also have a look on acl, if you want to manage permission better. With acl you can give different permissions to different groups.

You need to install acl packet, remount your partiton using acl option. then use the setfacl and getfacl command to set what you need.

I don't know for the valid users option.

---

### Post by wicked711 on 2007-01-28
Thanks for the info, i will look into ACL, sounds like a better way to implement this!

Also i figured out wat the issue was, it simply was that the parent folder of the share had 777 permissions, thus directories under it could be renamed and deleted, DOH!

i.e i had /home/samba as the main share folder, and created individual group folders under that!

One more question i had was that when creating new files/folders in a share, the new file and folder doesn't give write access to the group, i.e only 744 permission , anyway to make any new files/folders created by users to have 770 permission?

Cheers!

---

### Post by Koybe on 2007-01-28
You need to change the default in your smb.conf :
```
create mask = 660
directory mask = 770
```

you can also use 2770 for your directories. So the owner of the new file/folder is the owner of the original folder instead of the principal group of the user.

---

