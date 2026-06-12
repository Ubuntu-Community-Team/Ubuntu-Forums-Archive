---
title: "new to 7.04"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by the.eagle on 2007-05-21
Hi 
I just installed 7.04 and then installed 'adept'. When I go into adept it says i can't access it unless I log in as ROOT or some other thing, Why does it do this as the other version had no trouble. I don't understand root and want it to return to the other version's access. HOW do I do that?:)

---

### Post by Hellcom on 2007-05-21
Root is just another way of saying admin privileges. If you are doing this in the terminal just put "sudo" without quotation marks before any command that requires root access. Odd though, you should of been using sudo in the other verisons regardless.

---

### Post by rich.bradshaw on 2007-05-21
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by the.eagle on 2007-07-10
I have been through a lot of info about command line but nowhere can I find out how to log in as root and do something with ADEPT. What do I put after 'sudo -i'. There must be somewhere to get this information, and if I am the root user why do I need to log in as root again?  Puzzled.

---

### Post by Vague on 2007-07-10
All you have to do is open up the terminal and enter ```
gksudo adept
``` Then enter your password when prompted to do so.  That will let you run adept as root.

---

### Post by the.eagle on 2007-07-11
I think I an in trouble here. The only terminal I can find is called KONSOLE and it always starts off with 'ian@ian-desktop:~$'. when I put that command in it just went back to that first thing. I cant find any very basic command line tutorials that I can understand. Is there another consol somewhere?

---

### Post by Vague on 2007-07-11
Hmmm, well, try ```
sudo adept
``` and see what happens.  Doing it in Konsole should be fine.

---

### Post by the.eagle on 2007-07-13
No, they didn't work. Here is the output -:ian@ian-desktop:~$ sudo adept
Password:
sudo: adept: command not found
ian@ian-desktop:~$ gksudo adept
ian@ian-desktop:~$

 I still don't understand that I have logged in as root and yet it won't let me open Adept.
Can you think of any other secret codes?

---

### Post by Happy_Man on 2007-07-13
The proper command is ```
kdesu adept_manager
``` The other guys assumed you were on Ubuntu, not Kubuntu.

---

### Post by the.eagle on 2007-07-13
Further to my last, I tried "sudo adept_manager" and this was the output-:ian@ian-desktop:~$ sudo adept_manager
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authenti
cation protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/Default
Plugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugi                                                            ns.desktop
kio (KSycoca): ERROR: No database available!
kapture::PkgSystem::PkgSystem()
libasound2
libc6
mpg321
libasound2
libc6
mpg321
kdecore (KProcess): WARNING: _attachPty() 44
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authenti                                                            cation protocols specified are supported and host-based authentication failed
ian@ian-desktop:~$ ICE default IO error handler doing an exit(), pid = 6575, errno = 0

Any clues?

---

### Post by Happy_Man on 2007-07-13
How did you install Adept? Through the package manager? Or as part of a Kubuntu install? I've never seen those errors before..... :confused:

---

### Post by macogw on 2007-07-13
Are you using Ubuntu or Kubuntu?  Why did you install Adept?  Adept comes by default with Kubuntu, and Ubuntu has Synaptic to serve that function.

---

### Post by the.eagle on 2007-07-14
Sorry , I didn't know there was a difference between ubuntu 7.04 and kubuntu. Or is there? I will look it up. Thanx.

---

### Post by macogw on 2007-07-14
The difference is the Desktop Environment.  Kubuntu has KDE and as such all KDE applications.  Adept is for KDE (it can be used with GNOME, of course, but it requires extra libraries to be installed and then they have to load which, on a slow computer, can be a bit of a memory hit), and Synaptic is for GNOME.  Ubuntu uses GNOME, so it has all GNOME applications installed by default.  Some in this thread said gksu and some said kdesu.  Gksu is the graphical popup that asks for your password to do admin things in GNOME.  Kdesu is the KDE version of that.

---

