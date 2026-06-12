---
title: "reinstall problems"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-07-14
Hi all! I have done a clean reinstall of dapper.On setting about preferences and appearances etc, I have noticed that I cannot find the file browser icon (filing cabinet) to place in the taskbar panel as I had previously. Simarlarly, Firestarter is not in applications or add/remove. also which I had in the panel. Also previously Ubuntu had mounted (desktop icons) of my other HD and Fat partitions. Ubuntu is on a slave HD and  Windows on Master HD. Any suggestions would be appreciated as to how I can get round these problems!
Thanks
Regards:)

---

### Post by bruce89 on 2006-07-14
> **Sbarton said:**
> Hi all! I have done a clean reinstall of dapper.On setting about preferences and appearances etc, I have noticed that I cannot find the file browser icon (filing cabinet) to place in the taskbar panel as I had previously.

To make the menus cleaner, it was decided to remove some icons from the menu for Dapper.  File browser was one of them.  You can get it back by right clicking on Applications and selecting _E_dit Menus.  Then select Accessories, and tick the checkbox beside *File Browser*.

> **Sbarton said:**
> Simarlarly, Firestarter is not in applications or add/remove.
Firestarter is in Add/Remove applications if you tick "Show unsupported applications".  You can also install it this way: ```
sudo aptitude update && sudo aptitude install firestarter
```
in the terminal.

> **Sbarton said:**
> Also previously Ubuntu had mounted (desktop icons) of my other HD and Fat partitions. Ubuntu is on a slave HD and  Windows on Master HD.
See this - [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by Sbarton on 2006-07-14
Thank so much for your reply! :) 
Regards

---

