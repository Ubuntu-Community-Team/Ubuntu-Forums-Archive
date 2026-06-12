---
title: "Can FireStarter be started automatically?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-03
I'm running FireStarter under Ubuntu 6.10 (having previously used it with 6.06). I've never been convinced that it starts up when it needs to. When FireStarter is running it places an icon on my menu bar. However, this icon only appears if I actually launch FireStarter manually - at which point, it starts logging intruder alerts.

Is there a way to make FireStarter run automatically - either at boot-up or login, as appropriate?

---

### Post by quercusrobur2002 on 2007-02-03
I think it does run in the background, at least, I can't access other PCs on the wireless network in my house unless I manually disable Firestarter by startimg it up through the Applications menu and then disabling it.

---

### Post by smdeep on 2007-02-03
Hi

It it sets up the firewall. What you run is the front end to the firewall. Firestarter is just a frontend. I am sure there is way to start an app automatically in Gnome. In Kubuntu one just links the apps one wants to run in .kde/Autostart.

---

### Post by John E on 2007-02-03
Thanks guys. It's a pity that it doesn't at least place its icon on the menu bar straight away. Just for my peace of mind though, is there any way to tell (once I'm logged in) whether it's running or not? For example, under Windows I can open the Task Manager where I can see all the running processes. Is there any such equivalent for Ubuntu?

---

### Post by PurplePenguin on 2007-02-03
Starting firestarter does not start your firewall.  Your firewall is running in the background, firestarter is a gui that is used to configure it.

You can add firestarter to your session startup, but it gets annoying.  At any time you can use the terminal to start firestarter, double check that your firewall is up, and close the terminal (and firestarter).  This will not turn off your firewall, unless you choose to close it (that is, by clicking "STOP FIREWALL").

> Just for my peace of mind though, is there any way to tell (once I'm logged in) whether it's running or not? For example, under Windows I can open the Task Manager where I can see all the running processes. Is there any such equivalent for Ubuntu?
Your firewall will be running even when firestarter is not.

---

### Post by Joy on 2007-02-03
Hi,
How make Firestarter start automatically at start up?
 System>Preferances>sessions>Startup progrram>Add Sudo fire starter-star-hidden
Press OK
Cheers.
Joy.

---

### Post by szf on 2007-02-03
> **Joy said:**
> Hi,
How make Firestarter start automatically at start up?
 System>Preferances>sessions>Startup progrram>Add Sudo fire starter-star-hidden
Press OK
Cheers.
Joy.

I've had an *System>Preferences>Sessions* (tab) *Startup Programs* entry of ```
gksudo /usr/sbin/firestarter --start-hidden
``` since coming to Ubuntu last summer.

There is no icon in the notification area when Gnome starts. And, yes, I did configure /etc/sudoers with the NOPASSWD option.

John E. - you may find that you're in the same boat as me when following the 'approved' to-do. Also, Edgy has the System Monitor under *System>Administration* if a Windows-style Task Manager is your thing. Alternately, get adept at *top* in the terminal.

---

### Post by pistcivet on 2007-02-03
Look here:
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

They are using sudo instead of gksudo - don't know if that makes a difference. :)

---

### Post by szf on 2007-02-03
> **pistcivet said:**
> They are using sudo instead of gksudo - don't know if that makes a difference. 
I've tried both and it doesn't.:)

---

### Post by Maestro23 on 2007-02-03
> **szf said:**
> I've tried both and it doesn't.:)

From the website FAQ: [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by olddog58 on 2007-02-03
You can check and see if Firestarter is actually running in the background by opening a Terminal window and typing: sudo /etc/init.d/firestarter status
press ENTER , put in your password.  If Firestarter is running you will see the message *Firestarter is running (from Ubuntu Linux for Non-Geeks by R. Grant)
hope this helps.

---

### Post by szf on 2007-02-03
> **olddog58 said:**
> You can check and see if Firestarter is actually running in the background by opening a Terminal window and typing: sudo /etc/init.d/firestarter status
press ENTER , put in your password.  If Firestarter is running you will see the message *Firestarter is running (from Ubuntu Linux for Non-Geeks by R. Grant)
hope this helps.

Interesting. I use ```
 sudo /etc/firestarter/firestarter.sh status
```Along with the sudoers entry ```
*username* ALL=NOPASSWD: /usr/sbin/firestarter,/etc/firestarter/firestarter.sh
``` (always edit with visudo!), you can skip the password entry step.

---

### Post by John E on 2007-02-03
Thanks guys. This has been enormously helpful. I followed the instructions for launching FireStarter as a normal user but as it happens, I'm getting a strange error message which probably requires support from FireStarter. This is the error message I get when I try to start FireStarter whilst logged in as a normal user:-

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
(firestarter:5660): Gtk-WARNING **: cannot open display: 

I've emailed FireStarter for support but it would be helpful if anyone can interpret that message for me.

---

### Post by the music man on 2007-02-04
I get the same error:
> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:4438): Gtk-WARNING **: cannot open display:  
I have this in /etc/sudoers :
```
username ALL = NOPASSWD: /usr/sbin/firestarter, /etc/firestarter/firestarter.sh, /usr/sbin/gproftpd
```
but gproftpd doesn't seem to work too.
(and yes, i have my username entered in place of 'username')

---

### Post by TheRingmaster on 2007-02-04
The best thing to do is leave it well alone. Your firewall is running as a service in the background. There is no reason, other than tinkering with your firewall policies, to have the GUI open.

My 2 cents.

---

### Post by John E on 2007-02-04
**Ringmaster** - you're probably right, but if I open the System Monitor I can't see anything running that looks like it might be a firewall (not until I launch FireStarter, anyway).

**Music Man** - try emailing [FireStarter Support]("http://www.fs-security.com/contact.php"). I've already sent an email - but if two of us ask the same question, it might speed them up a bit...!

---

### Post by TheRingmaster on 2007-02-04
> **John E said:**
> **Ringmaster** - you're probably right, but if I open the System Monitor I can't see anything running that looks like it might be a firewall (not until I launch FireStarter, anyway).

**Music Man** - try emailing [FireStarter Support]("http://www.fs-security.com/contact.php"). I've already sent an email - but if two of us ask the same question, it might speed them up a bit...!


It is called something different if you are looking for it in the system monitor. I can't tell you what that name might be though, but it is there. Firestarter is just the [GUI]("http://en.wikipedia.org/wiki/Graphical_user_interface").

---

### Post by shareMenaPeace on 2007-02-04
the firewall is iptables -- firestarter is just the gui.

---

### Post by the music man on 2007-02-04
> **John E said:**
> **Music Man** - try emailing [FireStarter Support]("http://www.fs-security.com/contact.php"). I've already sent an email - but if two of us ask the same question, it might speed them up a bit...!

I don't know if emailing Firestarter will help, because other programs i entered in /etc/sudoers also don't work, so i think it's a system-related problem, not caused by Firestarter itself. But maybe i'll try it.

---

### Post by John E on 2007-02-05
> **the music man said:**
> I don't know if emailing Firestarter will help, because other programs i entered in /etc/sudoers also don't work, so i think it's a system-related problem, not caused by Firestarter itself. But maybe i'll try it.Interesting... I hadn't tried anything else. Do they all give a similar message?

---

### Post by r4ik on 2007-02-05
System > Preferences > Sessions, click Startup Programs, Add, type in gksu firestarter, click OK, close Sessions. Log out, log back in.
Should work.

---

### Post by John E on 2007-02-05
**r4ik** - Well done, that does seem to actually work (with 2 minor provisos)

1) I had to remove the line that I added to sudoers (namely **my_user_name ALL = NOPASSWD: /usr/sbin/firestarter**)

2) I discovered that I can't use the **--start-hidden** option.

But at least I now get the icon on my menu bar, which is all I wanted. One more question though... can anyone tell me what is the difference between sudo and gksu? In **r4ik**'s example, gksu firestarter works, whereas sudo firestarter doesn't...:confused:

---

### Post by the music man on 2007-02-05
> **John E said:**
> Interesting... I hadn't tried anything else. Do they all give a similar message?

Yes, they all give:

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(*[command-name]*:*[number]*): Gtk-WARNING **: cannot open display: 
I tried it with Firestarter and gProFTPd.

---

### Post by jcconnor on 2007-02-20
Run this in a terminal:

sudo /etc/init.d/firestarter status

It should say that Firestarter is running.

Also if you run this from a terminal:

dmesg

You should see an entry for iptables (which is the actual firewall - Firestarter is just the front-end)

John

---

### Post by kinematic on 2007-02-21
it doesn't matter if firestarter starts at system startup
firestarter is NOT the firewall,it's a graphical interface to configure iptables.
iptables is the actual firewall and it's always running.

---

### Post by r4e on 2007-03-13
> **John E said:**
> 
2) I discovered that I can't use the **--start-hidden** option.


Just FYI--you can use the **--start-hidden** option:

gksu **"**/usr/sbin/firestarter --start-hidden**"**

I realize that iptables runs all the time, but all the same it is nice to be notified when someone is port scanning your computer, which is why having the GUI running all the time is useful.

Thanks for your help, **r4ik**, on getting the GUI to run automatically at boot.

---

### Post by r4e on 2007-03-13
sorry--double posted

---

### Post by lamalex on 2007-03-13
starting the gui is just wasting system resources, you're better off installing shorewall to configure iptables (<-- the firewall as everyone else has said). IPtables is always running, it is built into the kernel.

---

