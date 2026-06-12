---
title: "XP won't access Ubuntu shared folders"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by jshamash66 on 2006-10-09
Hi, I posted earlier because I wasn't able to browse my Ubuntu computer from  any XP computers on the network (I'm using Samba). I have narrowed down the problem a little bit:

- The XP computer is finding my Ubuntu pc, but when I try to browse it, it says access is denied.
- I don't think it's a firewall problem, since both computers can ping each other.
- My Ubuntu computer has no problem browsing the XP pc.

I think that it might be an authentication problem caused by the username and password I set up, using the 'smbpasswd' command. Does the username/password have to be consistent with the user on my Ubuntu pc? Or should they be the username and password of the user on the XP pc trying to access the shared folders? Or, can it just be any random username and password, that XP computers will have to enter in order to access the shared folders? Even if the username/password is the problem, however, Windows XP isn't even prompting me for one! ](*,) 

If anyone could help me out, it would be greatly appreciated.

---

### Post by jordanmthomas on 2006-10-09
try this:
```
cd /etc/samba
sudo cp smb.conf smb.conf_backup #in case you mess it up
gksu gedit smb.conf

```

At the bottom, set up shares like this (obviously, substituting relevant values)
For read/write...share named upload
```
[upload]
force user = jordan
force group = users
case sensitive = no
guest ok = yes
msdfs proxy = no
read only = no
path = /home/jordan/comments

```
for read only, share named Desktop
```

[Desktop]
force user = jordan
force group = users
case sensitive = no
guest ok = yes
msdfs proxy = no
comment = random grab bag
path = /home/jordan/Desktop

```

Save, close, 

```
sudo /etc/init.d/samba force-reload
sudo /etc/init.d/samba restart

```

Hope this helps somewhat

**edit**  not so sure about what to do with the passwords as I usually just leave mine open
```
man smb.conf
``` should have relevant information, though.

---

### Post by mdecler2 on 2006-10-09
> **jshamash66 said:**
> 
- The XP computer is finding my Ubuntu pc, but when I try to browse it, it says access is denied.


As far as I know, if your Ubuntu system has an ext3 filesystem, and Windows is of course NTFS, then you cannot view any files on your Ubuntu PC from the Windows PC (unless you have SSH setup).

Perhaps I am not understanding your problem, but I faced a simailr issue when I first setup my dual boot Windows XP/Ubuntu PC. I can only read files from the windows partition, and I cannot read anything on the Ubuntu partition when Windows is booted. In fact, Windows does not even recognize that anything is in the second partition.

---

### Post by jordanmthomas on 2006-10-09
Just as Linux can read the NTFS drives on Windows over shares, Windows can read the ext3 drives over samba because it is translated before the other OS reads it.  

(It definitely works, as plenty of Windows computers connect to mine every day without doing anything special)

Oh, and mdecler2, if you want to see your Ubuntu stuff in Windows, check out
[http://fs-driver.org](http://fs-driver.org)
Works flawlessly (or it did a few months ago when I still had Windows installed)

---

### Post by jshamash66 on 2006-10-09
Thanks for the help, but the Ubuntu computer is still "not accessible". My smb.conf file looked pretty much just like yours, except the "force user" and "force group" part.

---

### Post by jordanmthomas on 2006-10-09
hmmm...the force user and force group part is precisely what I had to add to make it work correctly.

Maybe in the ################ MISC ############ section of the thing you should make the option security be share (line 191 of mine)
and the restrict anonymous option below it to no

Then, reload and restart samba again.

Also, some of my shares have these options, not sure if they really matter
```

available = yes
guest ok = yes

```

---

### Post by jshamash66 on 2006-10-09
Hm. I'm already using all those parameters, and still nothing's working. By the way, I'm configuring using SWAT, if that helps.

---

### Post by jordanmthomas on 2006-10-09
I've actually helped all I know how to and I have never used SWAT because I just use a module in kcontrol to manage it.  

It may have something to do with using smbpasswd, but I really don't know.  Sorry :(

Anyone else?

---

