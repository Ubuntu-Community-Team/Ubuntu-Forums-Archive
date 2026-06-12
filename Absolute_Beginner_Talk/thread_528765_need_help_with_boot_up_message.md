---
title: "need help with boot up message"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by esl1885 on 2007-08-18
As of yesterday, I started getting this message when booting up:

User's $HOME.dmrc file is being ignored. This prevents
the default session and language from being saved. File 
shuold be owned by user and have 644 permissions, User's 
$HOME directory must be owned by user and not 
writable by other others.

It has an OK box to click on, then finishes booting. I don't know
what I did to cause this problem, nor how to fix it. When I check the 
properties of the Home folder, the permissions are grayed out
and it says at the bottom that I am not the owner. Properties of my 
users name folder are OK.

Could some one help me to correct this? If it requires the use of the 
terminal, please be specific in directions. 

Thanks,

Sam

---

### Post by taurus on 2007-08-18
Assuming your log in name is **john**, try

```
sudo chmod -R 755 /home/john
sudo chown john:john /home/john/.dmrc
sudo chmod 644 /home/john/.dmrc
sudo shutdown -r now
```
and see if you still get the same error message about /home/john/.dmrc again when you log in.

---

### Post by esl1885 on 2007-08-18
When I get to the second line,sudo chown john:john /home/john/.dmrc, it says;

cannot access /home/john/dmrc  No such file on disc.

And I am using my home name in place of John.

Sam

---

### Post by taurus on 2007-08-18
You need to read my previous reply carefully.  

```
[SIZE="4"][COLOR="Blue"]_Assuming_ your log in name is[/COLOR] **[COLOR="Blue"]john[/COLOR]**[/SIZE]
```
You need to substitute john with your actual log in name.

---

### Post by esl1885 on 2007-08-18
I understand what you said. I just entered some wrong letters I think.
Tried it a second time and it shut down. When it rebooted, I did not get the message. 

Does that fix it, or is there more to do.

Thanks for any help you offer.

Sam

---

### Post by taurus on 2007-08-18
Everything is back to normal again for your machine now.  No need to do anything else.

---

### Post by esl1885 on 2007-08-18
Thanks

---

