---
title: "OSX sees Ubuntu, but not connecting"
date: 2008-01-29
forum: Apple Intel Users
---

### Post by edward4130 on 2008-01-29
I have two Ubuntu machines, one a Edgy mediacenter/server and the other a Gutsy workstation.  Both Ubuntu machines can see as well as connect to the OS 10.5 mac but the other way around i can't connect it always says invalid user/pass (OK I know my f'ing pass, so don't ask).  I tried Samba and the shares come up right in the mac filebrowser window, I can even connect to the mediacenter with a vnc remote desktop and do anything But share the files!!!

If anyone has had this issue I would love to find what I have missed, no luck so far everyone says it just works, in my case it just doesn't on either.

-Edward 4130

---

### Post by cyberdork33 on 2008-01-29
> **edward4130 said:**
> I have two Ubuntu machines, one a Edgy mediacenter/server and the other a Gutsy workstation.  Both Ubuntu machines can see as well as connect to the OS 10.5 mac but the other way around i can't connect it always says invalid user/pass (OK I know my f'ing pass, so don't ask).  I tried Samba and the shares come up right in the mac filebrowser window, I can even connect to the mediacenter with a vnc remote desktop and do anything But share the files!!!

If anyone has had this issue I would love to find what I have missed, no luck so far everyone says it just works, in my case it just doesn't on either.

-Edward 4130
Check your smb.conf. The Mac uses strange authentication for some reason. There was a topic discussing something like this not too long ago.
[http://ubuntuforums.org/showthread.php?t=660763](http://ubuntuforums.org/showthread.php?t=660763)

You might also consider something like NFS since you are using two *nix systems and no windows.

---

### Post by edward4130 on 2008-02-19
Here is the thing that was missing.  For some reason it was the breaking point, though Windoze could see and connect to the shares but not the Mac until the "smbfs" was installed.

```
 sudo apt-get install smbfs  
```

that was it, of course editing the config file is needed too but without the smbfs the Mac just won't get to it.  Solved, confused but solved....


-Edward4130

---

