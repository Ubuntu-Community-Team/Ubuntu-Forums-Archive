---
title: "yikes, windows samba shares wide open??"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by asinsh on 2006-01-31
I just put kubuntu on one of my pcs (my first experience with linux) and when I checked the samba shares on my network I found another pc that is running WinXP Pro.  I have NOT enabled any file sharing on that pc, and yet kubuntu found it.  I guess that's not so surprising, but what did surprise me is that when I tried to open it, it asked me for my winXP username and password and when I gave it my username and password it opened up at the root (as though I had shared C:/ and everything below).  Pretty disturbing.

But it only happens on one of the pcs on my network...the others seem to work properly (I can only get into directories on those pcs that I have shared).

I know this is really a windows question, but anyone know why my winxp pro pc would open itself up that way??

---

### Post by audax321 on 2006-01-31
Just a thought, but have you scanned it for viruses or spyware. I've never seen anything like that... but I use Linux for everything now anyway :)

I remember one time I had my cable modem plugged in and was browsing my Windows shares only to notice that I could access some of my neighbors computers as well!

---

### Post by asinsh on 2006-01-31
Nope, no viruses, but here's a big lead.  I went into the properties tab for c:/ directory and I found that it said to share the folder (even though there was no sharing icon on the c:/ folder).  I tried to turn that sharing off and I got a message that reads like this:
> This share was created for administrative purposes only.  The share will reappear when the Server service is stopped and restarted or the computer is rebooted.  Are you sure you wish to stop sharing C$?

Well, it just so happens that I am in fact running apache, mysql and php on that pc, so I guess apache is doing something bad along these lines.  Anything I can do to close it down and still run apache?

I'm gonna mess with the settings and see what I can figure out.

---

### Post by AndyCooll on 2006-01-31
That message is a fairly standard one for Windows XP. By default XP is usually set to allow administrator sharing access via C$ and an administrator password.

:cool:

---

### Post by asinsh on 2006-01-31
[QUOTE=AndyCooll]That message is a fairly standard one for Windows XP. By default XP is usually set to allow administrator sharing access via C$ and an administrator password.

:cool:[/QUOTE]

It didn't happen on my other pcs.  I think it's tied to my running apache, no?  How can I shut down that access in a way that survives a reboot?

---

### Post by asinsh on 2006-01-31
After a bit of resarch, I gather that this is an automatic sharing at an administrative level that I suspect gets turned when you install apache.  The share is 'hidden', meaning that other windows pcs on the network can't see it.  But unfortunately a mac or linux computer can see it!  However, I found a threadfound ( [http://www.hardwareanalysis.com/content/topic/22088/](http://www.hardwareanalysis.com/content/topic/22088/)
) that explains how to fix this:

> Open regedt32 (start -> Run -> regedt32)
browse to the following key

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\LanManServer\Parameters
and set the Autoshareserver amd Autosharewks dword value to 0.
(My registry didn't have those entries but I added them there and it worked fine.)

---

### Post by awahl on 2006-11-18
Thanks for the thread! I have several partitions on my WinXP box and all were showing up as $ shares via SMB. Oddly this did not happen in Dapper- e.g. in Nautilus I only saw the shares I selected. In Edgy - I saw everything and this made things quite messy, let alone wide open. 

One thing I did notice is that you need to reset shares in WinXP- as any folder on under root drive is disabled with this hack...even if it was shared before the change... 

Cheers.

---

### Post by steve.horsley on 2006-11-18
The windows share is normally hidden the windows browser will not display shares whos name ends in a '$' sign. Linux doesn't bother to hide them. But I am surprised that C$ isn't shared by all your PCs. I thought that all windows boxes shared all their disks. I'm fairly sure that it's nothing that Apache has done. I'm no windows expert, but I never ever figured out how to stop a windows box from sharing its drives. It is normal, and I think it is the default - it certainly was for NT, which was the last time I looked at shared disks on windows.

---

