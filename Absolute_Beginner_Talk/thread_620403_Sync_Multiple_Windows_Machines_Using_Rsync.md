---
title: "Sync Multiple Windows Machines Using Rsync"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by BadTimmy on 2007-11-22
Hello everyone,

I know that there will be several of you that roll your eyes in disgust at what you are about to read but please; humor me!  (I'm still somewhat new to Linux - I'm sure it shows)
[B]
The situation:[/B]
- I need to synchronize data on several Windows XP clients.
- The clients are used by a single user but are in multiple locations across North America.
- All client locations have cable (or better) connections to the internet.
- The user needs to be able to create, modify, or delete a document on one of his XP clients and have the change reflected on each of the other clients.
- I'm cheap and I don't want to pay for a subscription service this will do this for me (not to mention that I don't trust them).
- This needs to be completely transparent to the user (because if the user can tinker, the user *will* tinker and undoubtedly mess it up).
[B]
My plan (thus far):[/B]
- Using Ubuntu create a "server" in a centralized location and synchronize over VPN.
- Apps I'm using to do this:
   - Rsync (will look after the transfers and the versioning of the files)
   - Hamachi VPN (will give me a secure pipe to each of the clients that will traverse NAT securely so I don't have to go and punch holes in any firewalls)
   - Cygwin (enables me to run Rsync on the clients as a service)
[B]
Progress:[/B]
I've followed [this handy guide]("http://www.gaztronics.net/rsync.php") but I must be missing something somewhere because I'm having problems on the server side.  The author of that page also didn't assume that his readers would be synchronizing the data to/from multiple clients.  

Right now I'm calling rsync from a batch file from the task scheduler (for now) and that part seems to be working well.

Here is what my rsync command looks like on the XP clients:
```
rsync -vrutzh --stats --progress --password-file=c:\cygwin\secret --delete "cygwindrive/c/Documents and Settings/<username>/My Documents" <username>@<server's Hamachi IP>::<module name>
```

Here is what my /etc/rsyncd.conf looks like on the Ubuntu "server":
```
# GLOBAL OPTIONS
log file=/var/log/rsyncd
pid file=/var/run/rsyncd.pid

# MODULE OPTIONS

[mod1]

        path = /home/<username>/backup
        uid = <username>
        gid = <username>
        read only = false
        auth users = <username>
        secrets file = /etc/rsyncd.secrets
        list = yes
        transfer logging = yes
        log format = %t: host %h (%a) %o %f (%l bytes). Total %b bytes.
        timeout = 600
        dont compress = *.gz *.tgz *.zip *.z *.rpm *.deb *.iso *.bz2 *.tbz
```
[B]
Questions:[/B]
- Am I headed down the right path or is there something that is bigger/better/easier/cooler that will do everything that I need?
- Are my client side rsync options correct or am I going to cause myself data loss at some point?  Will this keep all of the computers up to date without risking unwanted deletes?
- Where (how) should I be automatically executing "rsync --daemon" on the Ubuntu machine?
- Where (how) should I be automatically executing "hamachi start" on the Ubuntu machine?

Please be gentle... I'm kinda/sorta new still!  How-tos appreciated.[B]

Thanks for reading this far![/B]:)

---

