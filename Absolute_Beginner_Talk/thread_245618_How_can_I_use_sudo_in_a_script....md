---
title: "How can I use sudo in a script..."
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by handy on 2006-08-28
I need to run a couple of simple   scripts at startup via the **Menu: *System / Preferences / Sessions - Startup Programs***

I need to use the commands, **sudo cp ...** in one script & **sudo mount -a** in the other.

How is it possible to do this when you are not root, & can't supply a password?

Any help much appreciated...

---

### Post by deltoya on 2006-08-28
well, i suppose you could make root the script owner, and then set the sticky bit, which would make it run as the user (root) even when launched from a normal user. But if you could isolate the need, and use the sticky in smaller  portions of the script, it'd be nicer. Never run anything as root unless you really need to....

try:
$ sudo chown root scriptname.sh
$ sudo chmod 750 scriptname.sh
$ sudo chmod +s scriptname.sh

Just make sure the script group is still yours, and you shouldn't have problems.

---

### Post by huygens on 2006-08-28
There is probably not a good way. If you put the password in your script and pass it to sudo, then perhaps somebody could read your password...
Perhaps, a not so bad way, could be that you authorise for your account only that the 'cp' and 'mount' command do not require a password to be used.
If your username is 'huygens', then a line like the following in your sudo configuration would be enough:
```
huygens ALL=NOPASSWD: /bin/cp, /bin/mount
``` The sudo configuration file shall only be edited with the command visudo: ```
sudo visudo
```If you want to know why and the risks of modifying your sudo configuration file, refer to this thread and particular post: [http://www.ubuntuforums.org/showthread.php?p=1337839#post1337839](http://www.ubuntuforums.org/showthread.php?p=1337839#post1337839)

Anyway, authorising these two commands without password is better than giving the password in your script directly, IMHO. Only experience users having access to your account could modify everything without giving a password in this way, just because they could use cp.

OK, so I introduce a small security hole in your system... Well there is a way actually to avoid it but it is a bit longer to implement than the above solution. Let say the file you need to copy is /etc/foo and you need to copy it as /etc/faa. What you could do is:```
sudo sudo addgroup --system priver
sudo adduser --system --no-create-home --ingroup priver priver
chmod g+w /etc/faa
chmod g+r /etc/foo
sudo chgrp priver /etc/f{aa,oo}
``` Now, the line in your sudoers should look like this:
```
huygens ALL=(priver) NOPASSWD: /bin/cp, /bin/mount
``` Now you can copy the file foo over faa with out having to enter a password :-) The line of code is:```
sudo -u priver cp /etc/foo /etc/faa
``` _Explanation_: What has been set is a new system user (no one can login into that account) and this new user can modify only the file /etc/faa ('chmod g+w' give the write permission to the group, 'chmod g+r' give the read permission to the group, and 'chgrp priver' change the group to priver). So priver can for sure read /etc/foo and write, modify /etc/faa. The line in the sudo configuration means that huygens can identify himself as the user priver and execute in this configuration the command cp without giving a password.
When you execute ```
sudo -u priver cp /etc/foo /etc/faa
``` you tell sudo that you want to be identified as priver. And thus, you can modify /etc/faa.
So someone having access to your account could only be modifying the file faa :-) which is much better than before...

Huygens

---

### Post by handy on 2006-08-28
Thank you both for your great replies.

I will spend a good deal of time tomorrow I'm sure, learning from both of you.

Surely thanks to your help, I will be able to succeed in automating 2 processes. :KS

& securely doing similar in the future...

---

### Post by handy on 2006-08-29
**@deltoya** Unfortunately, I could not get my simple two line script to work using your method.
It may have been something I did... Thanks again for your input though!

**@huygens** I have just tested with a reboot your first method, of editing the sudo configuration & it works!!!  This is great for me & for others who have similar problems, due to what I think is an incompatability between Ubuntu & certain router chipsets. (a BUG!)

I'm yet to try my 2nd one line script, which will automate my ***abuse*** of the NFS, allowing me to easily use it as a P2P home network. :) 

I'll post my results...

---

### Post by handy on 2006-08-29
**@huygens** Victory #2!! :KS 

The 2nd script which is **sudo mount -a** to re run the /etc/fstab, which is setup to mount remote directories with lines like the following:

192.168.0.3:/home /media/handy2home nfs	rw,hard,intr	0	0

so that if any other machines are allready on line in the home NFS LAN, they will be made accessible through their predefined mount point in the just booted machines fstab.

This is my bush mechaniced home NFS P2P network! :mrgreen:  I setup each machine as a server, & put each other machines address in the fstab's. & now I can automatically re run the fstab during the boot process.

[This page]("http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT"), gave me all & more than I needed to easily setup NFS 4 days ago. Highly recommended.

---

### Post by huygens on 2006-08-29
I'm happy it did work for you :-)

Huygens

---

### Post by cstudent on 2006-08-29
Another way to do it:

[http://www.ubuntuforums.org/showthread.php?t=233195](http://www.ubuntuforums.org/showthread.php?t=233195)

---

### Post by yota on 2006-08-29
@Deltoya

suid (I suppose you meant this instead of sticky) no longer works on scripts, but it still does on binary files.
It had been removed for safety reasons, try this to have a proof:
> 
yota@linbook:~/scripts$ ll suid.sh
-rwsr-s--- 1 root yota 7 2006-08-29 15:10 suid.sh
yota@linbook:~/scripts$ cat suid.sh
whoami
yota@linbook:~/scripts$ ./suid.sh
yota
yota@linbook:~/scripts$

Another way to launch script as root at boot-time is call them from /etc/init.d/rc.local.

Hope this helps.

---

### Post by handy on 2006-08-29
> **cstudent said:**
> Another way to do it:

[http://www.ubuntuforums.org/showthread.php?t=233195](http://www.ubuntuforums.org/showthread.php?t=233195)

Thanks for your input! :) 

I like not having to put my password out there.  (Not that it really matters in my current home LAN situation.) :rolleyes:

---

### Post by handy on 2006-08-29
> Another way to launch script as root at boot-time is call them from /etc/init.d/rc.local.

Hope this helps.

Thanks,:)  I new there was another way apart from the Gnome GUI, I must of brushed up against it in the forums some time.  No way I could remember what it was though ... ;)

---

### Post by huygens on 2006-08-29
> **cstudent said:**
> Another way to do it:

[http://www.ubuntuforums.org/showthread.php?t=233195](http://www.ubuntuforums.org/showthread.php?t=233195)

As mentionned in the thread, the drawback of this method is that you have the password in clear inside the script file, which even if one removes the read privilege, it is still not safe.
I was suggesting your way in my first reply in this thread, but actually I did not detail it, because I thought it was a bad solution.
I like the second solution I have proposed. It is longer to setup, but it is quite a lot safer :-)

Huygens

---

### Post by cstudent on 2006-08-29
> **huygens said:**
> As mentionned in the thread, the drawback of this method is that you have the password in clear inside the script file, which even if one removes the read privilege, it is still not safe.
I was suggesting your way in my first reply in this thread, but actually I did not detail it, because I thought it was a bad solution.
I like the second solution I have proposed. It is longer to setup, but it is quite a lot safer :-)

Huygens

Well, there are two ways I see it as unsafe. First is, someone has physical access to your machine. But being as my computer is in my home and the only other person who would have access is my wife, I'm not too worried about that. The other possible way I see is from the outside world, which means to access my computer they would have to figure out my username and password, thus they would already have my password, so it being visible in a script wouldn't matter much. 

Maybe there is someother security risk I'm not thinking of. If so, please enlighten me.

---

### Post by huygens on 2006-08-29
> **cstudent said:**
> Maybe there is someother security risk I'm not thinking of. If so, please enlighten me.

Hmm right :-k, but did you think of a malware? When you are under Windows with IE, you need to have abunch of these tools to remove, spyware, adware, keylogger, etc.
It is not only Windows related crap, it also exist in other OS. And under Linux, there are a bunch of rootkit and keylogger in the wild. But also, simple script that would scan your files for passwords. Those script could be run from a browser or e-mail client which has a security vulnerability not covered yet.

I know it is probably unlikely to happen, and you are right on this point :), but I prefer to stay on the safe side. People were calling me paranoïd when I was setting a firewall on my computer about 6-7 years ago ;-) who would still call me that now! :)

Huygens

---

### Post by handy on 2006-08-29
As previously mentioned, mine is a home LAN too.  I think that **huygens** first solution is ideal for my situation; it is **so** easy to do & there is **NO** password exposure at all! :)

---

### Post by Toxicity999 on 2006-08-29
I have a little script for resetting my LCD which works on the principle that all the commands need to be run with sudo but only the first one prompts you for a password. if you use gksu it makes it that much more fancy!

---

### Post by handy on 2006-08-30
> **Toxicity999 said:**
> I have a little script for resetting my LCD which works on the principle that all the commands need to be run with sudo but only the first one prompts you for a password. if you use gksu it makes it that much more fancy!

I have a script run automatically everytime a machine on my LAN boots. It is required to run totally transparently. The script is to handle a Ubuntu bug; with certain routers (chipsets) &  some ISP's where the ISP's DNS addresses are overwritten by the routers IP?  

So, I copy **/etc/resolve.conf** (the correct addresses) over **/etc/resolv.conf** - the genuine file.  

An easy solution that's taken me since Dapper was released to think of! :rolleyes:

***[Edit:] I finally was pointed to a very tidy solution to this DNS problem.  [See Post 3. here]("http://www.ubuntuforums.org/showthread.php?t=279339") for a walk through...***

---

