---
title: "Can't get administrator privaledges [Resolved]"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by danieltowsey on 2006-12-14
:confused: Hi I am new to this. I installed Ububtu 6.06 LTS duel boot with Xp. After I installed everything and logged in to 'oem' user I made some modifications (added programs in add remove) I created a new user with administrator privaledges then deletted 'oem' user..now when I boot into my new account I find out I don't have administrator privilages. I can't add programs and my users and groups under system/ administrator is gone and so is the add remove...what can I do to get my administrator (root) privaledges working again? Thanks for the help! and MERRY CHRISTMAS TO ALL.....:-D

---

### Post by bapoumba on 2006-12-14
Hi,
how did you delete oem user ?
You should now boot in recovery mode (second line from grub menu), you'll be root !!

```
sudo adduser <your_user> admin
reboot
```

If you ever reinstall ubuntu with the alternate CD in the future :
```
sudo oem-config-prepare
```
will automatically delete oem user and ask for a new user login and password at next reboot ;)

---

### Post by taurus on 2006-12-14
Do you belong to groups adm & admin at all?

```
groups
```

---

### Post by danieltowsey on 2006-12-14
I went into the add user..and after I added my user name I just deletted the oem user

---

### Post by danieltowsey on 2006-12-14
> **taurus said:**
> Do you belong to groups adm & admin at all?

```
groups
```
How do I check for that? but I don't think I do

---

### Post by PotOfVB on 2006-12-14
open terminal program
menu apps.>acc.>terminal
once in terminal type

u*ser@user-desktop:~$***_groups_**
press enter

this will show your groups that you belong to

---

### Post by danieltowsey on 2006-12-14
> **PotOfVB said:**
> open terminal program
menu apps.>acc.>terminal
once in terminal type

u*ser@user-desktop:~$***_group_**
press enter

this will show your groups that you belong to
sorrry I don't know how to do that..I opened a terminal and entered the things u said and it came back..not recognised command..

---

### Post by taurus on 2006-12-14
```
**groups**
```

---

### Post by danieltowsey on 2006-12-14
> **taurus said:**
> ```
**groups**
```
It says...'Daniel Fax Tapes'

---

### Post by PotOfVB on 2006-12-14
sorry for the typo, I edited my last post.
:)

---

### Post by taurus on 2006-12-14
Okay, we went through this before, a few hours ago.  Open a terminal and add user daniel to the end of adm and admin in /etc/group...

```
gksudo gedit /etc/group
```
Save it and see if you are in groups adm & admin again with

```
groups
```

---

### Post by danieltowsey on 2006-12-14
> **taurus said:**
> Okay, we went through this before, a few hours ago.  Open a terminal and add user daniel to the end of adm and admin in /etc/group...

```
gksudo gedit /etc/group
```
Save it and see if you are in groups adm & admin again with

```
groups
```
I did that then it asked me for my password..The reply in the terminal was..

daniel is not in the sudoers file.  This incident will be reported.


.then a error  window popped up..heres what was in it..

Failed to run gpedit '/etc/group/daniel
The underlying authorization mechanism (Sudo) does not allow you to run this program. Contact system administrator

---

### Post by taurus on 2006-12-14
Boot into recovery mode from GRUB menu and at the prompt, type

```
nano -w /etc/group
```
Now, add daniel to the end of adm (near the top) and admin (near the end of the file).  Save it with holding <Ctrl> while pressing x.  Hit the return both times.  Now, see if daniel belongs to groups adm & admin with

```
id daniel
```
If everything is good, reboot with

```
shutdown -r now
```

---

### Post by danieltowsey on 2006-12-14
Thanks I'll try that and i will be back in about a half hour

---

### Post by danieltowsey on 2006-12-14
Hi I tried what you said  when I do id daniel I get
uid=1000(daniel) gid=113(daniel) groups=113(daniel),4(adm),21(fax),26(tape) but that part you explained where you said
"and admin (near the end of the file)" does not make any sense to me..

when I check if my users groups or add remove is there. its still not there

---

### Post by danieltowsey on 2006-12-14
Hi..I posted my problems earlier..but still unable to get my administrator privalidges to work..is there a way to sign in as administrator?..

---

### Post by aysiu on 2006-12-14
This should help you get administrator privileges:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by taurus on 2006-12-14
Yes, by booting into recovery mode!  Your problem started because you didn't follow the instruction on the screen when you installed Ubuntu.  If you picked oem, there was a message saying that after you rebooted, you needed to log in as oem and the password that you picked.  Then at the prompt, ran

```
sudo oem-config-prepare
```
to create an actual account for you to use and delete the oem account...  

And since you decided to create an account by hand and removed the oem by hand, you needed to add yourself to groups adm & admin in /etc/group to use sudo.  And you can do that by booting into recovery mode from GRUB menu and open a text editor and add your username to the end of both **adm** & **admin**!  

```
nano  -w  /etc/group
```
Then save it with <Ctrl>x.

---

### Post by taurus on 2006-12-14
> **danieltowsey said:**
> 
"and admin (near the end of the file)" does not make any sense to me..

What do you mean it doesn't make any sense?  What does it look like?

```
cat /etc/group
```

---

### Post by danieltowsey on 2006-12-14
Thanks for yor help I have it working now..and have a merry christmas

---

### Post by danieltowsey on 2006-12-14
Thanks for your help...i have it working now

---

