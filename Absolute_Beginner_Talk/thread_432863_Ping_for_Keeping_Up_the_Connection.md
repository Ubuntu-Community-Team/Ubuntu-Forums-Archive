---
title: "Ping for Keeping Up the Connection"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by userthebuntu on 2007-05-04
Hi,

I have SSH running on my ubuntu computer. It works fine, however the DSL router seems to drop the line when there is no internet activity for some time. I often get a 'connection time-out' when trying to connect via ssh to my computer which indicates me that the router just disconnected from the internet.

How can I make Ubuntu send some kinda ping to some kinda website over and over again (e.g. one ping every 10 minutes..should do eh?) so that the router won't drop the internet connection?

Thanks in advance!

---

### Post by bullgr on 2007-05-04
are you trying to connect via ssh from another computer outside your local network?
if yes go in your router setup and give the option to always connected istead to a time limit with no activity.

if you trying to connect via ssh from another computer inside your local network, then the dsl connection has nothing to do.
no matter the dsl connection drops for a time limit with no activity, you still able to routing.

give some more details to help you...

---

### Post by userthebuntu on 2007-05-04
Oh OK...sorry I didn't give as much detail because I already assumed I was in the picture and only needed someone to provide me with that ping thing.

Anyways here it is: I am trying to connect to my computer via ssh from outside my local network. That is my computer which is running openssh or sshd (I can't remember which one...but ssh is running anyway so let's not worry about it) is connected to the internet via a DSL router.

I've configured the router (a Teledat DSL Router) via telnet such that in the internet access setup menu the option 'idle timeout' is set to zero.

However that didn't help...so I'm guessing that I still need to make my linux computer ping some other computer on the internet constantly just to keep my internet connection alive.

So does anyone know how to go about this?

Thanks everybody

---

### Post by Nikron on 2007-05-04
You're looking for a daemon called cronjob.  There's a 99.99 chance it's already installed on your computer.  Anyway, just input the command "cronjob -e" it should be pretty self explantory.  Here's a howto [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto).

An example of what you could do

```

crontab -e
<in crontab>
*/50 0-23 * * * ping www.google.com -c 4

```

I'm no expert at cron, but I'm pretty sure that'll ping google four time every hour on the fifty minutes mark

---

### Post by userthebuntu on 2007-05-05
Thank you!

---

