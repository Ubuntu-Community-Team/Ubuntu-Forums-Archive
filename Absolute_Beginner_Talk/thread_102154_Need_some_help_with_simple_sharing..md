---
title: "Need some help with simple sharing."
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Kindred on 2005-12-11
I just wanted to share my home dir with the other user in a group I created (my girlfriend) on the same machine.  

At first I just set the permissions in nautilus for the home dir.  Then when I log on though I get a message:  

"your $HOME/.dmrc file has incorrect permissions and is being ignored. this prevents the default session and language from being saved. File should the be owned by user and have 644 permissions" 

(I have no idea what this means really, I mean what's its problem.. sure I could fix the permissions for this file maybe (?) but I don't want to be doing it with every random file that has a problem)

I also realised that this only set the permissions for the home dir anyway, not all the folders within.  Not much use.

All I want to do is have the home folder and it's directories/files shared fully within the group and by default too so every new file created has the same permissions.  

Could anyone please help me out with this?

---

### Post by AndyCooll on 2005-12-11
I have had this before, and IIRC it is linked to the type of permissions that you may have set for your Home directory (I wish I could remember for sure). I think that your Home Directory must allow 'Group' and 'Others' to have Read and Execute permissions.

I suggest you try a few combinations and see what works

:cool:

---

### Post by AndyCooll on 2005-12-11
Forgot to say...

The reason that your Home directory needs to allow the above permissions (check what they are set up as default) is because all your settings are stored in hidden folders within this directory, so programs obviously need access to it.

To avoid such complications it might therefore be better to set up a "share" folder within your Home directory instead.

:cool:

---

