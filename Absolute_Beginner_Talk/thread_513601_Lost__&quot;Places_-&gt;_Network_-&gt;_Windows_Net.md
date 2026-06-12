---
title: "Lost  &quot;Places -&gt; Network -&gt; Windows Network&quot;"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by samtrevino on 2007-07-30
Hello Everyone,

I've tried like hell to resolve this issue researching it, but no real luck. I think something has occurred with samba or perhaps I did something stupid. I just recently loaded Unbutu 4 days ago and got it working (wifi, sound, networked a printer), but in doing so I've somehow compromised my networking with my windows desktop.

Running Unbuntu Feisty Fawn 7.04
Dell B130 Inspiron 
1.5 GHz Celeron
Broadcom wireless

Attempting to network for file sharing capabilities with a Sony running Win XP Home Ed.  

I've tried a few things to resolve this issue with limited success. 

Issue: for some unknown reason my Windows Network is no longer available under Places -> Network -> Windows Network. Used to I could find my windows machine (XANDER). Now when I click on it - nothing happens, dead.  

What's worked:

I loaded komba2 

$ sudo komba2

When I run komba2 at root I can access the windows machine fine, but I can not transfer files from my laptop running Unbuntu. I need to be able to deposit files from my laptop to the desktop's second shared drive "Back Up (D)". Also komba2 has to be started each time I boot the laptop, it does network automatically upon boot, but I'm not really concerned about that issue to much. 

Does this information offer anyone insight?

sam@sam-laptop:~$ smbclient -L XANDER
Password: 
Domain=[XANDER] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------              ----      -------
        IPC$                 IPC       Remote IPC
        SharedDocs     Disk      
        print$                Disk      Printer Drivers
        Back Up (D)     Disk      
        Printer2             Printer   Microsoft Office Document Image Writer
        Autohpde          Printer   Autohp
        Printer               Printer   hp deskjet 940c
Domain=[XANDER] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server            Comment
        ---------            -------

        Workgroup     Master
        ---------            -------
sam@sam-laptop:~$ 

Please keep in mind that I am totally new to linux, I've only been at it 4 days. If someone can help me with this networking issue I'd really appreciate that assistance. 

If you require more information just let me know, and fyi, as I said before I'm new so if you have a CLI instruction for me make sure you communicate it entirely, I am not very familiar with linux syntax yet.

Thanks,

Sam

---

### Post by samtrevino on 2007-07-31
A not to elegant solution, but it gets the job done:

Run in terminal:

sam@sam-laptop:~$ sudo komba2

Then run in terminal: 

sam@sam-laptop:~$ gksudo nautilus


This is what I got as I had to run the above command twice:


sam@sam-laptop:~$ gksudo nautilus
(nautilus:6159): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing nautilus-share extension
Initializing gnome-mount extension
Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING

Nautilus-Share-Message: returned from spawn: SUCCESS: 
Nautilus-Share-Message: exit code 255
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled

sam@sam-laptop:~$ gksudo nautilus
Initializing nautilus-share extension
Initializing gnome-mount extension
Nautilus-Share-Message: REFRESHING SHARES
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: spawn arg "net"
Nautilus-Share-Message: spawn arg "usershare"
Nautilus-Share-Message: spawn arg "info"
Nautilus-Share-Message: end of spawn args; SPAWNING

Nautilus-Share-Message: returned from spawn: SUCCESS: 
Nautilus-Share-Message: exit code 255
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled


sam@sam-laptop:~$ 

Opens a Nautilus file browser which allows me to navigate to the mounted net folder, which is the mounted drive on my Windows box. I can now modify files on the networked WIN XP computer.

Solved my problem... now if anyone wants to provide an alternative solution I'm game! Perhaps get my MSHOME to showup under "Places -> Network -> Windows Network." 

Word to the wise fellow noobies this is running at root so you may want to close out the nautilus file browser before surfing the web as may present a security risk. Basically do what you need to do and get out of it. Command also good for editing files.  

Thanks,

Sam

---

### Post by BenHobbs on 2007-07-31
Thanks...that gksudo nautilus command helped me do what I had to do! Much appreciated! :)

---

### Post by samtrevino on 2007-07-31
BenHobbs,

No problem glad my newbie experience could help you.

-samtrevino

---

