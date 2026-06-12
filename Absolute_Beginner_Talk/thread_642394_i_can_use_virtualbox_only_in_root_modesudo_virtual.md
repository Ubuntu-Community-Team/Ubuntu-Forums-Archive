---
title: "i can use virtualbox only in root mode/sudo virtualbox"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by iKonaK on 2007-12-16
i can use virtualbox only in root mode / sudo virtualbox
is not a big bother but i don't get it...

---

### Post by gn2 on 2007-12-16
Have you added your user account to the Virtualbox user group then logged out and back in?

There should be a Users/Groups item somewhere in the Gnome menu, in there, select the properties of your user account and select Virtualbox in user group.

---

### Post by iKonaK on 2007-12-16
thanks that just did the trick :)

---

### Post by tjk on 2008-02-26
I was going to post a new message, but then I saw that this was very related to my question...
I have been  running VirtualBox  in root for some time now -- is it  unsafe or not recommended to  do this?  And if yes, why?

PROBLEM: Long time ago, when I first created the virtual  disk, I first did not use root to run VirtualBox.  But then there was a time when I couldn´t start VirtualBox so I used root  to start it and reinstalled my OS and software.  Recently I discovered that I can run VirtualBox without being root and it is using exactly the same virtual disk! (But they each have different software loaded.)  How is this possible when there is only three partitions and they are used by home/, root/ and swap (both the same)?  What will happen if I delete one of the systems?  Will I lose both?  Any ideas   of how to correct this situation?

---

### Post by PeterJS on 2008-02-26
> **tjk said:**
> I was going to post a new message, but then I saw that this was very related to my question...
I have been  running VirtualBox  in root for some time now -- is it  unsafe or not recommended to  do this?  And if yes, why?

Short answer is running anything that doesn't absolutely need root privileges with them is a risk, in fact even running things that require root privileges with root privileges is a risk, but obviously a necessary one. Any time you run something as root it can be used as an attack vector for bad things to happen in a global fashion, even excluding deliberate attacks, running as root offers no protection against shooting yourself in the foot, you at least have the safety of knowing that when things screw up as a user your system will still be easily recoverable, if not instantly usable.

> 
PROBLEM: Long time ago, when I first created the virtual  disk, I first did not use root to run VirtualBox.  But then there was a time when I couldn´t start VirtualBox so I used root  to start it and reinstalled my OS and software.  Recently I discovered that I can run VirtualBox without being root and it is using exactly the same virtual disk! (But they each have different software loaded.)  How is this possible when there is only three partitions and they are used by home/, root/ and swap (both the same)?  What will happen if I delete one of the systems?  Will I lose both?  Any ideas   of how to correct this situation?

It's virtual, so the only connection between the virtual partitions and the actual partitions is that the virtual partitions must reside somewhere in the mounted file system the real partitions underlie. So the question is where are the virtual images, and what permissions do they have? I've never used Vbox, but I'd wager they're in your home directory some where, and even if running Vbox as root changed the user ownership over them, they probably still belong to the Vbox group which has read/write permissions to them.

---

### Post by Sonic132 on 2008-02-29
I can't even get virtualbox to run at all. Is there a sudo command you use?
Because it didn't create a shortcut and I really don't know how to use commands to get it out from wherever it is that it automatically installed to.

---

### Post by kpkeerthi on 2008-02-29
**VirtualBox** is the command to launch it from a terminal. Are you sure it is not in Applications -> System Tools ?

---

### Post by Sonic132 on 2008-02-29
From Terminal it gives me a 
> bash: Virtualbox: command not found
 message.
As for it being in my menus. I dont see it anywhere. Possibly it failed to install? Otherwise, is there a prefix to the run command? Or are you sure it's just > VirtualBox. No sudo or gksudo?

---

### Post by kpkeerthi on 2008-02-29
Its Virtual**[COLOR="Red"]B[/COLOR]**ox.

---

### Post by kpkeerthi on 2008-02-29
> . No sudo or gksudo?
Not required if you have your user Id added to vboxusers groups as explained [in post#2]("http://ubuntuforums.org/showpost.php?p=3963539&postcount=2")

---

### Post by Sonic132 on 2008-03-02
Yep. I have my main group set to vboxusers.
But is it a gui app or does it only run in terminal? I don't understand why typing 'VirtualBox' in Terminal does nothing.

---

### Post by forestpixie on 2008-03-02
it should be in your system tools menu, if it's not have you rebooted

I think - from memory - it's vbox in a terminal

---

### Post by Sonic132 on 2008-03-02
Ok. That was it.
I guess I'm just to blind. It was under System Tools. Thanks a lot!

:guitar:

---

### Post by Sonic132 on 2008-03-02
Now I just don't know how to add my existing Windows XP to Vbox so that I can run it from Ubuntu.

Anyone know?

---

### Post by forestpixie on 2008-03-02
not usre that you can - I did it once before, but that was with vmware instead - there is a tool that you can get to do that

have a look at this sticky from virtualisation
[http://ubuntuforums.org/showthread.php?t=631671](http://ubuntuforums.org/showthread.php?t=631671)


This is the tool I used from vmware to convert existing win install

[http://www.vmware.com/download/converter/](http://www.vmware.com/download/converter/)

---

### Post by Sonic132 on 2008-03-03
Yeah I think I'm just gonna leave that alone. I'm afraid of messing up my only working OS right now.
Because after skinning my Win XP OS to look like Vista. It's freezing while loading all the apps.
So now Ubuntu is the only working OS on my system and I want to keep it that way.

---

### Post by lswest on 2008-03-03
also, to run virtualbox from the terminal you need to run ```
virtualbox
``` (no capitals, linux is case-sensitive)

---

