---
title: "why i cant log in as root"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by swardfox on 2006-08-24
HI 
  i m realy new to ubuntu, I can not log in as root,and it says the password is wrong and it did not ask me any password for root and i just have one username? can you tell me how log in as root. because some commands do not work if you are not root. ie mount...
 i m having troubles to mount one hard disk..?
thanks
siu

---

### Post by hopstah on 2006-08-24
ubuntu doesn't, by default, give access to the root account, but it does allow you to execute root commands by way of the 'sudo' command.  just preface any command where a root account is needed with sudo.  ex. ```
sudo mount /dev/hd** /target
```

---

### Post by bvali on 2006-08-24
You can't login as root. Instead you need to use sudo in front of all commands in the console and you will be asked for your password: it's your user password. If you want a workaround you can do "sudo passwd" and assign a password for root, therefore you can "su" in the console then. Keep in mind that when you sudo it will still ask for your user password. 
Example:
#sudo command

---

### Post by bodhi.zazen on 2006-08-24
I feel your pain.

Upon installation, Ubuntu sets a root PW for you. You do not get to choose.

The first user you create has full admin privilages, but you must use
```

sudo <command>
```

You can sudo to change the root PW if you want to.

---

### Post by Madpilot on 2006-08-24
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

has the rundown on how Ubuntu has set up admin privs w/ sudo.

You could create a root account, but there really isn't any need to.

---

### Post by professor_chaos on 2006-08-24
Something not mentioned in that link on in previous posts is the use of the following command. 

```
sudo -s
```

this will drop you into a root account for that shell. Useful if you want to do a lot of stuff as root and get tired of typing sudo.

---

### Post by hraposo on 2006-08-24
to login as root:
sudo passwrd root
enter the neew root password
then type: su
root password and you are login as root

---

### Post by hraposo on 2006-08-24
Sorry, the line command is
sudo passwd root

---

### Post by macogw on 2006-08-24
The answer to "why" is that too many people log in as root and don't log back out of it which means any spyware adware crap can install itself no problem, while if you're not logged in as root, the password has to be typed every time something is going to be installed.

---

