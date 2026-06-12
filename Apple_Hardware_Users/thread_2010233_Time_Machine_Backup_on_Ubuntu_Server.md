---
title: "Time Machine Backup on Ubuntu Server"
date: 2012-06-25
forum: Apple Hardware Users
---

### Post by hollywoodpete on 2012-06-25
My wife has a Mac Book Pro that has been a real problem for her. It shuts down and crashes and she looses data. I could score some serious "Brownie Points" if I could set her Time machine to back up on a server. I have followed several guides but still have been having problems setting permissions, adding her as a user and getting a drive mounted. I have a 1 Tb drive I am willing to let her use exclusively for the backup. Her Time Machine currently will recognize the server but gives a OSStatus error 2 when I try to connect. Any help or direction to a current guide would be appreciated

---

### Post by Alevins5 on 2012-06-28
I actually just completed [[COLOR="DarkOrange"]this guide[/COLOR]]("http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/") yesterday, and everything seems to be working. Yesterday I set it up to back up to one of the internal hard drives on an old computer tower that I installed Ubuntu onto, but stopped it before it could finish. Today I was able to get it to recognize an external hard drive by following this guys instructions. It's backing up right now as I type this. It has its quirks, like for example the first time I tried to back up it would only find 28 gigs to back up, but then of that it would only backup less than a gigabyte. I am trying again now, though, and Time Machine seems to be recognizing my entire hard drive and sending it over to the external I have on the server. 

Again, this is the link: [http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/](http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/)

I'll let you know how everything turns out if you're interested. And if it works I'd be happy to help you troubleshoot any issues you're having, although I have a rather limited knowledge on the subject. But anyways, hope this helps! It might not work flawlessly, but it's much cheaper (it's free!) than purchasing a mac mini to use as a server or a time machine router combo from Apple!

Just to comment on the quality of over the air backups, it is SLOW going! Man, is it ever slow. I have a decent router, too. It's just a lot slower than USB. Probably because both the server and my macbook pro are relatively far from the router. But hey, it's wireless. And there will be less data to backup once I have the initial backup completed.

---

### Post by hollywoodpete on 2012-11-12
> **Alevins5 said:**
> I actually just completed [[COLOR=DarkOrange]this guide[/COLOR]]("http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/") yesterday, and everything seems to be working. Yesterday I set it up to back up to one of the internal hard drives on an old computer tower that I installed Ubuntu onto, but stopped it before it could finish. Today I was able to get it to recognize an external hard drive by following this guys instructions. It's backing up right now as I type this. It has its quirks, like for example the first time I tried to back up it would only find 28 gigs to back up, but then of that it would only backup less than a gigabyte. I am trying again now, though, and Time Machine seems to be recognizing my entire hard drive and sending it over to the external I have on the server. 

Again, this is the link: [http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/](http://pwntr.com/2012/03/03/easy-mac-os-x-lion-10-7-time-machine-backup-using-an-ubuntu-linux-server-11-10-12-04-lts-and-up/)

I'll let you know how everything turns out if you're interested. And if it works I'd be happy to help you troubleshoot any issues you're having, although I have a rather limited knowledge on the subject. But anyways, hope this helps! It might not work flawlessly, but it's much cheaper (it's free!) than purchasing a mac mini to use as a server or a time machine router combo from Apple!

Just to comment on the quality of over the air backups, it is SLOW going! Man, is it ever slow. I have a decent router, too. It's just a lot slower than USB. Probably because both the server and my macbook pro are relatively far from the router. But hey, it's wireless. And there will be less data to backup once I have the initial backup completed.

Thanks for the help. I got it to work but just as you found , the WiFi is miserably slow for a backup. I have a USB hard drive that has turned out to be a better option

---

