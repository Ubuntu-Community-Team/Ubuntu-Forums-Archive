---
title: "Importing XP Thunderbird settings."
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by zaxer on 2005-06-13
Hi guys.

Is there any way I can import all my account settings from my thunderbird in XP to my thunderbird in Ubuntu?

Thanks.

---

### Post by Sniffer on 2005-06-13
Try  to copy data from c:\documents and settings\$USERNAME\application data\mozilla\thunderbird\profiles\$RANDOMLETTERS or something like that to ~/.mozilla-thunderbird/profiles/$RANDOMLETTERS

[B]Sniff.

Ubuntu Paranoid.[/B]

---

### Post by zaxer on 2005-06-13
bash: cd: /home/XXXX/.mozilla-thunderbird/profiles/: Doesnt exist =(

---

### Post by zaxer on 2005-06-13
[QUOTE=zaxer]bash: cd: /home/XXXX/.mozilla-thunderbird/profiles/: Doesnt exist =([/QUOTE]
 I think it wont be any profile until I create one..

---

### Post by zaxer on 2005-06-13
Ive created one.

Now the folder is 

~/.mozilla-thunderbird/vqivpxmq.myUser

Is this the right place to copy data?

---

### Post by jeroevi on 2005-06-13
[QUOTE=zaxer]Ive created one.

Now the folder is 

~/.mozilla-thunderbird/vqivpxmq.myUser

Is this the right place to copy data?[/QUOTE]

You can copy the data in that folder.


Alternatively if you have a dual boot with a FAT partition readable for both OS you can do much better then that:
[list]
[*]boot into windows and move your thunderbird settings to the fat disk: from C:\Documents and Settings\xxxxx\Application Data\Thunderbird\Profiles\xxxx.default to some folder on the fat disk.
[*]change C:\Documents and Settings\xxxxx\Application Data\Thunderbird\profiles.ini: set isRelative to '0' and change the path to your new location.
[*]boot ubuntu and change the ~/.thunderbird/profiles.ini in the same way
[/list] 

You can now use thunderbird from both OS!!

greetz,
Jeroen

---

### Post by zaxer on 2005-06-13
[QUOTE=jeroevi]You can copy the data in that folder.


Alternatively if you have a dual boot with a FAT partition readable for both OS you can do much better then that:
[list]
[*]boot into windows and move your thunderbird settings to the fat disk: from C:\Documents and Settings\xxxxx\Application Data\Thunderbird\Profiles\xxxx.default to some folder on the fat disk.
[*]change C:\Documents and Settings\xxxxx\Application Data\Thunderbird\profiles.ini: set isRelative to '0' and change the path to your new location.
[*]boot ubuntu and change the ~/.thunderbird/profiles.ini in the same way
[/list] 

You can now use thunderbird from both OS!!

greetz,
Jeroen[/QUOTE]
 WooooW

That is sooo great but. Will it make effective the changes I make in one side to the other side?

Thanks Jeroen

---

### Post by jeroevi on 2005-06-13
[QUOTE=zaxer]WooooW

That is sooo great but. Will it make effective the changes I make in one side to the other side?

Thanks Jeroen[/QUOTE]
 yes it does

you will for example see that if you set this up on your windows side and load the profile in linux (by modifying profiles.ini) all your accounts are imported including information on your ISP, SMTP, newsgroup subscribtions, etc

thunderbird uses normal files to store its settings and these files are readable in linux and windows

---

### Post by aysiu on 2005-06-13
[QUOTE=zaxer]bash: cd: /home/XXXX/.mozilla-thunderbird/profiles/: Doesnt exist =([/QUOTE]

I don't think you type in *cd:*. Also, it's not *XXXX*--it's whatever your username is: *cd /home/bob/.mozilla-thunderbird/profiles/* or *cd /home/carol/.mozilla-thunderbird/profiles*. You don't have to do this all from the command-line, either. If you want to see if the folder's there, just browse there and click "Show Hidden Files" (I think it's under the "View" menu).

A weird little quirk. If you install the Debian (Ubuntu?) repositories version of Thunderbird, your hidden profile/settings will be in .mozilla-thunderbird. If you download Thunderbird directly from Mozilla's website, the hidden profile/settings will be in .thunderbird.

---

### Post by zaxer on 2005-06-14
[QUOTE=aysiu]I don't think you type in *cd:*. Also, it's not *XXXX*--it's whatever your username is: *cd /home/bob/.mozilla-thunderbird/profiles/* or *cd /home/carol/.mozilla-thunderbird/profiles*. You don't have to do this all from the command-line, either. If you want to see if the folder's there, just browse there and click "Show Hidden Files" (I think it's under the "View" menu).

A weird little quirk. If you install the Debian (Ubuntu?) repositories version of Thunderbird, your hidden profile/settings will be in .mozilla-thunderbird. If you download Thunderbird directly from Mozilla's website, the hidden profile/settings will be in .thunderbird.[/QUOTE]
 I wrote XXX beacuse I dont want to make public my username as it is my first and last name and dont know what those cd ":" are doing there..

By the way.

After importing my settings from xp to ubuntu through a simple paste o my profile folder whenever I try to write a message it crashes and exits thunderbird.

Any  help about this?

---

