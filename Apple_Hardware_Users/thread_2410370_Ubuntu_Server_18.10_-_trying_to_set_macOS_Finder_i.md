---
title: "Ubuntu Server 18.10 - trying to set macOS Finder icon via smb.conf and avahi service"
date: 2019-01-14
forum: Apple Hardware Users
---

### Post by nstuyvesant on 2019-01-14
[COLOR=#242729][FONT=Arial]I'm accessing a fresh install of Ubuntu 18.10 and Samba 4.8.4 from macOS clients running Mojave. When connected via SMB, I want the Finder icon to look like a Mac Mini (because that's what Ubuntu 18.10 is running on).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In **/etc/samba/smb.conf** ([global] section), these values for **fruit:model** worked: **Xserve**, **MacPro**, **iMac**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]These resulted in the default icon that looks like an Apple Cinema Display: **MacBook**, **MacMini**, **MacSamba**, **TimeCapsule**, **RackMac**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Saw a post recommending model names from /System/Library/CoreServices/CoreTypes.bundle/Contents/Info.plist on a Mac. While there are many there, the ones I tried didn't work.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Re: avahi-daemon, Samba 4.8.4 can set the icon for connected macOS clients without avahi-daemon running (worked for the three models above). While having avahi-daemon helps the server be perpetually visible in the Finder, I'm trying to understand only the working values for fruit:model in the smb.conf.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Anyone have any insight?[/FONT][/COLOR]

---

