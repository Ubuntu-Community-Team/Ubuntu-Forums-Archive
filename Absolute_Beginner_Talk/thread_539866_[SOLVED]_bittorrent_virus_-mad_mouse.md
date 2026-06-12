---
title: "[SOLVED] bittorrent virus -mad mouse"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by vector on 2007-08-31
Hi all
I have been using bittorent tornado lately with no ill effects however this morning I went to check in on how my files were downloading and soemthing very strange happened.
The mous went crazy.. As soon as I move the mouse , windows popup, things start to run I cant control the cursor.

I shut the system down a rebooted. All came back as normal. I then restarted the bittorrent within about 20 secs the behaviour started all over again!!. I had to shut down once more.

Rebooted and as yet have not restarted bittorrent.

SYSTEM:
Ubuntu 2.6.15
connected to a billion router. ADSL
bittorrent has been port fwd in the router.  a group of 4 ports from 2345-2349 fwd to 1345-1349 (those are not the actuall numbers of course)

Im a little scared to run the bittorrent again as I think it will invoke mad mouse again??

help??

---

### Post by mikewhatever on 2007-08-31
You can try checking your system with [AVG]("http://ubuntuforums.org/showthread.php?t=539791&highlight=avg") and with chkrootkit from the repositories. What version of Ubuntu do you have?

---

### Post by deadgobby on 2007-08-31
Which BT are using. I used Azures and it was acting funny. It started to up load crap from my desktop. I shut down the program. I was like hacking into my system. I do not use that BT any more. 
Gobby

---

### Post by por100pre1 on 2007-08-31
Try deleting your BitTornado settings:

```
rm -r .BitTornado
```

Install chkrootkit and rkhunter:

```
sudo aptitude install chkrootkit rkhunter
```

and run them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by vector on 2007-08-31
im not sure 
it rebooted my session last time I was typing here. and I didnt have bittorent running.

anyway.
chkrootkit and rkhunter are all fine
a new kernel /image was available so i have installed that. 
 I changed the port fwding ports for bittorrent and we will see what gives.

the point that it rebooted the session when torrent wasnt even runnign and I had router firewall on full lock down, no access. I tend to suspect its just a system bug and I jumped to paranoid conclusions.. ill keep ya posted

---

### Post by swoll1980 on 2007-08-31
> **deadgobby said:**
> Which BT are using. I used Azures and it was acting funny. It started to up load crap from my desktop. I shut down the program. I was like hacking into my system. I do not use that BT any more. 
Gobby

It's reseeding the torrents you downloaded(this is normal)

---

### Post by vector on 2007-09-03
well two days now touch wood its been fine and I have been torrenting. so i guess paranoia and some wierd behaviour combined.

Just strange. cant implicate what was responsible.

---

### Post by Perfect Storm on 2007-09-03
It could be a simple odd bug.

---

### Post by ddrichardson on 2007-09-03
Are there any comments  on the site you downloaded the torrent from suggesting similar problems?

---

### Post by vector on 2007-09-06
no. That was my first port of call, that and a google for bittorrent viruses.

Still all going well, mark it down to the twilightzone.

---

