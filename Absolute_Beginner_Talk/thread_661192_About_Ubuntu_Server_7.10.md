---
title: "About Ubuntu Server 7.10"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by astafnarotser on 2008-01-07
Hello everyone,

I'm a beginner maybe more novice than a beginner about whole linux and ubuntu family. But when it comes to setting up a server at home, i chose ubuntu 7.10 server with an advise from a friend. 

The thing is, I set it up correctly (i think). During installation i passed the DHCP settings and everything worked great. Until I restart my computer and see that a dos-like screen welcomes me. I managed to log in somehow. But I don't know how to do anything. 

Now some writngs come

     "Ubuntu comes with ABSOLUTELY NO WARRANTY....."   

and a dos-like prompt comes saying:

     "*myloginname*@*computername*:~$"

and right after the dollar sign our cursur lights on and off.

So now how should i proceed? 

Thanks for your patience by now.

---

### Post by PeterJS on 2008-01-07
That's what you get with ubuntu server. A good old fasion bare bores command line prompt. If you want to install a graphical environment run:
```

sudo apt-get install ubuntu-desktop

```

What are you trying to set up?

---

### Post by astafnarotser on 2008-01-08
Thanks PeterJS. 

I did what you said and this is what i get:

"[sudo] password for *loginname*"

i wrote my pass, it worked. Later:

"*loginname* is not in the sudoers file. This incident will be reported.
 *loginname*@*computername*:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory"

And than the prompt comes again. That computer has no connection to internet. Could this be the problem (because it's talking about sending an email)?

---

### Post by Raptor45 on 2008-01-08
If you are unfamiliar with the command line, you may just want to go back and install the desktop version. You'll get a GUI which you may feel more comfortable with.

---

### Post by astafnarotser on 2008-01-08
Will I be able to make my computer a server over a desktop version?

Where can i find the commands like sudo, is there a list somewhere?

---

### Post by PeterJS on 2008-01-08
There are two big differences between desktop and server:

1) What software comes installed by default, the both draw from the same repositories, so the defaults aren't so important as what you can install.

2) The default kernel they use. The desktop befaults to the generic image which has no specific customizations for preformance (hence being the generic image), where as server defaults to the server kernel which is tuned to give prefernce to IO (disk, network, etc) of local application responsiveness. This also can be changed and really doesn't come in to play unless you're under a heavy load.

This is a decent guide to the shell I've seen recommended a couple times. it doesn't have an exhaustive list but is a good start.
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by astafnarotser on 2008-01-09
Thanks. I was a little helpful.

I have another question. When i type something beginning with the *su* command, i'm requested for a password although the system never gave me a chance to create a password before. I tyoed my login password and i get a "su: Authentication failure. Sorry." message.

What am i supposed to do?

---

### Post by PeterJS on 2008-01-09
Use sudo instead. Ubuntu uses sudo instead to run administrative tasks, as it allows finer control of what users can and can't do, and works better to minimize the scope of the privilage escalation.

The password su expects is the root password, which is specifically not set in ubuntu. But if you use sudo the password it wants is your user account password.

---

### Post by astafnarotser on 2008-01-10
Thanks...

---

