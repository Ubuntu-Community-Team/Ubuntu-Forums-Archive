---
title: "Unable to cd to &quot;/home/..."
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by thompa on 2007-02-06
Hi there,

Still have problems booting into the desktop.... and wonder if anyone can help!

I have done something silly and on booting the machine its puts me into the TTY1 interface and entered login and password it reports that it is 'unable to cd to "/home/allan"'

I guess that means that somewhere the ability to change directory to my home directory has been lost.

I also see that it reports an inability 'to make a kernel log'... don't know what that means.. except it may be unable to report of what is happening at log time

thanks in anticipation.

Allan

---

### Post by taurus on 2007-02-06
Did you try to change the permission of the whole system?  What's the output of this command from a prompt?

```
ls -la /home
```

---

### Post by jonnyburns on 2007-02-06
similar problem to above!

---

### Post by mvaniersel on 2007-02-06
Have you moved or renamed the /home directory perhaps? What do you see if you do "ls /"?

---

### Post by thompa on 2007-02-06
HI,

I get:-

total 20
drwxr-xr-x 5 root root 4096 2007-02-04 .
drwx------ 21 root root 4096 2007-01-24 ..
drwxr-xr-x 60 allan allan 4096 2007-02-05 allan
drwxr-xr-x 2 root root 4096 2007-01-27 samba
drwxr-xr-x 2 root root 4096 2007-02-04 Windows

Allan

---

### Post by taurus on 2007-02-06
What about

```
ls -la /
```

---

### Post by thompa on 2007-02-06
with la /

I get:-
bin
dev
initrd
lib
mnt
root
sys
rar
boot
etc
initrd.img
lost+found
opt
sbin
tmp
vmliuz
cdrom
home
initrd.img.old
media
proc
srv
usr
vmlinuz.old

with ls -la / I get all of these files expanded to have the date and bit information... do you need that? it will take some time to write down and tap in!

---

### Post by taurus on 2007-02-06
Only need the ls -la for the directory /home though.  Try this

```
chmod 755 /home
```
Now, see if you can log in as allan.

---

### Post by thompa on 2007-02-06
OK - typed in chmod 755 /home
and then
shutdown -r now

The machine rebooted and everything loaded ok apart from Starting Kernel log and Avahi daemon which failed.

I was dumped at the TTY1 login typed in my login and password but was dumped out again with the same 'Unable to cd to "/home/allan"

So... I logged in as 'root' and changed the directory to /home and did the ls -la thing.. which came up with the same as I had before:-

total 20
drwxr-xr-x 5 root root 4096 2007-02-04 .
drwx------ 21 root root 4096 2007-01-24 ..
drwxr-xr-x 60 allan allan 4096 2007-02-05 allan
drwxr-xr-x 2 root root 4096 2007-01-27 samba
drwxr-xr-x 2 root root 4096 2007-02-04 Windows

... nothing changed and still stuck.

Could I not just reinstall the system files... from the Live CD?

Allan

---

### Post by taurus on 2007-02-06
At this point, it's better to reinstall the whole thing and don't forget to format it first.  And perhaps in the future, be careful with the sudo command and try not to change any system permissions or you would have a one sick machine again.

---

### Post by thompa on 2007-02-06
Taurus,

Hate to admit defeat on this but.... I have spent long enough on this and have occupied you way too much!

Thanks for your time!

Any advice on reinstalling from the live cd - I would like to keep the partitions the same as they are.

What about Edgy - should I install that instead of Dapper?

Allan

---

### Post by ComplexNumber on 2007-02-06
yeah, i would *probably* say reinstall. BUT BEFORE YOU DO THAT, can you give me a printout of your fstab file(its in /etc/fstab), please? i'm wondering if you have no mount point for your home directory if its on a separate partition.

---

### Post by thompa on 2007-02-06
Can you please advise how I do that?
I have cd /etc and fstab is there - but how do I list it to the screen?

---

### Post by ComplexNumber on 2007-02-06
> **thompa said:**
> Can you please advise how I do that?
I have cd /etc and fstab is there - but how do I list it to the screen?
ok, if you can't use a GUI appication, then go to /etc, then type in 'nano fstab'. tell me if you can see "/home" mentioned anywhere.

btw you did put your home directory on a separate partition when you installed ubuntu didn't you ?

---

### Post by thompa on 2007-02-06
That's neat!
proc           /proc               proc  defaults                              0       0
/dev/hda2  /                      ext3  defaults,error=remount-ro   0       1
/dev/hda5  none                swap sw                                      0       0
/dev/hdc    /media/cdrom0 udf,iso9660 user,noauto               0       0

When I log in as root I see home when I enter the command ls.

I don't think that I put it onto a separate partition....

---

### Post by ComplexNumber on 2007-02-06
>  I don't think that I put it onto a separate partition....
oh, well, that goes that theory down the drain then. i thought that you'd somehow lost the mount point for /home. therefore, you would be able to access the /home directory (note that you would still be able to see it with the 'ls' command, i believe).

---

### Post by dimeotane on 2007-02-22
I've got a very similar problem.  I was working on fixing the permissions for $home/.drms and I did a chmod 755 to /home/dimeo and a chmod 755 to /home.

But in the process of dealing with that small problem...it's gotten far worse.  Now
I can't login under my user name. I have to switch to tty1 and then it says "Unable to CD to /home/dimeo"


When booting the progress indicator stops halfway. If I boot into safe mode and startx under root, and I try to change the configuration for eth0 (to get my internet to work!) I get this error "The configuration could not be loaded You are not allowed to access the system configuration". Root can't access it WTF? I think it's sad that the only advice so far is to reinstall.  I really do not want to 'just reinstall' edgy after putting dozens of hours into setting up this OS that people claim is stable.

Here's the solution I found:

Boot into safemode and enter these commands: (except use your own username)

sudo chmod 755 /home
sudo chown username /home/username/.dmrc
sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username
sudo chmod 755 /home/username

---

### Post by gonr on 2007-03-11
Coincidentally, I am also named Allan and I had the exact same error as thompa today
(unable to cd to `/home/allan' for user `allan' and other errors), however until this my system had been running fine for a couple years .

After a few hours of searching I found that the permissions on my root directory itself had been screwed up:
ls -ld /    
drwx------  23 root root 4096 2007-03-11 10:40

So, the solution for me is just 
chmod 755 /
(from single user mode)

For some reason I don't understand checkinstall ended up changing the permission of the root directory when I tried to use it to install something. The next time I tried to open a new terminal, gdm and X crashed and I couldn't log in anymore.

---

