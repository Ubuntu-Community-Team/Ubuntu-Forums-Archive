---
title: "How do I load programs at startup automatically?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Wynne G Oldman on 2007-06-01
Hi, how do I load Evolution (or any other program) at startup automatically?  In XP, I just add it to the startup menu. I''d also like Evolution to start minimized. Can you help?

---

### Post by taurus on 2007-06-01
System -> Preferences -> Sessions -> Startup Programs.

---

### Post by Sethalos on 2007-06-01
I'm an Ubuntu linux noob as well and this puzzled me a bit too.

However, the above directions are correct, the only other thing you need to know is to Add the program.

so: System -> Preferences -> Sessions -> Startup Programs (is the first step)

Then you have to click New, and then in the Command box type in the Applications launch command.

The way I would find it would be to add the app to my launch bar, right click on it, choose properties and then copy and past the "command" into the session command box, and bingo it worked.

Hope this helps a bit.

Seth.

---

### Post by Wynne G Oldman on 2007-06-01
> **Sethalos said:**
> I'm an Ubuntu linux noob as well and this puzzled me a bit too.

However, the above directions are correct, the only other thing you need to know is to Add the program.

so: System -> Preferences -> Sessions -> Startup Programs (is the first step)

Then you have to click New, and then in the Command box type in the Applications launch command.

The way I would find it would be to add the app to my launch bar, right click on it, choose properties and then copy and past the "command" into the session command box, and bingo it worked.

Hope this helps a bit.

Seth.
Thanks. I've got that bit sussed. Is there any way to start a program minimized?

---

### Post by Nekiruhs on 2007-06-01
How do you do it in KDE?
And is it possible to login in automatically with kubuntu?

---

### Post by taurus on 2007-06-01
> **Wynne G Oldman said:**
> Thanks. I've got that bit sussed. Is there any way to start a program minimized?

When you add in the command to start a program, try includinng -iconic.

```
program_name -iconic
```
You should test it from a terminal first to make sure it works before you add it to your Sessions.

---

### Post by JonDubya on 2007-06-01
What about loading it to a certain desktop workspace (#2 instead of #1)?

---

### Post by PmDematagoda on 2007-08-28
Excuse me, does anyone know the commands to start Skype, Azureus, checkgmail and firestarter(At startup)?

Forget it i found them.

Sorry, but i found all of them except one(counted my chickens before they hatched), what's the command for firestarter?

---

### Post by OMNU on 2007-09-01
>>Sorry, but i found all of them except one(counted my chickens before they hatched), what's the command for firestarter?

Hello, I'm also a new Ubuntu user (in fact a new linux user, though I have a little bit experience as an UNIX user). I get the startup command of firestarter by this:

First, start your firestarter from System -> Administration -> Firestarter
Then, open a terminal with Application -> Accessaries -> Terminal 

In the terminal, type:

ps -ef | grep firestarter

and you'll get the command like this:
*myid *     6927     1  0 12:07 ?        00:00:00 gksu /usr/sbin/firestarter
root      6928  6927  0 12:07 ?        00:00:02 /usr/sbin/firestarter
*myid *     7424  6413  0 12:13 pts/0    00:00:00 grep firestarter

and you can cut and paste to include the command "gksu /usr/sbin/firestarter" in startup.

With the same token, you can use the "ps -ef |grep *process_name*" command to get the startup command of other application, although you may need to do a little filtering sometimes.

Hope this help. Enjoy. :)

---

### Post by gunslinger1953 on 2007-09-02
Thanks for the info
I just need an explation of the comand so I know what it is I'm doing
new to linux and its great!

---

### Post by Delkster on 2007-09-02
Actually, you probably don't want the Firestarter user interface to start up automatically. It requires administrator privileges, which by default requires entering a password when running it, which you probably don't want to do every time a little bit after logging in.

You don't need to have the Firestarter user interface running in order to have the firewall enabled either. The network filter (which can do firewalling) is built into the Linux kernel, the core of the operating system, and is practically always enabled in Ubuntu -- the detault rules just are to let everything through. Firestarter is just a way of setting the firewalling rules to the built-in filter. Firestarter comes with a startup script that applies those rules based on how you have configured it in the GUI, and that script is automatically run every time your system boots before you even login.

The only things you need the GUI for are setting the rules and possibly for viewing the events logged by the firewall, and Firestarter doesn't do very much in the way of the latter part anyway.

On the other hand, I have actually seen the firestarter startup script fail. You can check whether it has succesfully run by entering the following command in the terminal:
```
sudo iptables -L -n
```
If you get a long list of filtering rules, the script has run and the firewalling rules have been enabled properly. If you get only the following, then there are no rules and everything gets through:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
If you have configured Firestarter and it still seems that you only get the latter output after a reboot (i.e. the rules have not been applied automatically), post back here and I'll try to figure out how I fixed it on my system.

---

