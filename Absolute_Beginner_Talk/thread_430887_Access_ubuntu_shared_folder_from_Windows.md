---
title: "Access ubuntu shared folder from Windows?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-05-02
The Windows Xp comp can see the Ubuntu Fiesty samba server on the network, but cannot access it.  It asks for a user name and password (which I don't want it to do).  When I try a user name and password it does not work (or I don't know what to type in).

Do you have any ideas? 
Thanks!

---

### Post by useResa on 2007-05-02
I had good use following [this HowTo]("http://ubuntuforums.org/showthread.php?t=202605") in order to get everything configured correctly.
Maybe it can help you too.

---

### Post by octoberdan on 2007-05-02
and don't forget [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)!

---

### Post by Xarok on 2007-05-02
Hmmm, thanks, it seems like in the guides it talks about setting up accounts, but it's confusing as to whether or not it's necessary or how to do it.

Did you guys ever have this problem or could you access the files right away?

---

### Post by useResa on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/samba/+bug/32067](https://launchpad.net/ubuntu/+source/samba/+bug/32067) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 > **Xarok said:**
> Hmmm, thanks, it seems like in the guides it talks about setting up accounts, but it's confusing as to whether or not it's necessary or how to do it.

Did you guys ever have this problem or could you access the files right away?
No, it did not work out of the box for me either.
The indicated bug is the main cause that you have to register users.
What you could do -- before anything else -- is issue the following command
```
sudo smbpasswd -L -a your_username
```When asked for a password make sure you give the same password as when logging in.

Good luck

---

### Post by misconfiguration on 2007-05-02
how your config file? If you want everyone to browse/write you need to specify that.

#example
; pub
[pub]
; example smb config / pub
comment = Shared DIR
browseable = yes
writable = yes
path = /path/to/your/share/dir
public = yes

I myself like to employ strict rules for ppl on my network, I allow everyone to read but only I can write, I have a custom folder setup for uploading then I distribute the files accordingly. You could also set it up where everyone has their own username//login and they can have access to their "home" dirs remotely. Check your /etc/smb.conf under the ;[public] section make sure that's configured correctly, remember the semicolon = comments so  this is ignored, if you need something to work make sure the semi colon is uncommented.

---

### Post by Xarok on 2007-05-02
> **misconfiguration said:**
> how your config file? If you want everyone to browse/write you need to specify that.

#example
; pub
[pub]
; example smb config / pub
comment = Shared DIR
browseable = yes
writable = yes
path = /path/to/your/share/dir
public = yes

I myself like to employ strict rules for ppl on my network, I allow everyone to read but only I can write, I have a custom folder setup for uploading then I distribute the files accordingly. You could also set it up where everyone has their own username//login and they can have access to their "home" dirs remotely. Check your /etc/smb.conf under the ;[public] section make sure that's configured correctly, remember the semicolon = comments so  this is ignored, if you need something to work make sure the semi colon is uncommented.

Wow, it's kinda retarded that the help for the file sharing GUI front-end says nothing about this and doesn't give options for it.

I find editing config files fun, but for the average who doesn't care and wants to get there work done...will be pissed.

---

### Post by Xarok on 2007-05-02
Well, looking in my conf file I see my shared folder:
```

[share]
path = /home/daniel/share
available = yes
browsable = yes
public = yes
writable = no

```
Shouldn't this work?

---

### Post by useResa on 2007-05-03
_In addition_ to what you have in your configuration file, I additionally have the following statements for the drives I share with windows
> read only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = [COLOR=blue]yourUserName[/COLOR]
force group = [COLOR=blue]yourUserName[/COLOR]
comment = [COLOR=blue]sharedDirComment[/COLOR]
Where you - of course - need to edit the text marked in [COLOR=blue]blue[/COLOR]. ;)
 
Regardless I still think you have to "register" yourself and your password as indicated in my earlier post.

---

### Post by misconfiguration on 2007-05-04
> **Xarok said:**
> Well, looking in my conf file I see my shared folder:
```

[share]
path = /home/daniel/share
available = yes
browsable = yes
public = yes
writable = no

```
Shouldn't this work?

In essence it seems as if that's working flawlessly. All of your users are browsing the share, yes? Since you want to make this public you're gonna want to keep the logins obsolete, yes? You need to change your share DIR to something OTHER than your home folder, I wouldn't recommend letting everyone write to your HOME folder, also I don't think local permissions will allow that either. Create a custom folder somewhere that will allow some chmodding.

mkdir /usr/publicupload

chmod 777 /usr/publicupload

So change your code to this; 

[share]
path = /usr/publicupload
available = yes
browsable = yes
public = yes
writable = [COLOR="Red"]yes[/COLOR]

---

### Post by misconfiguration on 2007-05-10
Yes, no, maybe?

---

