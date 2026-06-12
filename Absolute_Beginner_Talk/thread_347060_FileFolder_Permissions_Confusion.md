---
title: "File/Folder Permissions Confusion"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Catsworth on 2007-01-26
Hi Guys,

I'm going round in circles here and I'm hoping that someone can help.

I have a system with two users:

mrCatsworth (the regular user that was set up when Ubuntu first installed)
mrsCatsworth (a new user account I have created)

I have folders set up as follows:

>home
....>mrCatsworth
........>myFiles
........>myMusic
........>myVideos
....>mrsCatsworth
........>herFiles
........>herMusic
........>herVideos

I have set permissions on mrsCatsworth and everthing below it to:

Owner | mrsCatsworth | Create and delete files
Group | users | None
Others | | None

And, as is correct, only mrsCatsworth can see the contents of those files and folders (unless, of course, I sudo or open a root terminal in which case I can see everything).

However.....

I have set permissions on mrCatsworth and everything below it to:

Owner | mrCatsworth | Create and delete files
Group | admin | Create and delete files
Others | | None

There are a couple of problems here.

1: I can't set 'Group' to users, it doesn't even appear in the drop-down list
2: mrsCatsworth can see the sub-folders directly below the mrCatsworth folder but cannot see the contents of those sub-folders.

How do I set the Group on mrCatsworth to 'users' (and do I even need to?).  How do I prevent mrsCatsworth from seeing the contents of the mrCatsworth folder?

I'm basically trying to set up both accounts so that they have their own file storage areas that can't be viewed by the other user (except for any administrator accounts which, I understand, will be able to view anything).

Thanks for the help.

---

### Post by ComplexNumber on 2007-01-26
the reason why the group "users"  doesn't appear is because you haven't created it. go to main menu -> system -< administration -> users and groups.

make it easier for yourself by setting group for mrscatsworth to "mrscatsworth" and setting  group for mrcatsworth to "mrcatsworth". then set the directories(ONLY SET THE FOLDER, NOT EVERYTHING BENEATH IT) /home/mrscatsworth and /home/mrcatsworth to 700 using sudo chmod 700 <directory>

---

### Post by Catsworth on 2007-01-26
Ok, I think I've scragged it somewhat.

I'm getting an error message when I log in complaining that:

$HOME/.dmrc

Is being ignored, this happens for both users.

I assume this is because I've previously rippled the permissions down through the folders and got them wrong somewhere along the line.....

I've now created the two groups that you suggested, and then put the appropriate user into them, is there a command that I can use to sort out the permissions lower down the folder structure as well as sorting out the permissions for the folder itself?

Thanks for your help with this.

---

### Post by Catsworth on 2007-01-26
ok.....

```
 sudo chmod 700 <homeFolder>

```

Resolved the ignored folder thingy :)

---

### Post by Catsworth on 2007-01-26
Ok,it would appear that 

```
sudo chmod 700 <homeFolder>
```

also sorted out the viewing problem as well, and all now seems to be working as it should.

Could I ask one last favour please? 

Would you mind explaining to me why/how that worked so that I know what to look for/do in a similar situation next time?

I know that chmod changes the permission (presumably just at the folder level in this case) but what does 700 do, and how does it affect (if at all) the permissions further down?

Thanks once again for your assistance, it's really appreciated :)

---

### Post by ComplexNumber on 2007-01-26
> is there a command that I can use to sort out the permissions lower down the folder structure as well as sorting out the permissions for the folder itself?yes, just use the same command with the -R option. that means: change permissions recursively. but don't do that.
just change the permissions on each of mrcatsworth and mrscatsworth directory to 750. ie 'sudo chmod 750 /home/mrcatsworth /home/mrscatsworth'. 
then 'sudo chown -R mrcatsworth:mrcatsworth /home/mrcatsworth' and 'sudo chown -R mrscatsworth:mrscatsworth /home/mrscatsworth'

---

### Post by Catsworth on 2007-01-26
Ok, I think I need to stop trying to jump ahead.

700 worked, but I'm guessing 755 would be better?

What's the difference?

Sorry.....I guess I need to learn patience :)

---

### Post by ComplexNumber on 2007-01-26
>  700 worked, but I'm guessing 755 would be better?well, i'm the only user on my system. but for some reason, my home directory folder is set to 755.
if we take 755, we can break it down as follows:
7 = the owner can read, write, and execute
5 = the group can read and execute
5 = all others can  read and execute

for the 5, above, it is calcauted as binary, as follows:

read[COLOR=White]...[/COLOR]write[COLOR=White].....[/COLOR]execute
1[COLOR=White]........[/COLOR]0.[COLOR=White].........[/COLOR]1






now, i would have thought that it was logical to have my home directory as 750, but that seems to be the way that ubuntu has set it up :confused:. maybe if there is more than one user, then the home directories are given permissions 750, but i doubt it.

---

### Post by Catsworth on 2007-01-28
Sorry I've taken a couple of days to get back to you, I haven't got Internet access at home at the moment so I need to keep borrowing my in-laws' access.

Thanks for the explanation above, I think that (as 700 seems to be working ok) I'll leave it as is for now and see how it goes.

I'm having a different problem now, which may or may not be related, I seem to now be missing a whole load of entries under the 'System > Administration >' menu - for example, I no longer have an entry that allows me to edit Users/Accounts.

Could this be because I'm no longer in the Admin group?  Any ideas how I can get this back?

Thanks.

---

### Post by Catsworth on 2007-01-28
Ok, I did:

```
 sudo nano -Bw /etc/group
```

and added myself to the 'admin' group and now everything seems to be working ok again :)

Wonderful thing this Ubuntu, I'm actually starting to like it.

So, just to confirm then.....is 700 ok above, or should I change to 750/755?

Thanks :)

---

### Post by Catsworth on 2007-01-28
Ok, this just keeps getting worse.....

now I count see the Windows partition on this box.

There's a line in /etc/fstab that reads:
```
# /dev/hda1
UUID=22A45277A4524D83 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       1
```

So I'm assuming that's set up ok, I just can't see it on the dekstop, it's not in the 'places' menu and I can't see it if I navigate to 'computer'.....any ideas?

---

### Post by ComplexNumber on 2007-01-28
>  Could this be because I'm no longer in the Admin group?  Any ideas how I can get this back?i was going to say "yes", then i noticed your next post :p. 
btw you can be part of more than 1 groups. for example, there may well be a group called "users" that both you and mrscatsworth can be part of (in addition to other groups), and i think it may well make some admin options easier (i would have thought so, anyway).


> is 700 ok above, or should I change to 750/755?if it works, then yes. also, i would have thought 700 is the more secure of the 2. 
i would change my own home permissions to "700", but i'm terrified of borking my system ;).

---

### Post by Rab22 on 2007-01-28
[B]The permissions (in numerical representation) work in the following manner:
[/B]
Read Access = 4
Write Access = 2
Execute Access = 1

There are three primary permissions that are positional.

Owner/Group/Other

The 'owner' is the user that creates/keeps the files. All those files under your /home/mrCatsworth would belong to Owner/User 'mrCatsworth'. Additionally, those under 'mrsCatsworth' would belong to her and her username would be the 'owner'.

The 'group' is a more broad permission This works for any user (other owners of their own files) that belong to that group. For example, if you had four users (A, B, C, and D) and each belonged to the group "Example", each user could interact with the other user's files that had the proper permissions set for the "Group" permission.

The 'other' permission represents **anyone** else. These are those 'users' who are not the 'owner' nor in the 'group'. For security reasons, this is usually set to '0' so that no other users can ever read or modify your files.
[B]
Now, how to apply the permissions...[/B]

We can customize these settings on both directories (folders) and files (documents). To do this, we give three numbers (Owner, Group, Other in that order). For example if you wanted all three permissions to have read access (Owner to be able to read his/her files, Group to be able to read the files, and **anyone** to be able to read the files) we'd apply the numerical value of '444'. This is because the value 4 represents 'read' and there are three permission settings. 

Well, that's cool, right? But what about Read AND Write (modify)? Well, then we simply add the values together for that permission.

Read = 4 + Write = 2 = 6 (value we need). 

So let's take an example. 

Users:
A
B
C
D

Group:
Example (Users: A, B, C, D)

Other:
E

Here user (owner) A wants to be able to read/modify his file "choices.txt". So, user A changes the permissions on the file to....

```
sudo chmod 600 choices.txt
```

A week later, user B comes up to user A and goes, "Hey, A, I need access to your file 'choices.txt', is there anyway you could give me read access to it?". User A, knowing that the file's contents are not that confidential tells user B, 'Sure, I'll set it right away!". User A, knowing he doesn't want **everyone** to view his file, but wouldn't mind those users in his Groups to see 'em changes the permissions to the following:

```
sudo chmod 640 choices.txt
```

This command allows him to read/write, and allows his groups to 'read'. If he wanted to give the groups write (modify) access as well, he only needed to substitute the '4' for a '6'. NOTE: This gives users B, C, D access to read his file. However, user E (which is an 'other' user) does not get access to read the file.


**Executing? Who needs to do that?**
So, we can now read/edit a document. Then you maybe asking why do we need this last 'Execute' access? Well, that's because some files can be 'executed' to perform a task. I'm not going to cover this topic in depth; but to make a file 'executable' simply add "1" to the permissions. So to make a file readable and executable the numerical representation would be "5". 

The only odd aspect with the executing permission is when it comes to directories (folders). It represents whether or not a user can 'go to' that directory. In all other regards, directory permissions work the same way as files (read means you can list the contents of the folder, write means you can modify the files inside the file, etc).


I hope this clears a few things up for ya. I'm not the best writer and I apologize for any inconsistencies or inaccuraices within this post.

Best of luck,

-Rick

---

### Post by Catsworth on 2007-01-28
> **Rab22 said:**
> [B]The permissions (in numerical representation) work in the following manner:
[/B]
[...]

Best of luck,

-Rick

That's a great explanation, thanks very much for taking the time to post that - I really appreciate it.

---

### Post by Catsworth on 2007-01-28
Ok, still trying to sort the hda1 problem above.

just tried:

```
sudo mount -a
```

and got the following response:

```
mount: special device /dev/disk/by-uuid/22A45277A4524D83 does not exist
```

That can't be good can it.....  :(   That'll be why hda1 isn't mounting/visible I would guess, anybody got any ideas how to solve?

Thanks.

---

### Post by ComplexNumber on 2007-01-28
**catsworth**
fire up your terminal and type 'cd /'. then type 'ls -l'. that will list all the directories at root level. post a printout of the ls -l command.
i'm wondering if the permissions have someone been changed from root downwards.

---

### Post by Catsworth on 2007-01-28
> **ComplexNumber said:**
> **catsworth**
fire up your terminal and type 'cd /'. then type 'ls -l'. that will list all the directories at root level. post a printout of the ls -l command.
i'm wondering if the permissions have someone been changed from root downwards.

Done:

```
total 112
drwxr-xr-x   2 root root  4096 2007-01-16 12:22 bin
drwxr-xr-x   3 root root  4096 2007-01-16 12:25 boot
lrwxrwxrwx   1 root root    11 2007-01-15 15:36 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13540 2007-01-28 15:53 dev
drwxr-xr-x 113 root root  4096 2007-01-28 16:22 etc
drwxr-xr-x   5 root root  4096 2007-01-16 14:57 home
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 initrd
lrwxrwxrwx   1 root root    33 2007-01-15 16:19 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  17 root root  8192 2007-01-26 12:11 lib
drwxr-xr-x   2 root root 49152 2007-01-15 15:35 lost+found
drwxr-xr-x   6 root root  4096 2007-01-28 16:22 media
drwxr-xr-x   2 root root  4096 2006-10-19 23:49 mnt
drwxr-xr-x   6 root root  4096 2007-01-26 18:56 opt
dr-xr-xr-x 110 root root     0 2007-01-28 15:50 proc
drwxr-xr-x  15 root root  4096 2007-01-28 16:53 root
drwxr-xr-x   2 root root  4096 2007-01-26 12:11 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 srv
drwxr-xr-x  11 root root     0 2007-01-28 15:50 sys
drwxrwxrwt  17 root root  4096 2007-01-28 17:10 tmp
drwxr-xr-x  13 root root  4096 2007-01-26 11:31 usr
drwxr-xr-x  15 root root  4096 2006-10-25 14:39 var
lrwxrwxrwx   1 root root    30 2007-01-15 16:19 vmlinuz -> boot/vmlinuz-2.6.17-10-generic

```

---

### Post by Rab22 on 2007-01-28
What's interesting to me is that in your fstab it has a UUID for an NTFS partiition. My /etc/fstab has /dev references for NTFS/FAT and UUID only for ext3.

Does anyone know how the UUIDs work? I've never really quite understood them. Could this be the problem?

I may consider trying 

```
/dev/hda /media/hda1 ntfs  defaults,nls=utf8,umask=007,gid=mrCatsworth,uid=mrCatsworth 0       1

```

But then again, I'm not sure. I've never seen an entry like that for NTFS.

---

### Post by ComplexNumber on 2007-01-28
> **Catsworth said:**
> Done:

```
total 112
drwxr-xr-x   2 root root  4096 2007-01-16 12:22 bin
drwxr-xr-x   3 root root  4096 2007-01-16 12:25 boot
lrwxrwxrwx   1 root root    11 2007-01-15 15:36 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13540 2007-01-28 15:53 dev
drwxr-xr-x 113 root root  4096 2007-01-28 16:22 etc
drwxr-xr-x   5 root root  4096 2007-01-16 14:57 home
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 initrd
lrwxrwxrwx   1 root root    33 2007-01-15 16:19 initrd.img -> boot/initrd.img-2.6.17-10-generic
drwxr-xr-x  17 root root  8192 2007-01-26 12:11 lib
drwxr-xr-x   2 root root 49152 2007-01-15 15:35 lost+found
drwxr-xr-x   6 root root  4096 2007-01-28 16:22 media
drwxr-xr-x   2 root root  4096 2006-10-19 23:49 mnt
drwxr-xr-x   6 root root  4096 2007-01-26 18:56 opt
dr-xr-xr-x 110 root root     0 2007-01-28 15:50 proc
drwxr-xr-x  15 root root  4096 2007-01-28 16:53 root
drwxr-xr-x   2 root root  4096 2007-01-26 12:11 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 14:26 srv
drwxr-xr-x  11 root root     0 2007-01-28 15:50 sys
drwxrwxrwt  17 root root  4096 2007-01-28 17:10 tmp
drwxr-xr-x  13 root root  4096 2007-01-26 11:31 usr
drwxr-xr-x  15 root root  4096 2006-10-25 14:39 var
lrwxrwxrwx   1 root root    30 2007-01-15 16:19 vmlinuz -> boot/vmlinuz-2.6.17-10-generic

```
looks ok. pretty much the same as mine.





**Rab22**
thats not the problem. mines similar, and begins with UUID. i'm confused about this part of his ntfs fstab entry, though:
>  gid=mrCatsworth,uid=mrCatsworth

---

### Post by Catsworth on 2007-01-28
Well, I'm stumped, I've Googled and searched through these Forums and I can't find anything.

I'm going to start a new thread for this with a more descriptive title - hopefulyly I can get somewhere with this :(

---

