---
title: "Make Gutsy Gibbon shutdown on login"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by michaeless on 2008-04-17
I want to create a user named 'shutdown' that when logged into will automatically shutdown the system. I have tried putting shutdown and init 0 in the .bashrc file for the user, but that did not work. Any help here?

---

### Post by northern lights on 2008-04-17
How 'bout running shutdown a a cronjob recurring every minute for that user?

Let's call the user "sduser"

Create a file called jobs.txt, for instance. In it add the line 

```
* * * * * shutdown
```

then, run

```
crontab -u sduser jobs.txt
```

Verify with ```
crontab -l
```

Log in as sduser and wait for the next full minute...

---

### Post by quirks on 2008-04-17
First of all: you do know, that you can shutdown your computer from GDM as well? Just click on the icon in the lower left corner.

The reason, why the trick with the .bashrc file does not work, is probably because the user does not have the privileges to use that command. I think you need to be root to do that. I don't know how Gnome does this, however, where you aren't root. By the way, commands that should be run during logon are usually put into the .bash_profile file, not the .bashrc file.

Another reason, why it might not have worked, is that when you logon to the Gnome (i.e., to your graphical system), no bash is started (as far as I know). And thus, the content of your .bashrc (or .bash_profile) is not examined, at all. You could add the command to your startup applications. Go to System -> Preferences -> Sessions. Anyhow, this does not fix the problem with the missing permissions.

quirks

---

### Post by michaeless on 2008-04-17
I was hoping to make it pretty immediate, I wanted a way to shutdown faster than I would be able to if I just logged in as my regular account and chose to shutdown. The reason I want this is because I find that I turn on my computer pretty often and don't really need to. So all it does is sit at the login screen for a while then I have to go on a trip somewhere and I will have to login and then immediately shutdown.

---

### Post by reacocard on 2008-04-17
> **michaeless said:**
> I was hoping to make it pretty immediate, I wanted a way to shutdown faster than I would be able to if I just logged in as my regular account and chose to shutdown. The reason I want this is because I find that I turn on my computer pretty often and don't really need to. So all it does is sit at the login screen for a while then I have to go on a trip somewhere and I will have to login and then immediately shutdown.

the login screen has a shutdown option. in the lower-left of the screen, there's a menu you can pull up that has that option. (alternatively pressing F10 will also bring up the menu.)

---

### Post by spydon on 2008-04-17
> **michaeless said:**
> I was hoping to make it pretty immediate, I wanted a way to shutdown faster than I would be able to if I just logged in as my regular account and chose to shutdown. The reason I want this is because I find that I turn on my computer pretty often and don't really need to. So all it does is sit at the login screen for a while then I have to go on a trip somewhere and I will have to login and then immediately shutdown.

But as quirks said, you can shutdown it from the login screen as well in the lower left corner ^^.

---

### Post by stchman on 2008-04-17
> **michaeless said:**
> I want to create a user named 'shutdown' that when logged into will automatically shutdown the system. I have tried putting shutdown and init 0 in the .bashrc file for the user, but that did not work. Any help here?

Shutting the system down automatically as soon as you login would not be very productive.

---

### Post by michaeless on 2008-04-17
I can't believe I forgot about the options menu on the login screen. I checked it out when I first installed and haven't bothered with it since.

Thanks for the help everyone.

---

