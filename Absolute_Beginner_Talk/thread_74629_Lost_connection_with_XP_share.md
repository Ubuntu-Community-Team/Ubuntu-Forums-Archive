---
title: "Lost connection with XP share"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by bengtfalke on 2005-10-12
I am new to Ubuntu. I installed the Breezy preview 2 weeks ago and everything worked fine. I could use the wireless network here at home and reach the shared folders on the windows XP machines and print on the WiFi enabled HP Photosmart printers.

Then one of the daily updates of Breezy broke something (I think) and now I can not reach the shared folders on the XP machines anymore. I just get a lot of login questions about the domain and nothing more.

Does anybody know what has happened or what I am doing wrong?

Regards/falke

---

### Post by SilentCacophony on 2005-10-12
If you used samba to share, some things you can try:

In gnome, System > Adminsistration > Shared Folders, and make sure the settings are correct. Also, in the properties dialog of any item listed, is a button to set "General Windows sharing settings", in which you can set the wrokgroup and such. I'm using Breezy, so not sure if Hoary has the same settings.

**sudo dpkg-reconfigure samba** might be worth a try, if no luck there.

I've also seen some people have to uninstall and reinstall samba. I don't know if it's necessary in any case though. I'd imagine you'd have to reconfigure it afterwards.

There is a configuration file in /etc/samba/smb.conf you might want to look over, if the gnome front-end is giving you problems.

---

### Post by bengtfalke on 2005-10-12
Thank you mate! That did the trick! But it is a bit strange...... though?

You see at first I just used the default distribution without any configuration and could see and use my XP shared directories. After a week this suddenly stopped working.

Then I installed Samba and started to try to use it without any success. Now, I changed the default user in XP to the same as in Ubuntu and suddenly it worked after reconfiguring Samba after your instructions.

Regards/falke

---

