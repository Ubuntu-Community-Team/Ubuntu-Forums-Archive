---
title: "netbios name"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by bobmorris on 2006-09-11
[From]("http://www.ubuntuforums.org/showthread.php?t=202605&highlight=stormbringer") a forum thread on getting Ubunto to find Windows

"netbios name = YOUR_HOSTNAME

Replace "YOUR_HOSTNAME" with your desired hostname (don't use spaces!). Best pratice would be to use the same name you configured upon installation."

Where do I find this? Not sure what I called it.

My current Ubuntu found a Windows printer on another computer, but can't find any Windows drives on the computer (it's dual boot) or the other computers on my home net or a network drive I just installed.

So, clearly I'm missing something.

No, the drives aren't mounted. This would be where I'd probably start assuming I knew what to do.

---

### Post by jordanmthomas on 2006-09-11
Your hostname can be found by opening up a terminal.
you'll see, for example
```
bobmorris@hostname:~$
```
where hostname is your hostname

As for your other Windows computer, try this on it
Right click on 'My Computer' and go to Properties
One of those tabs (can't remember which one...sorry it's been a while) will have that computer's name in it.
Press Win + r
type
```
\\nameofcomputer
```
and see if you can get to the shares in Windows.

If it works, try this in Ubuntu
Press Alt + F2
type
```
smb://nameofcomputer
```

*NOW, FOR THE WINDOWS DRIVE ON YOUR DUAL BOOT MACHINE*
Try this:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
and look for NTFS



Sorry if that's a little scattered...

---

### Post by David Corrales on 2006-09-11
/etc/samba/smb.conf

---

