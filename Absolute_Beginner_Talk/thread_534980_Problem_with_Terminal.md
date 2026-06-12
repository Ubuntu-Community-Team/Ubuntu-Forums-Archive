---
title: "Problem with Terminal"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Ioosef on 2007-08-25
I'm trying to install [this]("http://java.com/en/download/help/5000010500.xml#selfextracting"), but when I enter the terminal and type 'su' and then type my password this appears:
> 
su: Authentication failure
Sorry.


I don't understand what's going, on, I've tiped my password at least three types and it just won't take it.
Could anyone tell me if they know what may be wrong?
And now I'm kinda scared to log out because perhaps I won't be able to log in again or something.

---

### Post by AceofSpades19 on 2007-08-25
in ubuntu its sudo
so it would be
sudo <command here>
su isn't enabled my default

---

### Post by rkrug on 2007-08-25
When you run a command with su make sure you are entering the root password and not your own.

---

### Post by MS-DOS4 on 2007-08-25
yes I have this same problem. But nothing seems to be working.

---

### Post by asmoore82 on 2007-08-25
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

^^This will explain the Ubuntu Way. Being an already competent Linux user,
I really didn't like it at first; but now I say "Another layer of security... Why Not??"

---

### Post by thefowlstar on 2007-08-25
BTW, to enable the root account, on the terminal type in ```
sudo passwd
``` and then type in your password. You can then enter a password for root. This password should now work using su. I'm not sure if this was in the link above, so sorry if you already knew this.

Hope this helps! :]

---

### Post by ticklecricket on 2007-08-26
You need to run "sudo su" 

I know it's confusing but it has to do with the difference between being the root user and being a user with root access. the "sudo" command allows a user to run a program as if they were the root user. But "su" is a way for the root user to login. However Ubuntu default configures the root user to have a randomly generated password. It's confusing but it's more secure.

Whether you understood or not, you just need to run "sudo su" and enter *your* password. to leave the root terminal just type "exit" or close the window

---

### Post by mcduck on 2007-08-26
Actually it's better to use 'sudo -i' instead of 'sudo su', as 'sudo -i' loads root's environment correctly while 'sudo su' doesn't.

---

### Post by aysiu on 2007-08-26
Here's how to install Java:

**Step 1**
Close the terminal

**Step 2**
Go to Applications > Add/Remove

**Step 3**
Under *Show* (Top-right corner), select *All available applications*

**Step 4**
In the search box, type *java*

**Step 5**
Select *Sun Java 6 Web Start*

That's it.

---

### Post by logos34 on 2007-08-26
> **mcduck said:**
> Actually it's better to use 'sudo -i' instead of 'sudo su', as 'sudo -i' loads root's environment correctly while 'sudo su' doesn't.

that's what I've seen too, 'sudo -i' is the recommended method

---

