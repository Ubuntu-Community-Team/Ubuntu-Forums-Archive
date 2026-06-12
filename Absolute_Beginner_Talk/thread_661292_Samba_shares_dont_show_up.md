---
title: "Samba shares dont show up"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by xitdedragon on 2008-01-07
I feel like a total n00b for asking this, although I am definitely not an experienced Linux user. The problem is that my home desktop is not showing any workgroups in the Network window. I click on Windows Network, but nothing is in it. My ubuntu laptop cant see them either although it can see its own and its shared directory. I uninstalled samba, purged it, reinstalled many times, deleted config files, changed the config file multiple times, but nothing. I really am at a loss as to what to do next. Any help would be greatly appreciated.

---

### Post by spiderbatdad on 2008-01-07
not sure if this will help you, but did you properly set up the windows box? Here's a guide that worked for me.[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by spiderbatdad on 2008-01-07
by the way, there is an error when you get down to setting the permissions in the linux section. where it says mode=770  it should say 1775  in both places. You may not have to worry about the linux side anyway. it's mostly the windows side you're probably needing configured.

---

### Post by xitdedragon on 2008-01-07
Oh. Sorry if I didnt make myself clear before. I was using two Ubuntu computers. One of them (laptop) has Samba working fine. On the desktop though, it can't see any computers, even itself (at least through Network). I dont need to configure anything for it to see itself in the Network section do I?

---

### Post by spiderbatdad on 2008-01-07
not sure. i thought samba was for windows shares. if you check the share options by right clicking on the shared folders from each ubuntu box, maybe selecting nfs will work. That is...change the properties settings to nfs...maybe . good luck.

---

### Post by exile on 2008-01-07
I've personally had a very mediocre experience with the ubuntu/gnome network browser, often it is empty when I was using the shares only a few hours earlier.

I have found that the easiest way was to manually browse a directory first and then (usually) the network samba browser is fine after that.

try "smb://ip-address/share" in the location bar.

if that doesn't work manually, then there is a config error somewhere, check that you are both in the same workgroup and that your perms are setup using smbpasswd etc.

Good luck.

---

### Post by xitdedragon on 2008-01-08
> **exile said:**
> I've personally had a very mediocre experience with the ubuntu/gnome network browser, often it is empty when I was using the shares only a few hours earlier.

I have found that the easiest way was to manually browse a directory first and then (usually) the network samba browser is fine after that.

try "smb://ip-address/share" in the location bar.

if that doesn't work manually, then there is a config error somewhere, check that you are both in the same workgroup and that your perms are setup using smbpasswd etc.

Good luck.
I have tried this over and over and I see nothing. I have changed the config file many times, I have deleted users, added them again, and changed passwords. I can't think of anything else to do. Are there any specific packages I should delete and reinstall. I am running out of options here.

Also, I had Samba working on this computer, but now its not. The only thing I remember changing between then and now is setting up a dyndns, but I got rid of that. Also, I got a new router and installed thrid party firmware on there, but the problem seems to lie in software.

---

### Post by manmohanpv on 2008-01-08
Probably your windows computer may be in a diiferent domain or work group

---

### Post by spiderbatdad on 2008-01-08
> **manmohanpv said:**
> Probably your windows computer may be in a diiferent domain or work group

:lolflag::lolflag:

---

### Post by njparton on 2008-01-08
Use NFS for sharing between linux computers.

Have you installed samba and smbfs on both computers? Is the samba daemon running on both?

Have you got the samba ports blocked in iptables? Are you connecting via a router (port forwarding)?

---

### Post by ukripper on 2008-01-08
check your smb.conf and find out what workgroup you are using in it.

```
sudo gedit /etc/samba/smb.conf
```

Also check permissions for the user, should be  something like 644

and at terminal try setting up smbpassword as mentioned by someone earlier in the post.

```
sudo username smbpasswd -a 
```

---

