---
title: "[SOLVED] Problem copying files using OpenSSH and WinSCP"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by mattorama on 2007-09-10
I installed OpenSSH and can log in using WinSCP. But when I try to copy a file from windows to ubuntu, I get a "Permission Denied" error. 

My idea is that I want to be able to copy pictures from my XP box to my ubuntu box which acts as a file server on my local network.

Any help is appreciated!

---

### Post by reckless2k2 on 2007-09-10
the user name you login with must have permissions to copy to the directory you are trying to copy too. if you are a normal user, you will only really be able to copy to their home directory by default.

---

### Post by mattorama on 2007-09-10
In Nautilus, I set the owner of the folder to be "matt".

I then set "Folder Access" to "Create and delete files".

I set the group to be "matt" with "Folder Access" set to "Create and delete files".

I then restarted ubuntu.

Using WinSCP, I then login as "matt".

This still gives me permission denied errors when trying to copy from XP to Ubuntu with WinSCP.

Is there some OpenSSH configuration I need?

Regards,

Matt

---

### Post by bodhi.zazen on 2007-09-10
Sounds odd ...

1. Are you logging in a user "matt" (with winscp ?)

2. Are you trying to copy files to a ntfs partition ?

3. Can you copy files to your home directory ? I assume /home/mat 

4. Can you copy files with scp from the command line (you may need to install cygwin to try this from windows).

---

### Post by mattorama on 2007-09-10
* I am logging in as "matt".

* I am trying to copy files **from** an ntfs partition. (to ext3)

* I can copy files to my home directory (/home/matt).

* Not sure if I can copy files with scp from the command line (you may need to install cygwin to try this from windows). I haven't tried this. 


-Matt

---

### Post by reckless2k2 on 2007-09-10
ok so you can copy to /home/matt using winscp? if so, where is it that you are trying to copy to that you can't? that is the permission issue. 

you don't need the cli way of doing it. winscp has the norton commancer interface though so if you are not drilled into the correct directory at the copy point you will get an error. like if you are trying to copy to / instead of /home/matt or /home instead of /home/matt, then you will have issues.

---

### Post by mattorama on 2007-09-10
Ok, I figured it out.

As I said before...

>In Nautilus, I set the owner of the folder to be "matt".
>
>I then set "Folder Access" to "Create and delete files".
>I set the group to be "matt" with "Folder Access" set to "Create and delete files".

But what I didn't do is set the same permissions for subfolders.
I did check the "Apply permissions to enclosed files" with nautilus but this apparently doesn't do what I thought it did.

When I applied the same permissions to the subfolder it worked.

Do I need to apply the permissions to each folder (owner,group) or can I do it recursively somehow?

Regards,

Matt

---

### Post by reckless2k2 on 2007-09-10
sounds like you are making subfolders in your home directory via sudo. you don't need to do this in your home directory. by using sudo you are giving it elevated permissions and that is the issue. you would only need to create a folder using sudo if it were in another directory where you did not have permissions. 

this is getting into permissions and such where you need stronger command line knowledge which is not very hard to get. you'll use things like:

ls -l : tells you the ownership and such about files in that directory along with permissions
chmod : changing permissions
chown : changing ownership
chgrp : changing group ownership

with the ch commands you can add a -R after the command and that option is recursive. i think that's somewhere in the gui as well but i'm not sure. i actually do all of this from the cli and not sure about the gui. hahaha. geez...now i sound like the guys i use to ask help for....."i don't know about the gui, i do it all at the command line" ....hahaha

---

### Post by mattorama on 2007-09-10
Cool.

 I'll do some reading up on the cli for chown, chgrp, and chmod.

Thanks a lot for your help!

-Matt

---

### Post by reckless2k2 on 2007-09-10
there is a bit in the gui for recursive. right click the folder and go into properties and then permissions. at the bottom it says about apply permissions to enclosed files. i think that might handle folders/directories too under that one. not sure. if not.....cli all the way.

sudo chown -R matt:matt /home/matt/whateverthedirectoryis

---

