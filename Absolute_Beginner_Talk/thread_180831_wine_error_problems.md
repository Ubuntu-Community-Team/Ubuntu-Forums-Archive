---
title: "wine error problems"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by seb4131 on 2006-05-23
Hello,
         I was wondering if anyone can help me i was running winecfg and think i have made a big mistake anything i try to resolve the problem like adding drive auto detecting and typing wineprefixcreate after a onscreen tip but this hasn't fixed the problem here is the readout after i run winecfg

shaunn@c210-49-251-83:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0

any help would be greatly appreciated as i dont know what i have done wrong
thankyou in advance

---

### Post by Ecthelion on 2006-05-23
It looks like you have a permission problem...

If you try
```
sudo chmod 755 /home/**username**/.wine/c/windows/
```
EDIT: Also do
```
sudo chmod 755 /home/**username**/.wine/c/windows/system32/
```

it might solve the problem.
Maybe it would be even better to make it recursive, but DON'T if your problem is solved by that first line. Making something recursive is just adding an 
-R
But be carefull 1 wrong recursive argument can mess up your whole system (I've had a hard time learing that)

Recursive is:
```
sudo chmod 755 -R /home/**username**/.wine/c/windows/
```

---

### Post by Ecthelion on 2006-05-23
Another easier solution is to run winecfg with root rights...
But I think to recall that no-one sould run **wine** with root permissions...
Does anyone else know if you may run **winecfg** with root permissions?

That would make it much easier.
The code is
```
sudo wincfg
```
But don't do it unless someone else says you may do it.

---

### Post by Swatje on 2006-05-27
[QUOTE=Ecthelion]Another easier solution is to run winecfg with root rights...
But I think to recall that no-one sould run **wine** with root permissions...
Does anyone else know if you may run **winecfg** with root permissions?

That would make it much easier.
The code is
```
sudo wincfg
```
But don't do it unless someone else says you may do it.[/QUOTE]

That's a very bad idea, because the you create new files with root rights, that you can't change as user anymore...
The best thing is to delete the wine dir or change the permitions on the wine directory.

Change permitions:
```
sudo chown -R $USERNAME ~/.wine
sudo chmod -R o+w  ~/.wine
```

or delete (you will lose the old wine settings):
```
sudo rm -R ~/.wine 
```

and then run winecfg again.

---

