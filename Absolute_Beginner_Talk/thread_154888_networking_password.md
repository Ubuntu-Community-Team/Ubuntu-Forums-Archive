---
title: "networking password"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by mravi on 2006-04-04
hi

i would like to configure my network. the ethernet card is installed but is not activated. i'm unable to login to network configuration using root password. wat is the password for network configuration or how do i assign one? in the terminal i'm able to sudo to root user.

thanks
ravi.

---

### Post by trent dillman on 2006-04-04
Ubuntu has root disabled by default. If you can sudo, that's all you need. If you must absolutely have a root terminal, try

```
sudo -s
```

Once in a root terminal, you could enable root by adding a password using the passwd command. But sudo should be enough.

---

### Post by steve.horsley on 2006-04-04
If you're talking about the System->Administration->Networking tool, it asks for "the admin password", meaning **your** password. Not the root password. This is the same as using sudo on the command line, which wants your password. 

The wording on the popup does seem a little confusing, and I think they have changed in in the next release (Dapper).

---

### Post by mravi on 2006-04-04
hi steve,

u've understood my problem. i've tried both passwords (for System->Administration->Networking tool). when i give the root password, a popup says incorrect password & when i give the user password it accepts that but the networking window does not open. i don't know what else can be the admin password. please help. or otherwise i'd like to know how i can activate the ethernet card thru the command line, as well as setting up the IP, DNS addresses.

---

### Post by steve.horsley on 2006-04-04
You shouldn't **have** a root password - unless you did an expert install, in which case sudo may well not work, and I don't know how to fix that.

Try this command from the command prompt: **gksudo network-admin** and see what error you get. This is the command that the System->Administration->Networking tool launches.

---

### Post by xenmax on 2006-04-04
here we go again. try this thread
[http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

---

### Post by mravi on 2006-04-06
hi steve,

u got it right. i had done an expert install (just to get a root password).

i tried **gksudo network-admin** at the command prompt - it gave a couple of warnings, no errors. i used **su root** and then **network-admin** - ti again displayed some warnings but opened the networking window thru which i was able to configure the IP settings.

thanks a lot for the help,
ravi.

---

