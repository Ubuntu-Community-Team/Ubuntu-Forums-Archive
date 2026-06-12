---
title: "[SOLVED] Password help"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by 1scorpio on 2008-04-07
I reciently changed my password and then promptly forgot it (my bad). I have tried to reset from both GRUB and Recovery with no success 

here is what I have done
on boot I have pressed esc then typed c and on prompt typed passwd (usrname) no effect
on boot pressed esc selected recovery and wait for prompt then typed passwd (usrname) next prompt says type new Unix pass and then repeat 
i have done all these but still cant get into synaptic

Help thanks in advance
scorpio

---

### Post by Het Irv on 2008-04-07
You have checked caps lock and all that good stuff correct?  All I can think of at the moment is to try the Recovery again, pressing the keys very slowly and writing down what you typed right after.  I'm not trying to be insulting with this, but I know how bad I can be sometimes.

---

### Post by Oldsoldier2003 on 2008-04-07
Like Het Irv said , then if you still have problems once you log in check the account by typing
```
id <your_username>
```  If your account is not in the admin group you'll have to add it so that you can access synaptic

---

### Post by 1scorpio on 2008-04-07
het irv no insult taken it was my bad as you say I will keep going and writing it down LOL after all Ubuntu is for humans and humans make mistakes
thanks
is there any way to list the passwd from the terminal?

---

### Post by Het Irv on 2008-04-07
Remember that the password you need for Synaptic is not always the same password you use to login.  By default it is the password for the first user created during installation.  Try using your new password to login and the old password to get into Synaptic.

---

### Post by 1scorpio on 2008-04-07
that was the info i needed thanks
old pass worked fine

---

### Post by Het Irv on 2008-04-07
I think the root password can be changed in the users and groups dialog box. 
(Not in Ubuntu right now so I can't give you detailed instructions.)

---

### Post by 1scorpio on 2008-04-07
just tried it I will let you know via forum need to reboot to see if it worked

I use gutsy BTW

---

