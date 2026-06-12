---
title: "Understanding Permissions on Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-14
I have a share folder setup on this machine I am typing on, shared with SAMBA on my windows network.  I created a new username for Samba and shared it with that name over the network.  My windows machines and my other Ubuntu machine can access the share folder fine over the network, but I cannot access it locally.

I setup the folder, ran ```
CHOWN jsamba:jsamba <directory path>
```  My login name to this machine is [COLOR="Blue"]jason.[/COLOR]  The user [COLOR="Blue"]jason[/COLOR] is in the jsamba group on this machine and I can READ the folder fine, but I cannot make changes to it.

I also run into problems on some apps that I run in GNOME when I am logged in as [COLOR="Blue"]jason[/COLOR] ...sometimes they tell me that only [COLOR="Blue"]root[/COLOR] can do what I am trying to do.  One good example is when I try and add my serial # to VMWARE...it tells me that I must be logged in as [COLOR="Blue"]root[/COLOR] to do this.  As I understand it, you cannot login as root to Ubuntu without some changes, and I don't see the need to do that if I can figure out this permissions issue.

Any ideas?

---

### Post by jem7v on 2007-04-14
I can't help you with the SAMBA issue because I don't use it, but I can answer the root question!

It's sorta true that you can't log in as root in Ubuntu, BUT! That's what sudo is for.  Any command prefaced with sudo (or gksu if you're going to run a program with a GUI) is run as though you are root... so presumably, all you'd have to do is run VMWARE with gksu or sudo from a command line or the Run Application dialogue (Alt+F2) instead of starting it from the menu (in order to get it to do what you want it to do).

---

### Post by annda on 2007-04-14
i assume the shared directory is on an ext3 filesystem. check the permissions of the directory (and subdirectories) using
ls -l

make sure your files are writable by group. there's a comprehensive info on permissions here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by kc5hwb on 2007-04-14
> **jem7v said:**
> I can't help you with the SAMBA issue because I don't use it, but I can answer the root question!

It's sorta true that you can't log in as root in Ubuntu, BUT! That's what sudo is for.  Any command prefaced with sudo (or gksu if you're going to run a program with a GUI) is run as though you are root... so presumably, all you'd have to do is run VMWARE with gksu or sudo from a command line or the Run Application dialogue (Alt+F2) instead of starting it from the menu (in order to get it to do what you want it to do).

I run sudo all the time from cmd line, but this program has a screen that is requesting a serial # to be entered.  It isn't something entered from cmd line, its in one of the menus of VMWARE.

---

### Post by kc5hwb on 2007-04-14
Ok, I read thru that link above with the Permissions description and it is quite helpful.  I think I understand it a little better now, however I still don't know why I can't access this one folder.  

ls -l showed this:
drwxr-xr-x 2 jsamba jsamba 4096 2007-04-12 19:05 Samson

I ran this command:
```
sudo chmod ug+rwx /mnt/shares/Samson
```

Then I could access/write/execute to the folder.  However, after I removed the "other" permissions with this command:
```
sudo chmod o-wx /mnt/shares/Samson
```

It won't let me write/execute that folder anymore under the username [COLOR="Blue"]jason[/COLOR]  I double-checked and confirmed that the username [COLOR="Blue"]jason[/COLOR] IS in the jsamba **group**

So if I am in this group, and the current ls -l reads:
```
drwxrwxr-- 2 jsamba jsamba 4096 2007-04-14 14:58 Samson
```

Shouldn't [COLOR="Blue"]jason[/COLOR] be able to write/execute here?

---

### Post by annda on 2007-04-14
yes, you should have write access. check if the files in the directory have the right permissions too. if they don't, the chmod option -R (meaning recursive) should take care of that.

---

### Post by chalex on 2007-04-14
type "id jason" to see the group memberships for the username jason

Also, if you're the only person using this share and the machine isn't on the internet, it would probably be safe enough to chmod o+rwx

Also, make sure the directories above this one have o+x

---

### Post by alexlex on 2007-04-14
actually it is very easy to setup root so that you may log in with it (but not recommended. follow the other posts to see if you can get it working. otherwise i can tell you how to login as root in two simple steps.

---

### Post by kc5hwb on 2007-04-14
> **chalex said:**
> type "id jason" to see the group memberships for the username jason

Also, if you're the only person using this share and the machine isn't on the internet, it would probably be safe enough to chmod o+rwx

Also, make sure the directories above this one have o+x

```
jason@SAMSON:/mnt/shares$ id jason
uid=1000(jason) gid=1000(jason) groups=1000(jason),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin)

```

The directory above this share is..
```
drwxr-xr-x 5 jason jason 4096 2007-04-12 18:52 shares
```

---

### Post by annda on 2007-04-14
so the id command says you are NOT in the jsamba group...

---

### Post by kc5hwb on 2007-04-14
Right....thats how I read it also....HOWEVER, in Gnome, if I go to System-->Administration-->Users & Groups and click on Manage Groups, then go to the JSAMBA group....it shows [COLOR="Blue"]jason[/COLOR] as a member.

So what is the cmd line cmd for adding [COLOR="Blue"]jason[/COLOR] to the jsamba group?

---

### Post by Maestro23 on 2007-04-14
In terminal:

> sudo adduser jason jsamba

---

### Post by kc5hwb on 2007-04-14
Done.

```
root@SAMSON:/mnt/shares# id jason
uid=1000(jason) gid=1000(jason) groups=1000(jason),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1001(jsamba)

```

```
root@SAMSON:/mnt/shares# ls -l
total 12
drwxrwxr-- 2 jsamba jsamba 4096 2007-04-14 14:58 Samson
```

And I still cannot write/execute to this folder.  The only way that it seems to want to let me have full permissions is to make it RWX to the O(other) user.

---

### Post by jem7v on 2007-04-14
> **kc5hwb said:**
> I run sudo all the time from cmd line, but this program has a screen that is requesting a serial # to be entered.  It isn't something entered from cmd line, its in one of the menus of VMWARE.

Right.  What I'm saying is that you'll need to run VMWARE itself with sudo or gksu.  i.e., probably something like "gksu vmware" so that the program starts up with administrative privileges.  Same principle as running a command with sudo... just, you're running the entire Program with sudo.

---

