---
title: "KDE error"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Imsati on 2007-03-24
Stupid question...While trying to show my Root and Home drives in Konqueror, I went into System Settings and opened up Disk and Filesystems to try to see if there was anything I could do there. When I went into Admin Mode, I got these messages as a possible reason: "An error occured during your last KDe upgrade leaving an orphaned control module." and "You have old third party modules lying around.". I checked my KDE version and it shows it as 3.5.5 (before was 3.5.2). I then went into Adept and did a search for KDE and it shows everything uninstalled. Do I need to install all those KDE packages? Will that make any difference? I'm starting to think that maybe I have a bad Alt-Install CD or maybe a bad HDD. Nothing but problems since I switched over to Sata.

---

### Post by aysiu on 2007-03-25
Can you try pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo apt-get update && sudo apt-get install --reinstall kdebase
``` If that doesn't fix the problem, post back whatever error messages you get.

---

### Post by Imsati on 2007-03-25
That seemed to work. Now I can see the disk info, but when I try to open up the Admin tab, nothing happens. I can click the tab and the border turns red, but none of the information is displayed and I'm not prompted for a password.

---

### Post by aysiu on 2007-03-25
Can you post the output of this command? ```
kdesu kcontrol
```

---

### Post by sinclac on 2007-03-25
Hello,

I have been having problems with mine so i did what you said and this is what i got

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


What might be my problem?

---

### Post by aysiu on 2007-03-25
Believe it or not, most of those "errors" are normal.

These, however, are not normal: ```
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
``` I'm not sure how to fix that, though. Maybe edit the appropriate file and try to change the *Type* from *Link* to *Application*? ```
sudo nano -B /usr/share/applications/DefaultPlugins.desktop
``` should allow you to edit that file while also creating a backup. When you're done, just press Control-X, Y, and Enter.

---

### Post by sinclac on 2007-03-25
It's not saving the edit when i reload the file it still says link

---

### Post by aysiu on 2007-03-25
Are you saying you're not allowed to save changes to the file?

Or are you saying you could save changes to the file, but when you try ```
kdesu kcontrol
``` the file has mysteriously reverted back to Link?

---

### Post by sinclac on 2007-03-25
It's not saving the changes.

---

### Post by aysiu on 2007-03-25
And you definitely did *sudo nano* and not just *nano*?

If you did, we might have to boot into recovery mode for this to work, as *kdesu* seems to be busted.

---

### Post by sinclac on 2007-03-25
Yes i cut and pasted your command, I think i will do a complete reinstall, i am missing a bunch of stuff for KDE and i want to change the partitions on my HD

---

### Post by Imsati on 2007-03-25
Well, back from work now and my how my thread has grown! This is my result from 'kdesu kcontrol':

(First, just 'kdesu...')
: user not authorized to run the X server, aborting.
jason@JasonK:~$   Major opcode:  147
bash: Major: command not found
jason@JasonK:~$   Minor opcode:  3
bash: Minor: command not found
jason@JasonK:~$   Resource id:  0x0
bash: Resource: command not found
jason@JasonK:~$ Failed to open device
bash: Failed: command not found
jason@JasonK:~$ X Error: BadDevice, invalid or uninitialized input device 169
X: user not authorized to run the X server, aborting.
jason@JasonK:~$   Major opcode:  147
bash: Major: command not found
jason@JasonK:~$   Minor opcode:  3
bash: Minor: command not found
jason@JasonK:~$   Resource id:  0x0
bash: Resource: command not found
jason@JasonK:~$ Failed to open device
bash: Failed: command not found
jason@JasonK:~$ Xlib: connection to ":0.0" refused by server
bash: Xlib:: command not found
jason@JasonK:~$ Xlib: No protocol specified
bash: Xlib:: command not found

(Second, using 'sudo kdesu...)
jason@JasonK:~$ sudo kdesu kcontrol
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
kdeinit: Launched DCOPServer, pid = 4756 result = 0
DCOP: register 'anonymous-4756' -> number of clients is now 1
kdeinit: Launched KLauncher, pid = 4760 result = 0
DCOP: unregister 'anonymous-4756'
DCOP: register 'klauncher' -> number of clients is now 1
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
DCOP: new daemon klauncher
DCOP: register 'kded' -> number of clients is now 1
DCOP: unregister 'kded'
kdeinit: Launched KDED, pid = 4761 result = 0
DCOP: register 'kded' -> number of clients is now 1
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP: register 'anonymous-4761' -> number of clients is now 2
DCOP aborting call from 'anonymous-4761' to 'kded'
DCOP: unregister 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
DCOP: unregister 'anonymous-4761'
kdeinit: PID 4761 terminated.
DCOP: register 'kcontrol' -> number of clients is now 1
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
DCOP: unregister 'kcontrol'
DCOP: register 'anonymous-4751' -> number of clients is now 1
ERROR: KUniqueApplication: Registering failed!
ERROR: Communication problem with kcontrol, it probably crashed.
DCOP: unregister 'anonymous-4751'
jason@JasonK:~$ DCOPServer : slotTerminate() -> sending terminateKDE signal.
klauncher: KLauncher::process ---> terminateKDE
kdeinit: terminate KDE.
DCOP: unregister 'klauncher'

Very similar to the other user's results.
Even though this is very frustrating, I'm enjoying the learning curve an OS OS (heh) offers. There are so many things that I can both do very well and teach very well, but always something like this that poses a challenge.

I'd still like to know why none of my Kubuntu Live CD's install but my Ubuntu ones are a dream, but that's for another thread:)

---

### Post by sinclac on 2007-03-26
Sorry didn't mean to hijack your post.

---

