---
title: "[SOLVED] vmware - no server console"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by matjaz on 2008-01-12
Hi
I have just installed vmware server 2 beta (VMware-server-e.x.p-63231.i386.tar.gz), for the second time, using the tutorial on [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209) .

I installed it for the second time, because the first time i couldn't find vmware server console in system tools section, which does exist and has several entries.

I am running Ubuntu 6.06 i386 on AMD64 semepron 3000+

After my second instalation, the console still isn't there, and if i type 
matjaz@matjaz-desktop:~$ vmware
Try 'man vmware' for more information.
matjaz@matjaz-desktop:~$
matjaz@matjaz-desktop:~$

I have also tried to replace line 10 ... : [http://ubuntu-tutorials.com/2007/11/19/install-vmware-server-20-beta-on-ubuntu-710-gutsy/](http://ubuntu-tutorials.com/2007/11/19/install-vmware-server-20-beta-on-ubuntu-710-gutsy/)
> Because Ubuntu does not use the root user account we also need to setup access for your main user. Replace root with your username on line 10 of: /etc/vmware/hostd/authorization.xml (ACEDataUser).

(That post is intended for Ubuntu 7.10 users)
I fount that link in [http://ubuntuforums.org/showthread.php?t=648476](http://ubuntuforums.org/showthread.php?t=648476)

Well my authorization.xml file:

```
<ConfigRoot>
  <ACEData id="10">
    <ACEDataEntity>ha-folder-root</ACEDataEntity>
    <ACEDataId>10</ACEDataId>
    <ACEDataIsGroup>false</ACEDataIsGroup>
    <ACEDataPropagate>true</ACEDataPropagate>
    <ACEDataRoleId>-1</ACEDataRoleId>
    <ACEDataUser>root</ACEDataUser>
  </ACEData>
  <NextAceId>11</NextAceId>
</ConfigRoot>
```

Even if i i change it ( on line 8 not 10 ) to:
> <ConfigRoot>
  <ACEData id="10">
    <ACEDataEntity>ha-folder-root</ACEDataEntity>
    <ACEDataId>10</ACEDataId>
    <ACEDataIsGroup>false</ACEDataIsGroup>
    <ACEDataPropagate>true</ACEDataPropagate>
    <ACEDataRoleId>-1</ACEDataRoleId>
    <ACEDataUser>matjaz</ACEDataUser>
  </ACEData>
  <NextAceId>11</NextAceId>
</ConfigRoot>

it still doesn't work.

I think i have tried everything i could come up with on my own,
so i am asking you for your suggestions.

And my installation was successfull both times, and so was uninstall.
I am enclosing my second install and uninstall terminal sessions.

I think i have disabled ipv6:
matjaz@matjaz-desktop:~$ ip a | grep inet6
matjaz@matjaz-desktop:~$

And i do have some mods, that probably belong to vmware listed:
matjaz@matjaz-desktop:~$ lsmod | grep vm
vmnet                  44596  15
vmmon                 915980  0
matjaz@matjaz-desktop:~$

If i have mised something i should have done, please point that out.

Thank you for reading this, quite long post.
If you have any suggestions, i would be grateful.

Matjaz

---

### Post by matjaz on 2008-01-12
I wanted to say that i would like to run that console that just isnt where it should be.

---

### Post by matjaz on 2008-01-14
Well, I am back to the first release of VM. 
Perhaps i should give the beta some more time.

---

### Post by damoisture on 2008-01-15
When using VMWare Server 2, there is *no* admin console; everything has been replaced by a web GUI. I forgot where on the web I found that information and how to make it work; I'll do some digging and update here.

---

