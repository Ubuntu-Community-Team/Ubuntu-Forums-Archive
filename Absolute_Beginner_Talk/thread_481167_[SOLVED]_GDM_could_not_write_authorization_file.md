---
title: "[SOLVED] GDM could not write authorization file"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-06-22
Hi everyone, I've been helping friends setup their new ubuntu systems. One guy, Hope, really has no idea about computers, so I'm not entirely sure what he's done today.
I got a call that he couldn't print (again) and when I got there the Print app wouldn't run at all. Then Synaptic gave me this;
> failed to run /usr/sbin/synaptic as user root.........etc.
unable to copy the users Xauthorization files.

So, it seems the 'only' change he made was to download the updates today, but there was 'a whole lot of them' so I'm guessing its the first time he's done it for about a month - (when I did it). He said the printer stopped working after this.
Anyway, I searched here and found various entries re this and followed this one;
> [http://ubuntuforums.org/showthread.php?t=374702&highlight=users+Xauthorization+file](http://ubuntuforums.org/showthread.php?t=374702&highlight=users+Xauthorization+file)
Everything went well as far as ```
sudo shutdown -r now
``` in that this certainly worked but now I am completely unable to login.error is; 
```
GDM could not write authorization file. Disk may be full .....etc.etc. [COLOR="Red"]Login is not possible[/COLOR]
```
I don't believe the disk is full and anyway with these errors its about the access codes having been chopped.......right??:(
Obviously I'd like to fix it if possible but also, he hasn't backed-up since the last time I did it, and if I reinstall he'll lose it all. I've not had any experience using the live CD to fix the install (if thats even possible).
I'm thinking, maybe do a new install on another partition and then hopefully drag the files across.:o

Have I made myself clear? If so then I've explained it poorly.:D
Oh, ......his system is a BenQ 512mb Mem and 60gb? HDdisk,....... only running feisty.

---

### Post by davidshere on 2007-06-22
Reading the other thread you referenced, they suggest running this again if you still have problems:

```
sudo aptitude update
sudo aptitude upgrade
```

Since you can't login, though, you'll need to do this from a terminal window.  At the login screen, choose "Change session" (Sometimes hidden behind an "options" button) and choose "Failsafe terminal".  You'll get a shell prompt.  Execute the above, and when you're done, type 
```

shutdown -r now
```
like you did before.  I always used ```

shutdown -h now
``` but that's from my FreeBSD experience.

Hope this helps.  I'm not really sure what the actual problem is.

---

### Post by klytu on 2007-06-22
This sounds like a permissions issue.  If you can boot into recovery mode on your friends computer, try this from a console: ```
sudo chown yourfriendsusername:yourfriendsusername *.*
``` where <yourfriendsusername> is of course your friend´s actual username.

---

### Post by carloslosgrande on 2007-06-22
Hey, thanks fellas, I'm going back there tomorrow and give it a try.

---

### Post by carloslosgrande on 2007-06-25
Hi, sorry to take so long replying, had a bike accident and altercation.
Anyway, got back to my friends system today and its up and running just fine, even prints!
He just restarted and voila, fixed itself. Seems it needed a bit of a rest.
So I don't know what caused it but I left him a printout of your suggestions, thanks.

---

### Post by ckin2001 on 2007-08-22
I had the same issue tonight - I did an "ls -la" to my home directory, and root owned my .Xauthority file.  A chown me:me .Xauthority fixed the issue.

---

