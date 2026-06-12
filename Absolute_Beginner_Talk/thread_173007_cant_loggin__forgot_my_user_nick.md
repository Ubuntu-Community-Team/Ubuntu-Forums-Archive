---
title: "cant loggin  forgot my user nick"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by pc4fun on 2006-05-09
hi guys !!

sorry to bother u but i forgot my user nick & though i have my password 
i cant loggin  any advise >>>>?????????????

---

### Post by fake123 on 2006-05-09
i am afraid you are going to have to reinstall linux now
have fun

---

### Post by Rinzwind on 2006-05-09
1. You need to boot into safe mode from grub. A bigger topic about this is here: [http://www.ubuntuforums.org/showthread.php?t=133102&highlight=forgotten+password](http://www.ubuntuforums.org/showthread.php?t=133102&highlight=forgotten+password) 
Just read the part about getting to the prompt (since that topic assumes you still know your account name). After that follow these few steps:
2. This will get you into a root-prompt.
3. type **more /etc/passwd**

This will get you a list like this (only showing the last 4 lines:> 
<..>
messagebus: x :104:107::/var/run/dbus:/bin/false
haldaemon: x :108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
gdm: x :105:111:Gnome Display Manager:/var/lib/gdm:/bin/false
hplip: x :106:7:HPLIP system user,,,:/var/run/hplip:/bin/false
GrannyWeatherwax: x :1000:1000:GrannyWeatherwax,,,:/home/GrannyWeatherwax:/bin/bash


The LAST line shows you your username.

5. **passwd {username}**
let's you alter your password.


After that you can reboot and login again.

---

### Post by uzi09 on 2006-05-09
well, i'm not going to put a copy of my passwd list (because hackers actually use this to crack passwords), but the last ones should be the accounts you setup.

good luck

edit: oops, looks like we posted at the same time =\

---

### Post by Rinzwind on 2006-05-09
[QUOTE=uzi09]well, i'm not going to put a copy of my passwd list (because hackers actually use this to crack passwords), but the last ones should be the accounts you setup.

good luck

edit: oops, looks like we posted at the same time =\[/QUOTE]

Hey I changed the name in passwd into a random name  ;)

---

### Post by erniewinner on 2006-05-09
8) make sure you put passwords in a safe place next time ... i was forever losing my bits of paper with passwords on. i tried an old pda (loses data when battery runs out.) and an old personal data bank (i can't get it to do lower case letters! i don't think it does them.) so now i use an old mac i had laying around unused... i would have left them on the computer i use but i thought they could get nicked like that and it's easy to remember where they are now, as i use more than one computer...
after you boot up next time use auto login??? (macos x) 

is it really a reinstall job? :-k

---

### Post by Rinzwind on 2006-05-09
[QUOTE=erniewinner]8) make sure you put passwords in a safe place next time ... i was forever losing my bits of paper with passwords on. i tried an old pda (loses data when battery runs out.) and an old personal data bank (i can't get it to do lower case letters! i don't think it does them.) so now i use an old mac i had laying around unused... i would have left them on the computer i use but i thought they could get nicked like that and it's easy to remember where they are now, as i use more than one computer...
after you boot up next time use auto login??? (macos x) 

is it really a reinstall job? :-k[/QUOTE]

I store my passwords ('encrypted') on the web (google mail). As long as 1 of my 4 PC's can get on the web I'm fine. OR else I need to get them from my work computer.

---

