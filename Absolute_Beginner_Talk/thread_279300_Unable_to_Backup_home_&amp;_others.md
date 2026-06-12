---
title: "Unable to Backup /home &amp; others"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-10-17
Hi, I want to backup or copy important files to DVD&/orCD,. I have searched your forum and HowTo's - and found exactly what I wanted.

/home /boot /root/ /var /etc  ,,,,,,,,,,,,,,,,,,,,,,,,,the ones to backup

The CL:-
tar clfvz - /home > /home.tgz

And the result is:-......................

joe@Joes-pc:~$ tar clfvz - /home > /home.tgz
bash: /home.tgz: Permission denied
joe@Joes-pc:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
joe@Joes-pc:~$ tar clfvz - /home > /home.tgz
bash: /home.tgz: Permission denied

I must be doing something wrong, there was no mention in the thread about being in root. sudo clearly wont work, any help will be appeciated, including pointers to FAQ/HowTo's - I do try to research before asking; how many of us asking here realise that this is knowledge for nothing for goodness sake(kfnfgs)?
Sarum

---

### Post by catlett on 2006-10-17
put sudo before the command but keep them in the same line 
```
sudo tar clfvz - /home > /home.tgz
```

---

### Post by sarum on 2006-10-17
I thought I'd replied to you, but can not find it. I think you made a typo because when I left off the second "/" it worked.
Thanks catlett.

---

### Post by towsonu2003 on 2006-10-18
> **sarum said:**
> 
The CL:-
tar clfvz - /home > /home.tgz

just explaining ;)
your command says that (donno about the options, nor about the - there) you want home.tgz under / (the root "folder"). You don't have permissions to do so: you can only read and write as yourself under the "folder" /home/yourusername/

---

### Post by sarum on 2006-10-19
Thankyou for your reply. I'm interested in this because I thought I'd found what I wanted - what to backup and the CLI with which to do it.
'tar clfvz - /home > /home.tgz' didn't work,
I stay with Ubuntu because of this forum - so thanks.
btw. What would be your cli for 'tar clfvz - /home > /home.tgz'
Cheers..............Sarum

---

### Post by towsonu2003 on 2006-10-19
> **sarum said:**
> What would be your cli for 'tar clfvz - /home > /home.tgz'

I would use an external storage unit (a usb drive, an external drive, something like that) and I'd do
> 
cd /media/mounteddrive #mounted drive is the external drive
tar -cvf myhome.tar /home/yourusername/
sudo tar -cvf etc.tar /etc/
sudo tar -cvf root /root/


also have a look at rsync (man rsync) if you will be using an external drive or a network storage unit. I prefer rsync for my backups...

---

### Post by sarum on 2006-10-20
Thanks towsonu, you've actually given me what I was looking for in the first place - backups to external storage.
And yes I'll vote for winmodem support. For me it was the biggest no-no for even trying Linux.
Cheers Sarum.

---

### Post by towsonu2003 on 2006-10-20
> **sarum said:**
> Thanks towsonu, you've actually given me what I was looking for in the first place - backups to external storage.
And yes I'll vote for winmodem support. For me it was the biggest no-no for even trying Linux.
Cheers Sarum.

thanks :)

just to make sure there's no confusion (and because I just noticed the backup medium you wanna use in your first post), rsync won't work with a CD DVD as the external storage ;) 

But it works nicely with a fat32 formatted external drive (like a usb flash, or even better, an external hard drive). it works even better with an ext3 formatted drive, because it actually does a one-way syncronization when the backup & the original mediums are ext3. when it's ext3, it won't copy over everything, it will just copy over what has changed in the original since the last backup (which makes the process much faster). 

have fun :)

---

### Post by sarum on 2006-10-24
Thanks, I've made a note of your comments..Sarum

---

