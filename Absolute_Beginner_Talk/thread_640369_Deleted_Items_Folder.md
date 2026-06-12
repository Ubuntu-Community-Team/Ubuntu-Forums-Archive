---
title: "Deleted Items Folder"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by dchurch24 on 2007-12-14
Hi all,

For some reason, despite not using the machine for 2 days, it has used up 13gb of space - I am trying to determin the cause as we speak.

However, in the meantime of course the machine cannot be logged in due to lack of disc space - I fixed this last time by VNCing to the box and emtying the 'Deleted Items folder", however, this time it won't start VNC server remotely, but I can PuTTY to the box - of course, I have emptied the .Trash folder, but this seems to be different from the 'Deleted Items folder'.

So, 2 questions really:

1) How do I delete the Deleted Items folder over PuTTY (i.e. what is the path), and
2) Why is there effectively 2 'trash' folders?

I thought that deleting things would move them to the .Trash folder; empty that and you have freed up the space.

Help would be appreciated as after doing a df -h I am at 100% usage when I know for a fact that I have used about 50% of the disc...and to use 13gb in 2 days when the machine wasn't being used is a bit odd (I think this may be a MythTV problem).

---

### Post by natehall on 2007-12-14
Can you start up the system with a cdrom disk? If that works you can examine the files that way.

---

### Post by dchurch24 on 2007-12-14
I will try that when I get home - thanks.

However, at the moment, I am at work and am SSHed into the box, trying to get it so my GF at home can use the machine!! Lol.

I just need to be able to look in the Delete Items Folder I think and get rid of what's in there so she can log in and then I can figure out why it's using disc space so quickly.

---

### Post by dchurch24 on 2007-12-14
Also, how would I list ALL files on the volume in order of reverse date - so I can see what files have been amended/added last - this might give me a clue as to what is using the disc space so quickly.

---

### Post by hyper_ch on 2007-12-14
you could use "du" to find out where all the space is used.

(1) Go first to your root directory and create a output.txt file and chown it your USER
```

cd /
sudo touch output.txt
sudo chown USER.USER output.txt

```

(2) run du and save results in the output.txt file
```

du -h > output.txt

```

(3) Open the output.txt and find out where all your space goes to

---

### Post by dchurch24 on 2007-12-14
Sounds like a good idea to me! ;-)

However, I get permission denied on that file once I have done that.

I even did a chmod 777 output.txt just to be sure.

What am I doing wrong?

(I have a massive toothache at the moment too, so am prone to making stupid mistakes)

---

### Post by natehall on 2007-12-14
Try  ls -l to see what your permissions are.

---

### Post by dchurch24 on 2007-12-14
Hi, here's the results:

```

-rwxrwxrwx   1 dave dave     0 2007-12-14 11:06 output.txt

```

Looks ok to me. Very odd.

---

### Post by dchurch24 on 2007-12-14
Ahh - just got it!!

There's no disc space left to write to the file, despite a df -h giving this:

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             **352G  342G**     0 100% /
varrun                3.8G  260K  3.8G   1% /var/run
varlock               3.8G     0  3.8G   0% /var/lock
procbususb            3.8G  124K  3.8G   1% /proc/bus/usb
udev                  3.8G  124K  3.8G   1% /dev
devshm                3.8G     0  3.8G   0% /dev/shm
lrm                   3.8G   39M  3.8G   1% /lib/modules/2.6.20-16-generic/volatile
/dev/sdc1             233G   74G  160G  32% /mnt/win2


```

God, I'm getting confused now.

Surely that says that there is 10gb free on /dev/sdb1 doesn't it? How can there be 0 available?

I'm deleting files wildly (rm * in folders), yet it's creating no space and my .Trash folder is empty.

---

### Post by natehall on 2007-12-14
try sort -n output.txt

---

### Post by Ocxic on 2007-12-14
check to root's trash

---

### Post by dchurch24 on 2007-12-14
I don't think it's going to help - I have 0 bytes left available on the volume so it won't write.

I just don't seem to be able to clear any space despite deleting loads of files.

I just don't get it.

---

### Post by dchurch24 on 2007-12-14
> **Ocxic said:**
> check to root's trash

I can't for some reason, I get Permission Denied. I try to SU but it says my password is wrong, which I know it is not - this couldn't be a symptom of running out of space could it?

Is there a way to change the root password so I can put this to the test?

---

### Post by natehall on 2007-12-14
Perhaps rm .Trash will give you enough room.

---

### Post by dchurch24 on 2007-12-14
Just checked /root/.Trash - it's empty!

I'm really at a loss now - how can df -h say there is 10gb free, but available 0 ?

Is this something to do with the Deleted Items Folder rather than .Trash?

It's getting to the point where I seem to be deleting everything on the drive except from the OS - and yet STILL having no room left.

That can't be right, surely.

---

### Post by natehall on 2007-12-14
> **dchurch24 said:**
> 

Is there a way to change the root password so I can put this to the test?

You have to do that on the machines start up. By the way the Ubuntu book says if you're running out of space to use applications>Acessories> Disk Usage Analyzer. i suspect it won't work in your case.

---

### Post by dchurch24 on 2007-12-14
It really is quite bizarre as I'm not actually running about of space.

About a week ago, I had over 100gb spare - now not a single byte spare.

I've not been downloading 100gb in one week - my ISP might have a few words if I had ;-)

I am at a loss to understand it to be honest.

If this were Windows, I'd think I had a virus.

---

### Post by dchurch24 on 2007-12-14
Ahhh - ok, found it.  Thanks for your help guys (especially for 'df' I'd not used that before).

It was my backups - for some reason they are now backing up to my main volume and not my external drive.  I don't remember changing it, but I doubt very much it changed itself!!!

---

### Post by dchurch24 on 2007-12-14
Just a quick one now then (ha!):

Doing a ps -A shows up a process called "system-tools-ba" - could this be the backup software I installed all those moons ago?

I obviously need to find this software and reconfigure it to point at my external drive once again?

---

### Post by hyper_ch on 2007-12-14
dunno

I do my backups with a self-written script using rsync, cron and the power of hardlinks.

---

### Post by dchurch24 on 2007-12-14
Fair enough - I may well follow your example TBH.

Thanks for all the help guys, really appreciated!

---

