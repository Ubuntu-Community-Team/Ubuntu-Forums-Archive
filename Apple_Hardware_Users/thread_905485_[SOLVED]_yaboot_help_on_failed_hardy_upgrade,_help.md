---
title: "[SOLVED] yaboot help on failed hardy upgrade, help getting to prompt"
date: 2008-08-30
forum: Apple Hardware Users
---

### Post by Kilz on 2008-08-30
Hi Hi
I feel a little out of my knowledge area so I thought to ask for help.
I help out as the school my daughter goes to by being its it department. :) Since its a school attached to a church we have a low budget and Linux is perfect.
While I have a great deal of knowledge about Ubuntu, sadly I know nothing about running it on a mac. Someone donated a older PPC tray cdrom imac and I was happy to see Xubuntu already installed. Sadly it was Dapper drake. All the other pc's (3 total) run Xubuntu Hardy. The cdrom is broken so I couldn't do a fresh install, and I cant start over. After doing a search I found the fix to getting an upgrade going and let everything upgrade.
On reboot the screen goes white, and then black, and stayed black. I found [a thread that helped a little]("http://ubuntuforums.org/showthread.php?t=749715") when 
```
Linux nosplash video=ofonly
``` is booted it doesnt go immediately black. I can see the loading screen. The loading line goes all the way until the screen usually changes to the login screen then goes black. I have a feeling its a xorg.conf problem. But I have no idea how to get to a command prompt to fix it, or what the fix would be. In grub I would boot into failsafe and the prompt would be there.

Thanks for any suggestions in advance.

First edit.
Ok some progress, so that anyone else running into this knows

```
Linux video=ofonly single
```
Brings up the rescue menu, including a root prompt. Now I am sure its a xorg.conf problem. I also found out that the imac has ati graphics.

Edit 9-14-08 
After I got the xorg.conf working I had to remove the video=ofonly because with it the desktop was slow and had corruption when the windows were moved.

---

