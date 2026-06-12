---
title: "A couple of Questions from a former M$ user"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Bladerunner71 on 2007-05-21
Hello,
I am a real recent convert to Linux.  Began with FC6, then switched to UbuntuStudio about a week ago. So far I ran across this issue:

When surfing the internet, on occasion when I click on a link, it seems as if the x11 resets itself (like it does if I were to hit ctrl-alt-backspace). Is there a way to fix this?

Also, I loaded Houdini Apprentice. To get it running I have to do the following in the terminal:

$ cd /opt/hfs8.2.13
$ source houdini_setup_bash
$ houdini

The problem, I want to make a symbolic link and I read that I have to put 'source houdini_setup_bash' into the .login. How would I do that? I searched high and low and could not find a straight answer to do this. Any help here would be appreciated.

Thanks.
:)

---

### Post by jiminycricket on 2007-05-21
.login...do you mean you want it to run at startup?  You could put it (with the full directory path) in System->Preferences->Sessions.  Or, put it in /etc/init.d/rc.local

I think the link issue is linked to nVidia proprietary drivers.  Do you use the nVidia drivers?

---

### Post by mitch.c on 2007-05-21
> **Bladerunner71 said:**
> When surfing the internet, on occasion when I click on a link, it seems as if the x11 resets itself (like it does if I were to hit ctrl-alt-backspace). Is there a way to fix this?
If you could provide more information, it might help narrow down the problem....
[LIST]
[*]What browser are you using when this happens?
[*]An example of a link that causes the error
[*]The contents of /var/log/Xorg.0.log.old right after the restart.
[/LIST]
> **Bladerunner71 said:**
> Also, I loaded Houdini Apprentice. To get it running I have to do the following in the terminal:

$ cd /opt/hfs8.2.13
$ source houdini_setup_bash
$ houdini

The problem, I want to make a symbolic link and I read that I have to put 'source houdini_setup_bash' into the .login. How would I do that? I searched high and low and could not find a straight answer to do this. Any help here would be appreciated.
You make a symlink like this (assuming the directory you listed above):
```
$ sudo ln -s /opt/hfs8.2.13/houdini /usr/bin/houdini
```
This would put the houdini command in your $PATH so that you could start houdini without changing directories.

As for houdini_setup_bash, your best bet is probably to put the following line in ~/.bashrc
```
source houdini_setup_bash
```

Good Luck!
-- 
Mitch

---

