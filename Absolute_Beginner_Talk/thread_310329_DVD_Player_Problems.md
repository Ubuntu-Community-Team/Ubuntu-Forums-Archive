---
title: "DVD Player Problems"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by serpente on 2006-12-01
Hi I'm new at this and my DVD Drive won't play I already went into Sys->Pref->Removable Drives and Media and changed the default to VLC Player. However that made no difference as VLC wasn't playing it so I looked online and one of the forums mentioned that a link needed to be created between /dev/hdc and /dev/dvd. Using:

sudo ln -sf /dev/hdc /dev/dvd

I did that and it made no difference so thinking I had the gist of it I tried:

 sudo ln -sf /media/cdrom /dev/hdc

Which now won't let me eject my disc when I press the button on my drive. When I initially did that a message popped up saying that I should have ejected my disc before doing that... so then I:

 sudo ln -sf /dev/hdc /media/cdrom

which lead to the message:

ln: creating symbolic link `/media/cdrom/hdc' to `/dev/hdc': Read-only file system

Does any one know how to fix it so a) the DVD will eject again when I press the button and b) how to get the DVD to play on my laptop.

Suffice it to say I should probably not be allowed around laptops or any forms of technology. And I should probably definitely not be playing around in terminal until I know what I'm doing. But if you can help me I'll be eternally greatful in a non-creepy way?

Thanks

---

### Post by Scorpuk on 2006-12-01
Have you installed the correct codecs for playing DVD's?


If not have a look here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

