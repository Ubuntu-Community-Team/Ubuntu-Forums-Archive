---
title: "Automate Rsync or Unison Remotely"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-06-02
I want to use the rsync protocol to backup my system remotely over an ssh connection. Unison does this 
great, but the trick is to automate it. Has anyone tried this or know any tactics to get this done?

Thanks for your time!

---

### Post by hyper_ch on 2007-06-02
Have a read here:

[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

(I should add there on how to delete older backups automatically after xx days....)

---

### Post by shanepardue on 2007-06-02
Now I feel dumb. That was a little over my head..I guess I was thinking there was a program that made it a 
much easier process. I'll try to wrap my head around that process or find an alternative. I appreciate your quick 
reply and assistance!

---

### Post by hyper_ch on 2007-06-02
well, if you want to setup syncronisation within your lan then you don't need ssh... if you want to set it up accross the internet, then ssh is recommended... the script I have there isn't that difficult to understand... most of it is just assigning variables :)

---

### Post by shanepardue on 2007-06-02
It is within my lan, but unfortunately I have a security paranoia that I can't shake and SSH fills that void. :)

Would there not be a way to schedule unison to run at a certain time of day with the "auto" argument to make it 
completely automatic?

---

### Post by hyper_ch on 2007-06-02
I don't know unison but the howto I made is actually pretty straight forward... just follow the steps...

---

### Post by drmbogo on 2007-06-14
shanepardue,
If you're still looking for answers on this one, I am doing something similar with Unison and crontab. Your best bet would be to read (and re-read :P) the unison manual and the crontab man page, as they can do a much better job explaining than I can.
If your machine is always on, like my office machine, then crontab will work just fine. 
Basically, you would create a profile for unison that specifies what you want to b/u, then call that profile from a crontab entry.
Sorry if this doesn't seem to make much sense: I'm not doing a good job explaining this!
If it'll help I'd be happy to post my unison profile and crontab....
Cheers

---

### Post by shanepardue on 2007-06-14
Thanks! I appreciate the help! I'll look into Crontab for the scheduling of my backups. Thanks!!

---

### Post by shanepardue on 2007-06-15
this looks promising! i've only encountered a couple problems with unison's textual interface.

when i run the command "unison Storage -auto"

I get prompts for password, and yes or no on the transfer. i couldn't find a way to make this part automatic. i do really enjoy crontab and it's ease of use. thanks for that tip!!

---

### Post by kevdog on 2007-06-15
You need to setup a .prf file.  Also once you know what you want to sync, I think you can put a batch statement in the prf file.  Unison compares differences between two files.  When it finds a difference it usually asks you, do you want to keep version a or b.  You can set up some criteria so unison doesnt need to ask you -- something like always have machine a override machine b -- this would be a force command in the .prf file.  If you wanted to keep the most recent version of the file based on time stamp (or inode number in linux), you would place in the prf file times=true.  I think if batch=true, it uses these predetermined criteria, and if a situation arises that these criteria can not be used to solve a file conflict, the file is skipped.

Its all in the unison documentation.  It seems intimidating to use at first, but once you get the hang of it and you set up your .prf file, you kind of use it and forget it/

---

### Post by shanepardue on 2007-06-15
Well, i got a prf file with the directories to sync and such but was unable to find a place to store the password.

I suppose i could choose which directory gets forced to copy, but i thought "-auto" would just go with the defaults without questioning.

---

### Post by kevdog on 2007-06-15
Are you having a problem with typing the password to the ssh keys??  I dont have a password problem.

---

### Post by shanepardue on 2007-06-15
the password works fine, but with an automated cronjob, it wouldn't be able to sync without user interaction defeating the purpose

---

### Post by shanepardue on 2007-06-15
and for the record, forcing one replica to the other still asks for confirmation...

deleted  ---->            registry.png  [f] f

---

### Post by kevdog on 2007-06-15
Between the force and batch command I think that is all you need. 

Can you post your prf file?

---

### Post by shanepardue on 2007-06-15
```
root = /media/Storage
root = ssh://diana@192.168.1.6//media/disk
```

and i ran it with "unison Storage -force /media/Storage"
(Storage is the profile name)

Am I missing something?

---

### Post by kevdog on 2007-06-15
I guess you could do it like that, but make your prf file look like:

root = /media/Storage
root = ssh://diana@192.168.1.6//media/disk

force = /media/Storage
batch = true

or 

force = newer
times = true
batch = true

The first time you run this thing you might want to eliminate the batch=true statement.  This is the last thing you want to make true since after adding this you kind of lose any debug capabilities while testing.

---

### Post by shanepardue on 2007-06-15
cool, the sync occurred without prompting for anything but a password, got any ideas on how to avoid or store a password?

---

### Post by kevdog on 2007-06-15
What password are you talking about???

If you just ssh to the machine (no unison) do you have to type a password???

---

### Post by shanepardue on 2007-06-15
yeah, when i ssh into the computer it asks for a password so when i use unison, it asks for the password of the ssh server to sync with. sorry to confuse. is this an ssh server setting that i'll have to disable or what? i don't want to necessarily go without a password

---

### Post by kevdog on 2007-06-15
Not exactly sure how you would do this -- this is really an ssh problem, and not a unison problem per say.  I know in windows there is pageant -- or putty agent -- that stores the password, but this is only while the machine is turned on.  The minute windows shuts down or another user is logged on, the password needs to be re-entered.  

I remember something a ways back but cant remember....

Hmm you'll have to look around...If you find something let me know.  I dont use passwords on my ssh keys so Ive really never had to overcome this problem.

---

### Post by shanepardue on 2007-06-15
Thanks for your help!

I hope this isn't a dealbuster with the password and all..but i'll let you know if i fnd anything!!

---

### Post by hyper_ch on 2007-06-15
In the howto I posted is also a reference how you can do auto-login through SSH...

---

### Post by shanepardue on 2007-06-19
Thanks hyper_ch for pointing that out..I'll get to setting that up. I appreciate all of the help I've gotten from this thread!

---

