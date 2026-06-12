---
title: "Set Default Group Permissions for a Files in a Folder"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-04-15
Hello,

I have been searching for quite a bit on this topic and can't put my finger on an answer (only have finding resources for samba shares) ... hoping someone can help me find the light!

I want to create a shared folder: /home/shared and allow users of the group "shared" to have read+write access to ALL files in the folder (even the ones they didn't create).

Currently, I can create the folder, create the group, add users to the group, change the group ownership of the folder /home/shared, and allow group members to read all files and write to the directory.  However, I can't figure out how to force the creation of user files in the /home/shared directory to have g+rw permissions.  That is, once a file is created in the directory, no one else in the group can modify it except the user (which defeats the purpose, in this case, of the shared directory).

How do I force all files created in the directory (and sub-directories) to have the correct group and group read+write permissions to allow all members of the group full read+write access ?

Thanks,
Damon

---

### Post by bodhi.zazen on 2007-04-15
I have two suggestions.

1. Is to set your users umask values, but this will affect finel creation system wide and is not quite what you are asking.

2. Try setting the gid bit on the directory.

```
chmod g+s /home/shared
```

Permissions are then set via group rather then owner permissions.

---

### Post by thornomad on 2007-04-15
Hello - thanks for the suggestions.  I agree that setting the umask is not really what I am trying to accomplish.  So, I have been trying to under the "g+s" option but failing.  Here is what I did:

$ sudo mkdir /home/shared
$ sudo chown root:shared /home/shared/
$ sudo chmod g+ws /home/shared/

However, when I go to create my text file, it is still showing only read permissions for the group (though the GROUP id is set correctly).  So, that seems to take care of the group ID issue ... but what about the read+write issue ?  Am I missing something ? 

Thanks!

---

### Post by bodhi.zazen on 2007-04-15
Can you post the output of : ```
ls -l /home | grep shared
```

And may I ask, what file system (is /home/shared on a separate partition)?

---

### Post by thornomad on 2007-04-15
Hi - sorry for the delay in responding ... 

My /home is on its own partition, however, /home/shared is not on a different partition than the other /home folders.

```
drwxrwsr-x 2 root shared 4096 2007-04-15 18:48 shared
```

I am noticing that when I transfer a file via AFP (netatalk) that the group read+write value is set; but if I create a file from the command line, it doesn't happen.

I don't understand.

---

### Post by bodhi.zazen on 2007-04-15
No joy I see.

Since you can get the correct settings, perhaps if you create a file in ~ and then mv ~/file /home/shared ?

Change your primary group from users to shared and set your umask to 002 (or 007) (or change name/ownership of /home/shared to /home/users) ?

My only other thought is to consider chrontab to change permissions periodically ?

---

### Post by thornomad on 2007-04-16
Hi - actually, setting the umask to automatically create files with g+rw probably is a good idea.  Then change my default group to "shared" ... of course, this would leave open the files in my home directory as well ... hmm, let me think about that.  Thanks!

---

### Post by the_it on 2007-06-03
> **thornomad said:**
> Hi - actually, setting the umask to automatically create files with g+rw probably is a good idea.  Then change my default group to "shared" ... of course, this would leave open the files in my home directory as well ... hmm, let me think about that.  Thanks!

yes, you need your umask to have rw for group.  But you should not have to change your primary group to shared.  So long as you create a file in a directory that has g+rwxs permision, it will be created with the same group as the directory.  The permissions allowed for the file's group will be defined in your umask.

So for example, a user named markd, and a user named kanako, both a member of the users group can share rw files using a folder called shared that has rwxrwsr-x permission and is group owned by users.  If their umasks are set to 002, then they will be happy to allow readwrite to all group members of users.

However, since markd's home directory is under groupname markd, and kanako's under groupname kanako, markd cannot access kanako's directory and vice versa.  Hope that helps.  Me, I'm scratching my head because I cant remember which file I edited to change my umask.

---

### Post by bmagyarkuti on 2007-07-10
I have also been trying to share folders locally for months, so this thread was extremely useful for me, thanks :)

Yet, there is a thing that just doesen't seem to work for me:
When creating a new file or copying an old one in the shared folder, it's group is set correctly. However, when I move a file into the folder (using the mv command), it's group is not reset to the shared group.

Any ideas on this?

By the way: You can change your umask settings by editing the ~/.profile file.

---

### Post by bmagyarkuti on 2007-07-12
Anyone with ideas?

---

### Post by csnemes on 2007-07-22
UP! I have the same problem! Anyone?

I am also interested in any other method, that gives the same result...
ftp, sshfs?

thx

---

### Post by rincewind_11 on 2007-11-06
Dunno if this is still active, but here it is --BUMP--
I have a similar setup, but with a user1 and a user2 who share /home/fotos and who are both part of the group 'photo'. To have rwx rights on the folder I used acl (Access Control Lists).
```
sudo aptitude install acl
sudo mount -o remount,acl /home
sudo setfacl -Rm d:g:photo:rwx,g:photo:rwx /home/fotos
sudo vim /etc/fstab
/dev/dm-5       /home   ext3    defaults,acl    0       2 #add acl-option to boot options
:wq
```[LIST]
[*]*'sudo aptitude install acl': Install acl package
[*]*'sudo mount -o remount,acl /home': remount the partition containing the shared folder with the acl-option
[*]*'sudo setfacl -Rm d:g:photo:rwx,g:photo:rwx /home/fotos':[LIST]
[*]with setfacl -m you apply a acl-rule on (modify) the folder (the R is for recursivly)
[*]The next part is the rule : 'd:' means default rule which is applied to new items in the folder; g:photo: means that group 'photo' gets certain permissions, rwx means that  read-write-execute rights have been granted.
[*]the next element (seperated by  "," g:photo:rwx) applies the rule to the already existing files and folders within /home/fotos. this should only be added if there are already files in the folder. If you start an empty folder, you can drop this part and only use 'sudo setfacl -m d:g:photo:rwx /home/fotos'.
[*]/home/fotos: the folder which needs to be shared[/LIST] 
[*]*sudo vim /etc/fstab: you still have to make sure that the partition containing the shared folder gets loaded with the acl-option at next boot[/LIST]You can check the acl-rule with 'getfacl':> getfacl /home/fotos/
# file: home/fotos
# owner: root
# group: photo
user::rwx
group::rwx
group:photo:rwx
mask::rwx
other::r--
default:user::rwx
default:group::rwx
default:group:photo:rwx
default:mask::rwx
default:other::rwx >  ls -al /home/fotos
...
drwxrwxr--+ 2 user2 photo 4096 2007-11-04 21:43 teset
-rwxrwxr--+ 1 user1 user1 317068 2007-11-04 22:47 volledesktop.jpg The "+" indicates that an acl-rule is active. The file 'volledesktop.jpg' has the groupid 'user2' but it still is adjustable (writable) by any user of the 'photo'-group>  getfacl volledesktop.jpg
# file: volledesktop.jpg
# owner: user1
# group: user1
user::rwx
group::rwx
[B] group:photo:rwx
[/B]mask::rwx
other::r-- [http://www.debian-administration.org/users/JulienV/weblog/6](http://www.debian-administration.org/users/JulienV/weblog/6)
[http://techrepublic.com.com/5208-6230-0.html;jsessionid=PtXchT30Wke_lEEmyr?forumID=101&threadID=222734&messageID=2281788](http://techrepublic.com.com/5208-6230-0.html;jsessionid=PtXchT30Wke_lEEmyr?forumID=101&threadID=222734&messageID=2281788)

ps: could anyone tell how to quote/use code on this forum... i can't figure it out :s
edit: thx bodhi.zazen

---

### Post by bodhi.zazen on 2007-11-06
> **rincewind_11 said:**
> ps: could anyone tell how to quote/use code on this forum... i can't figure it out :s

[noparse]```
Block of Code
```

> Quote[/noparse]

---

