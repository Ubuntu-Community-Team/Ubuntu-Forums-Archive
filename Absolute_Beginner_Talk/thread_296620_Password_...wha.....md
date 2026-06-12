---
title: "Password ...wha....?"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by source on 2006-11-09
I installed ubuntu today and am very excited to begin my new OS experience. The fast loading times and great interface are perfect and i plan on staying a linux user forever

i have one problem though, I installed ubuntu and can login with my user and password, but when i try to do any sort of system administration control or terminal command , when i type in my password it says incorrect password. Now ive made sure COmpletly that i was typing in the EXACT password i was for system startup and it says its wrong.


does anyone know whats going on?


thanks :)

-source

---

### Post by ner0tic on 2006-11-09
so you type "sudo vi edit.txt"
and when prompted for a password yours doesnt' grant you access?

---

### Post by dannyboy79 on 2006-11-09
no, that doesn't sound right. the only thing i can suggest is to check your sudoers file. so your saying then when you run a command that requires sudo, you enter YOUR password and it says incorrect password? there are many posts regarding people who lose their sudo capabilities, just do a search with these forums and you'll find it right asway. like can't sudo? or sudo passwor

---

### Post by aysiu on 2006-11-09
With what command are you launching these administrative or terminal commands?

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
password:
``` will ask for your user password, but ```
su
password:
cp /etc/apt/sources.list /etc/apt/sources.list.bak
``` will ask for the root password, which is essentially non-existent.

---

### Post by source on 2006-11-09
yes exactly two all  of your posts 

when asked for a password i type but no characters appear on the screen. it is very strange yet i still type my "invisible" password in and wait , and it says wrong pass for all sudo commands i do, i tryed upgrading to   and installing movie codecs. nothings working. btw. my password is kenshin1. if that helps. something to do with having numbers and letter with your pass...idk.

ps- i really dont think anyone would want to hack me lol. i have no programs yet :)

---

### Post by ner0tic on 2006-11-09
you're not going to see any characters when typing in the passwords.

the best thing i can think of off the top of my head is to reboot and select recovery mode from the grub menu and after it loads open a terminal and do this:> usermod -a -G admin username replacing username with your username

---

### Post by codejunkie on 2006-11-09
reboot your computer and at the grub menu choose the recovery mode option when your there it will take you into a temporary root mode  now enter ```
adduser yourusername admin
```this will add your username to the admin group and should let you access system administration options.

---

### Post by dannyboy79 on 2006-11-10
> **source said:**
> yes exactly two all  of your posts 

when asked for a password i type but no characters appear on the screen. it is very strange yet i still type my "invisible" password in and wait , and it says wrong pass for all sudo commands i do, i tryed upgrading to   and installing movie codecs. nothings working. btw. my password is kenshin1. if that helps. something to do with having numbers and letter with your pass...idk.

ps- i really dont think anyone would want to hack me lol. i have no programs yet :)


having numbers ain't the prob, i have way more than just numbers in mine, it's got 5 letters, 7 numbers, and 10 symbols, so that ain't it. As far as the password not showing up, others have explained, it's so that if some1's over your shoulder they can't see what it is. Yeah, you won't be able to do anything that requires admin rights. I beleive the post before mine is correct, but I think that same result can be obtained by adding your username on the line within the /etc/groups file. so it might currently say, 
admin:x:112:
but it needs to say,
admin:x:112:usernamehere
Obviously this weould have to be done from the recovery mode as well and if you were going to do whichever thing was easier, well that would obvisouly be what he suggested from the command line.

---

### Post by CatKiller on 2006-11-10
> **source said:**
> when asked for a password i type but no characters appear on the screen. it is very strange yet i still type my "invisible" password in and **wait** 

This might seem like a really lame question, but are you pressing Enter after you've entered your invisible password? You might want to try that.

(As others have mentioned, your password is supposed to be invisible, so that people peeking over your shoulder can't see how many letter it has)

---

