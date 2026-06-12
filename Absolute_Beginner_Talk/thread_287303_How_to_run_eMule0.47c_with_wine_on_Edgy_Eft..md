---
title: "How to run eMule0.47c with wine on Edgy Eft."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by janmartin on 2006-10-28
How to run eMule 0.47c with wine on Edgy Eft.

eMule is the first an oldest (read: stable) fork of the original eDonkey client.
Which unfortunately is no longer available since September 2006.

Even when a Windows program eMule works very well with wine. 
Wine is an Open Source implementation of Windows for Linux.

**For this example my username is edgy. Use yours instead!**

This is meant to be simple, so I intentionally avoided fancy stuff. 
Also it should teach a bit how to do things yourself.
You are welcome to add to this manual.

This has been tested with Ubuntu 6.10 Edgy Eft and eMule0.47c.
Before you start you might want to check for a new version of eMule at the eMule homepage:
[http://www.emule-project.net](http://www.emule-project.net)

1) **First follow this easy guide:**
[http://whirlpool.net.au/forum-replies-archive.cfm/613653.html](http://whirlpool.net.au/forum-replies-archive.cfm/613653.html)


2) **Increase "open files" to avoid "too many open files" errors.**
In Terminal:
```

edgy@eft:~$ sudo su -c 'echo \* soft nofile 4096 >> /etc/security/limits.conf'
edgy@eft:~$ sudo su -c 'echo \* hard nofile 4096 >> /etc/security/limits.conf'

```
Restart Ubuntu.

**Panel Icon for easy start.**

In /home/edgy create a file named runemule.sh  and put this into it:
wine ~/.wine/drive_c/Program\ Files/eMule/emule.exe

Panel
Rightclick -> "Add to Panel..." -> Custom Application Launcher"
Type: Application  in Terminal
Name: eMule
Command: /home/edgy/runemule.sh
OK

You can even have a nice icon:
In /home/edgy/.wine/drive_c/Program Files/eMule/webserver 
there is a jpg named ct_1.gif.
Rightclick -> Open with -> Open with GIMP Image Editor.
File -> Save as
Save it as ct_1.xpm to home/edgy
(You will have to change the "Name:" from ct_1.gif to ct_1.xpm.)

Now rightclick on the icon you added to the panel before.
Click on No icon.
Click on Browse.
Goto home/edgy
Click Open.
Choose ct_1.xpm.
Click OK.

**Handy "Incoming" folder**
eMule's default Incoming folder is
/home/edgy/.wine/drive_c/Program Files/eMule/Incoming
we will add a symlink to access it at 
home/edgy/Incoming

Open Terminal.
```

sudo ln -s '/home/edgy/.wine/drive_c/Program Files/eMule/Incoming' /home/edgy/Incomming

```

A new "Incoming" entry wil appear in home/edgy.
Click it to see the content of
/home/edgy/.wine/drive_c/Program Files/eMule/Incoming
It will behave like a real folder.
However if you delete it the original folder (and its content) will still be there.

Have fun!

---

### Post by janmartin on 2006-10-29
Update:
eMule needs to open 2 random ports to conect.
You might have to open / forward these ports when using a router to make eMule really fast.
This is a good site: [http://www.portforward.com](http://www.portforward.com)
Even when written for Windows, it works great for Ubuntu.

---

### Post by sup on 2006-10-29
use [amule]("http://www.amule.org") for God's sake, it is almost feature full port, stable and native.

---

### Post by janmartin on 2006-10-29
I have been using eDonkey2000 for years.
The Options -> Filter function is unique and I have not found it in any other mule program.

Then when I migrated to Edgy Eft I tried aMule, xMule, and eMule each for a few days. Also a lot of other programs. 

eMule came out best.

This is a nice comparison and good starting point:
[http://en.wikipedia.org/wiki/Comparison_of_eDonkey_software](http://en.wikipedia.org/wiki/Comparison_of_eDonkey_software)

Also sometimes it helps to compare a few screenshots if one does not want to install.

---

### Post by sup on 2006-10-29
what does the filter do?

---

### Post by janmartin on 2006-10-30
In eDonkey one could add entries to a permanent filter.
Search results matching this filter would never ever be displayed.

Filter entries could look like this: 

If one does not ever want to see Windows stuff:

.exe
Microsoft

or
porn
sex

to avoid certain results. You get the idea.

My list was rather long and personal.
Unfortunately I never found something like this in a mule.

---

### Post by nrs on 2006-11-01
> **sup said:**
> use [amule]("http://www.amule.org") for God's sake, it is almost feature full port, stable and native.

aMule is next to useless in Edgy either because of a wxGTK issue or aMule itself. 

Really wish they'd just use straight GTK+ with or without a language binding.

---

### Post by disc on 2006-11-01
Fantastic guide, thank you very much!

---

### Post by sup on 2006-11-02
> aMule is next to useless in Edgy either because of a wxGTK issue or aMule itself.
what issue? I have not run amule since upgrading, but when I started it, ti looked fined:-/?

---

### Post by nrs on 2006-11-02
(amule:10836): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

Gtk-ERROR **: file gtkcontainer.c: line 2447 (gtk_container_propagate_expose): assertion failed: (child->parent == GTK_WIDGET (container))


I believe there have been bugs reports already filed & confirmed.

---

### Post by YokoZar on 2006-11-05
Good news - looks like there's a working patch for the bug in eMule that would cause it to stop making new connections after about a day.  The next version of Wine should include this, rendering the need for hacking limits.conf obsolete.

---

### Post by Dr Lecter on 2006-11-06
Hi everybody:

 I've noticed that "too many open files" bug dissapears with the changes written in this post, but when emule 0.47c is working, it crashes about 3 hours from the beginning. Is this trouble caused by the number of connections proposed (4096) or is a bug from wine?

 Sorry, I have not idea about software, wine etc.

---

### Post by freshmaker on 2006-11-07
I actually tried with different version of emule then tried with 0.47c and... the same result the same messeg

```
Failed to open the service control manager.
```

I don`t have even a clue what to try next...

---

### Post by freshmaker on 2006-11-07
I tried the instruction and got thiss:


```
my@my-laptop:~$ wine ~/eMule0.47c-Installer.exe
wine: creating configuration directory '/home/en/.wine'...
Failed to open the service control manager.
```



any idea what went wrong???

EDIT*

I tried again by unistalling and installing wine agai and got this:

```
my@my-laptop:~$ wine ~/Desktop/Neo_Mule_v4.25_installer.exe
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:SetWindowTextA setting text "Neo Mule 4.25 Setup" of other process window (nil) should not use SendMessage
libGL warning: 3D driver claims to not support visual 0x4b
err:ntdll:RtlpWaitForCriticalSection section 0x7eb64360 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,8,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,16,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,24,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,32,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,41,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,49,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,57,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,65,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,74,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,82,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,98,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,106,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,123,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,131,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,139,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,148,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,156,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,164,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,172,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,205,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,213,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,222,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,230,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,238,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,246,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,255,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,246,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,238,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,230,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,222,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,213,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,205,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,180,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,172,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,164,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,156,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,148,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,139,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,131,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,123,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,115,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,106,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,98,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,82,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,74,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,65,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,57,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,49,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,41,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,32,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,24,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,16,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10024,0x00ffffff,8,2): stub!
wine: Critical section 7eb64360 wait failed at address 0x7bc2df40 (thread 000c), starting debugger...
Unhandled exception: wait failed on critical section 0x7eb64360 thread_data_tls_index+0x44
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc2df40
Process of pid=0x0000000a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
00000008 
        0000000e   15
        00000009    0

```

nothing happened for 20 min.... ](*,) 
and I closed the terminal.

---

### Post by YokoZar on 2006-11-09
Ok, the patch to fix the connections bug with eMule is into WineCVS.  Wine 0.9.25 should run eMule fine and without any special instructions!

---

### Post by lostedsoul on 2006-11-18
kad still drops after a few hours....:evil:

---

### Post by raptor_ on 2006-12-01
any news about kad drops?
with 0.9.26 the bug persists

---

