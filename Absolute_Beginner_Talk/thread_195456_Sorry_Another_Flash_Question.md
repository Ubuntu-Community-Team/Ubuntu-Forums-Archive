---
title: "Sorry Another Flash Question"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Chef Stephen on 2006-06-12
Well I have been playing with the last and now current relaeses of Ubuntu for about a month now, but a couple of days ago I was required to get serious when my XP box crapped out. Not very upseting but, now the wife and kid are forced to use the linux box (until I get them a new XP box) but I have a flash problem.

When I first went on Firefox I needed to load the Flashplayer plugin; I clicked on the load plgin icon and poof, no problem I have flash. Well now that my wife and kid are using my linux I set up user accounts for them, no problem but when they log in and use firefox they keep getting messages that the Flash Plugin is not installed. They log out and I log back in and Flash is there working fine.

I tried the same installation under their logins as I did originally under mine, but the installation failed. It gave me an option to manually install the plugin. Since the plugin already exists I thought this might be why the second installation failed...not to mention if that is what I neeed to do I don;t know how. 

Is there somewhere I need to set permissions for things like Flash or have I missed something else completely? Thanks in advance for your help, I am sure this won't be my last question.

---

### Post by u.b.u.n.t.u on 2006-06-12
It sounds like the flash installed only for your user account and not globally.

Have you customised Firefox? If so, does it revert to the default when different users are logged in?

Copying over your profile for Firefox may be one solution but obviously not the best.

---

### Post by uzi09 on 2006-06-12
that's one thing, the other is when you created the other users, you need to ensure that they're in the following groups:
dialout 
cdrom 
floppy 
audio 
dip 
video 
plugdev 
lpadmin 
scanner

that way they'll have access to everything (except admin stuff).
also, when you installed flash, how did you do it? if you did it through apt, then it should have automatically put it in a universal directory.

---

### Post by Chef Stephen on 2006-06-12
There is no customisation, I only copied in some bookmarks.

[QUOTE=uzi09]that's one thing, the other is when you created the other users, you need to ensure that they're in the following groups:
dialout 
cdrom 
floppy 
audio 
dip 
video 
plugdev 
lpadmin 
scanner

that way they'll have access to everything (except admin stuff).
also, when you installed flash, how did you do it? if you did it through apt, then it should have automatically put it in a universal directory.[/QUOTE]

I installed flash by clicking on the install plugin icon on the first page I loaded that needed it. It worked just great (for me that is).

OK, went to the users and groups but I can't see where I check if the other users are in the right groups. 

Again thenks for the help and patience.

---

### Post by uzi09 on 2006-06-12
should be able to see in the users & groups menu.
[http://ubuntuforums.org/attachment.php?attachmentid=10758&d=1149644422](http://ubuntuforums.org/attachment.php?attachmentid=10758&d=1149644422)

but if you installed it that way, i really think the problem was that you didn't install it in a shared directory for everyone to be allowed access. see this guide to reinstall it properly:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by Chef Stephen on 2006-06-12
[QUOTE=uzi09]should be able to see in the users & groups menu.
[http://ubuntuforums.org/attachment.php?attachmentid=10758&d=1149644422](http://ubuntuforums.org/attachment.php?attachmentid=10758&d=1149644422)

but if you installed it that way, i really think the problem was that you didn't install it in a shared directory for everyone to be allowed access. see this guide to reinstall it properly:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)[/QUOTE]

[QUOTE=uzi09]that's one thing, the other is when you created the other users, you need to ensure that they're in the following groups:
dialout 
cdrom 
floppy 
audio 
dip 
video 
plugdev 
lpadmin 
scanner

that way they'll have access to everything (except admin stuff).
also, when you installed flash, how did you do it? if you did it through apt, then it should have automatically put it in a universal directory.[/QUOTE]

I can find the "User Privliges" in Users and Groups is that the same as what groups a user is in?

I will try reinstalling Flash using those instructions and report back, thanks.

---

