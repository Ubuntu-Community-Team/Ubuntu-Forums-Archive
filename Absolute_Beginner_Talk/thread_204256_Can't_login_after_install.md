---
title: "Can't login after install"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by I1I Amnesiac I1I on 2006-06-26
I just installed Ubuntu 6.06 on a very decent computer. The install process seemed to go fine, but when i booted linux for the first time it brings me to a console type login that looks something like this:

Ubuntu 6.06 LTS ubuntu tty1

ubuntu login: _ 


'ubuntu' was the default hostname i used during installation. I've tried typing the user name I installed with ('ken') but that didn't work either. Also, after I type something at the ubuntu login: and then press ENTER, 
it prompts for 
password:_ 
But when I try to type a password, nothing shows up until i press ENTER again. Then i try to type a password and it tells me login incorrect, and repeats the ubuntu login:_ 
 I have not seen any kind of linux GUI since installing, just the unfriendly, black, endless console. I've tried googling and forum diving with no luck thus far. Thanks in advance for any help and let me know if you need more info about my system or the problem.

Also, I can't seem to use any kind of normal linux commands like 'passwd, startx', etc.

---

### Post by uzi09 on 2006-06-26
looks like you installed the server version (which means no gui).

login with the user account you set up during the install (the passwd doesn't show like it normally shows all the astricks in Windows), and run:
```

sudo aptitude install ubuntu-desktop

```

if you're having problems logging in, reboot in recovery mode, at the prompt, type:
```

passwd uzi

```
replace uzi with you're username, and you can set a new passwd

---

### Post by shoot2kill on 2006-06-26
[QUOTE=I1I Amnesiac I1I]
But when I try to type a password, nothing shows up until i press ENTER again. Then i try to type a password and it tells me login incorrect, [/QUOTE]

in ubuntu, when typing your password, nothing will show.. not even ***'s.

just type correct password and press enter.. 

that is for the password error, not sure bout the main error, sorry...

---

### Post by I1I Amnesiac I1I on 2006-06-26
Wow! Thank you for the super fast response! I did install the server version (I was skeptical at the mirror site, but it said if you want to permanently install ubuntu, download these). And your solution did work. It seems as though I might have to download a different iso? I thought 1 CD seemed a little light. thanks again.

---

### Post by shoot2kill on 2006-06-26
even downloading the desktop version of ubuntu, it will fit on 1 CD...

---

### Post by catlett on 2006-06-26
Edit

---

