---
title: "[SOLVED] Terminal Command doesnt recognise password"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by andy675 on 2007-08-25
Hi,

I am very new to Ubuntu & the Command Line etc.....I am gradually getting more things operational in Ubuntu, however, I cannot get the terminal window to recognise my password when trying to run a command. The terminal only has my default profile & I am using my passwaord that is applicable on my log in. I have read the forum articles on the terminal window  not showing the password, but I think this is not related.

Could someone please advise if I am doing something wrong, or if I need to follow a different process etc.

Any help would be greatly appreciated.

Thanks

---

### Post by Controlpanel on 2007-08-25
I'm not sure when I type my password I type it, the terminal shows nothing, and then I press enter.

---

### Post by Daveth on 2007-08-25
it is case sensitive so are you sure your typing it the same- no offence!

---

### Post by Magneticgravity on 2007-08-25
With me, when i type in my password on terminal, i see nothing,

You should just simply type it in (making sure of your cases) and hit enter.

---

### Post by rkrug on 2007-08-25
When you run a command in the terminal that requires a password, you are running it as root.

Are you sure you are entering the root password?

And also, when you enter your password it won't show what you type. This is normal.

---

### Post by andy675 on 2007-08-25
Hi,

Thanks for the inial replies. I am aware that the password does not show as you type it and I am aware that it is case sensitive. I know this via trying it several times etc.

I am very unsure re the root system, althouth I have read that root is the main system used re administration etc. I am using the only password that I have with Ubuntu, which is the one I use on the initial log in screen.

I apologise for sounding so new. I am sure it will be something simple I am doing wrong.

Any further advice.

Thanks

---

### Post by jordanmthomas on 2007-08-25
What do you get if you type
```
groups
``` and hit enter?

If you don't see the word admin listed, your account is not allowed to use sudo.

---

### Post by jfinkels on 2007-08-25
What command are you trying to execute?

If it is ```
sudo *whatever*
``` then type in your password.

If it is ```
su
``` then type in the root password.

To set the root password if it is not already set, type:```
sudo passwd
```and type your password when prompted.

Read more about Root & Sudo using the link in my profile.

---

### Post by andy675 on 2007-08-25
Many thanks.

Working ok now.

---

### Post by freebeer on 2007-08-25
When are you being prompted for a password?  After the **sudo somecommand** command that you type?  Or are you following instructions that is asking you to type **su**?  If the latter, Ubuntu uses the **sudo** command, not the **su** command.

---

