---
title: "shutdown another computer from terminal? (like windows shutdown?)"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-12-07
On my workplace we are setting new computers with Ubuntu installed, but, when we used windows one great advantage we had was turning off some computers from one computer (using shutdown). Is there a way to do this on Bash? (seeing that bash's shutdown has no support for shutting down another computer)?

Oh, and is possible for this to be possible only to users with root access? (sudoers)

---

### Post by Dr Small on 2007-12-07
To shutdown a computer from a remote location (not being on that computer) you will need to have SSH installed, and then SSH to the system you wish to shutdown and then run:
```
shutdown -h now
```

---

### Post by llamakc on 2007-12-07
Yes, you can login in remotely over ssh and run the 'shutdown' command. SSH keys would be good for this sort of situation.

---

### Post by Fixman on 2007-12-07
Can you do this to many computers at the same time? (with a script or something)? I never heared about SSH

---

### Post by bodhi.zazen on 2007-12-07
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

you could try scripting with expect

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

change the ssh to :

```
ssh -fT user@server sudo shutdown -h now
```

give your user the power to shutdown w/o password

---

### Post by Fixman on 2007-12-07
Is possible to do this from linux to windows? I mean, that a compouter with Ubuntu shuts down a computer with Windows XP

---

### Post by Fixman on 2007-12-07
bump

---

### Post by Fixman on 2007-12-07
bump

---

### Post by Dr Small on 2007-12-07
> **Fixman said:**
> Is possible to do this from linux to windows? I mean, that a compouter with Ubuntu shuts down a computer with Windows XP
No, I do not think so, unless it could do it if the system was running OpenSSH-Server, but then the commands would be differnet and all, so I would most assuredly say, No.

---

