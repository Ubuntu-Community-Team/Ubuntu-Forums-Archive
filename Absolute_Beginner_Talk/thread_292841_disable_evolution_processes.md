---
title: "disable evolution processes"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by almos on 2006-11-04
Hello everybody,

I am new to Ubuntu (Edgy Eft), but I used other
linux distributions. I think Ubuntu starts suprisingly lots of processes at boot time.

How can I disable evolution (evolution-exchange-storage, evolution-alarm-notify and so on)?
I never use evolution, but
I admit that I dont know what they are good for.
The only two reasons for disabling (or killing them)
are more free memory and faster gnome startup.

 By the way, there are other processes and services
like ssh-agent, /usr/lib/nautilus-cd-burner/mapping-daemon
and 
/usr/lib/notification-daemon/notification-daemon
which seem to consume lot of memory.
Is it a good idea to disable/kill them?

Thanks for any suggestion.

A.

---

### Post by davmac on 2006-11-06
If you don't use evolution why not remove it? If you start up synaptic (system -> admin -> synaptic package manager), find evolution, click the button next to it and choose "complete removal".

I personally prefer to use thunderbird and have had no problem removing evolution.

Hope this helps,

Dave Mac

---

### Post by almos on 2006-11-06
Thank you very much for your suggestion.
It works for me too :-)

As for MUAs, I prefer mutt due to huge maildirs
(6000+ messages) which is unfortunately 
not supported by thunderbird (yet).

And there are other processes I would like to kill
(like nautilus-cd-burner/mapping-daemon and so on).
Do you know how to dissable them? Perhaps in a
tricky ~/.gnome configuration file or somehow with
the system menu?

Again, thank you for your help.

Best regards,A.

---

### Post by davmac on 2006-11-07
Are you using Dapper (6.06) or Edgy (6.10)? I know that many of these processes in Dapper are started by the scripts in the /etc/init.d/ directory. You could try editing the relevant scripts and commenting out the offending lines, but make sure you've got a backup and live CD to hand for when it breaks :)

In Egdy, the init system has been replaced by upstart and I've not yet had chance to dig into how it works and how to enable/disable stuff.

Dave Mac

---

### Post by almos on 2006-11-07
Hello,
I have upgraded to Edgy recently (with some minor problems
I have been fighting).
So I dont know what starts those processes.
I tried to empty the whole /etc/X11/xsession.d but
then the whole gdm login process failed (even with icewm,
kde, gnome, default session).

Thanks for your tips :-)

Best regards,
B.

---

### Post by Vexed Arcanist on 2006-11-08
> **davmac said:**
> If you don't use evolution why not remove it?

This works unless you used ubuntu-desktop to install ubuntu/evolution.  In that case removing evolution removes ubuntu-desktop, which comes with the warning that removing it could interfere with updates.

I too would like to remove or neuter Evolution, with only 512mb ram every mb counts and the processes running for no reason via Evolution are eating up ~6mb.

---

### Post by almos on 2006-11-08
Thanks for the information.

I installed Ubuntu from a CD. 

Do you know more about the possible interference with the updates?
I run update-manager manually almost every day
(because I am a bit anxious about security).

Best regards,
A.

---

### Post by seventypercent on 2007-01-09
I came across this post while trying to find the answer to the same question. I too, use Thunderbird and was a bit worried about the consequences of completely removing Evolution. After digging around in the menus a bit, the easiest way that I could find (in Edgy) was to go to "System -> Preferences -> Sessions", choose the "Startup Programs" tab, select "evolution-alarm-notify", and disable it.  The next time you start up, the evolution processes should no longer be there.

---

