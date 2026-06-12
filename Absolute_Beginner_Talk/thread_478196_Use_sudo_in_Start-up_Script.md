---
title: "Use sudo in Start-up Script"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2007-06-19
Hi:

I have this startup script which contains a command that needs to be run as root, which understandably is not working correctly.  I have tried to use fakeroot, but it doesn't work for this command.

So I am wondering: is there some way to run this command properly in this startup script?

Cheers,
LK

---

### Post by hyper_ch on 2007-06-19
Put it into the according runlevels. That should do the job.

---

### Post by Carlos Santiago on 2007-06-19
the boot is performed with root privileges, so you just have to add the script to your boot routines.
For example add it in /etc/rc.local
And you dont need to use sudo.

---

### Post by LordKelvan on 2007-06-19
Hi:

Thanks for the replies:

Santiago - rc.local says it is run at the end of each runlevel, does that mean it will be executed like 6 times?  Is there some other place I can add it so that it runs only once?

hyper_ch - when you say add it to the appropriate runlevels, do you mean I should add a script into one of the /etc/run*.d (where * = 0,1,2,3,4,5,6 or S) folders?  If so, which folder(s) should I add it into?  The command I am trying to execute is "lomoco -m --sms", which configures my Logitech MX518 mouse using the lomoco program.

--LK

---

### Post by Rui Pais on 2007-06-19
> **LordKelvan said:**
> Hi:

Thanks for the replies:

Santiago - rc.local says it is run at the end of each runlevel, does that mean it will be executed like 6 times?  Is there some other place I can add it so that it runs only once?

hyper_ch - when you say add it to the appropriate runlevels, do you mean I should add a script into one of the /etc/run*.d (where * = 0,1,2,3,4,5,6 or S) folders?  If so, which folder(s) should I add it into?  The command I am trying to execute is "lomoco -m --sms", which configures my Logitech MX518 mouse using the lomoco program.

--LK
hi
No, just add lomoco -m --sms before the exit 0 of /etc/rc.local.
It will be run only once at the end of the boot process, and changes will be available to all sessions and all users.

Avoid to manually add something to the run levels... thats why rc.local exist :)

---

### Post by LordKelvan on 2007-06-19
Thanks for clearing that up - I'm gonna go try that.

---

### Post by LordKelvan on 2007-06-24
Hmm, for some reason it didn't appear to work.  What I ended up doing was creating a cron job which runs on start-up, which *seemed* to have done the trick. 

At any rate, thanks for all of your help :)

---

### Post by kevdog on 2007-06-24
Can you post how you did this exactly??

---

### Post by LordKelvan on 2007-06-24
Hi:

You might want to look online to corroborate my method, since I learnt it from some websites as well, but here goes:

1) Open a terminal, then type in 'sudo crontab -e' (without the quotes).  The sudo is important, as that creates this task for root, and not your user account.
2) Enter your password if it asks you for one, then you should be in a terminal-based text editor.
3) For me, I wanted my command to be done at boot-up, so I added a line '@reboot /usr/bin/lomoco -m --sms' (again without the quotes)
4) Then press Ctrl+O to save your changes, and Ctrl+X to exit (I think those are the shortcuts, but you should look along the bottom for the list of shortcuts)

The format is basically '@reboot <your command>' - to be safe I would advise providing the full path to your executable/script/whatever, like in my example.  For further info, google "crontab".

Cheers,
LK

---

