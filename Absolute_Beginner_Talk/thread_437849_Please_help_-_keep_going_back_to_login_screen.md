---
title: "Please help - keep going back to login screen"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by echo15 on 2007-05-09
Hi!

I've been using Ubuntu 6.06 on a backup computer for a month or two now.  Today, I tried to login but kept going back to the login screen.  I enter my username and password, press enter, and then go to a dos screen saying "ubuntu login" and then go back to the login screen.

Can anyone help me solve this?

Thanks!

---

### Post by LaRoza on 2007-05-09
A dos screen? Where did you get that?

Is this installed as a server or a desktop?

Could you successfully log in before?

---

### Post by echo15 on 2007-05-09
after i try to login, the dos screen replaces the login screen. then after a second or two, it goes back to the login screen.

this is installed on a desktop.

never had problems loggin in before today.

---

### Post by LaRoza on 2007-05-09
By dos screen, do you mean command prompt or a dos prompt? DOS is not Linux. (DOS is capitalized because its an acronym, not for emphasis)

Can you start Ubuntu in recovery mode?

What happens when you log in at the command prompt?

Do you get any error messages.

Before logging in, try selecting you session as KDE, or GNOME or whatever you typically use, maybe the default changed.

I has this happen to me last night, but I know why.

---

### Post by ikonia on 2007-05-09
chances are you home directory/partition is full or not accessable so on login it can't access your home dir and kicks you back out to the gdm login.

Check file system permission on /home and /home/$user and that you have space on the file system

---

### Post by echo15 on 2007-05-09
yes, sorry, command prompt.

i tried pressing ctrl+alt+f1 at the login screen and went to the command prompt. i logged in at the prompt and i got in although using command prompts. no desktop for me.

so far, i haven't seen any error message. it seems to be something with loading the desktop?

i also tried selecting the session but nothing seemed to work.

---

### Post by LaRoza on 2007-05-09
Does 

```

startx

```

Work?

---

### Post by slibuntu on 2007-05-09
This happened to me a while ago when my drive was full, a quick bit of command line 'rm'ing did the trick! Is there free space on your drive?

---

### Post by echo15 on 2007-05-09
It was drive space problems! Stupid me! 

Thanks to everyone!  I was able to login again after deleting some files.

---

