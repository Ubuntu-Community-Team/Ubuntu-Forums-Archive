---
title: "evolution n00b question"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-02-11
so, I have been using evolution only for a few months now. IT is cool. I like it, etc.

However, I have changed some setting and have no idea how to change it back. I find it very annoying so i would like to get the original back up.

If I delete a msg from a mail group/list, or one from a serious of mails (replies  to replies) then evolution automatically jumps to the next msg in that list or volley of replies.

This was not always so. I want to be able to go through the mails and delete them, one bye one, in the order they appear.

Anybody have any idea how to set it up?

thanks

robi

---

### Post by abhiroopb on 2008-03-31
If you haven't used evolution much then simply do a complete uninstall of it and reinstall.

```

sudo apt-get remove evolution --purge

```

then:
```

sudo apt-get install evolution evolution-exchange evolution-plugins

```

NB: ONLY do this if  you don't have anything important in evolution as this will delete mails, settings, calendar information.

In future use File>Backup Settings to save your WORKING settings.

---

### Post by beanco on 2008-05-17
hi,

forgot to get to this thread..

still ahving the reply problem. ie. replies being placed in the list of incoming mail where the original was and not at the newest date.

I have missed a few very important msgs because I did not think to go back and check if there were new messages further back in the line so to speak.

and I have a ton of implortant things in evolution so I will not purge, re install, do you happen to have any other ideas?

also as fo today I get core dumped when I launch from the command line...so I cannot even get evolution open... kind of annoying!!

Robi

---

### Post by janz84 on 2008-05-17
right click the title above the inbox pane, select custom, in the drop down pick date, then select ascending or descending depending if you want new messages appearing from the bottom or the top.

---

### Post by beanco on 2008-05-18
Ok seems easy enogh.

as soon as I can get evolution to launch again I will try it.

robi

---

### Post by abhiroopb on 2008-05-18
Sorry didn't reply...ok open up a terminal and type in evolution and see what happens, if a lot of text shows up in the terminal paste it here please.

---

### Post by beanco on 2008-05-18
> **abhiroopb said:**
> Sorry didn't reply...ok open up a terminal and type in evolution and see what happens, if a lot of text shows up in the terminal paste it here please.


here you go

```
rob@rob-desktop:~$ evolution
CalDAV Eplugin starting up ...
Segmentation fault (core dumped)
rob@rob-desktop:~$ 
```

thanks

robi

---

### Post by abhiroopb on 2008-05-18
try this in the terminal:

evolution --force-shutdown

---

### Post by beanco on 2008-05-18
> **abhiroopb said:**
> try this in the terminal:

evolution --force-shutdown


got this

```
rob@rob-desktop:~$ evolution --force-shutdown
Shutting down evolution-exchange-storage (Evolution Calendar Exchange backend / Evolution Addressbook Exchange backend)
Shutting down evolution-data-server-1.10 (Evolution Calendar file and webcal backend / Evolution Addressbook file backend)
Shutting down evolution-alarm-notify (Evolution Calendar alarm notification service)
rob@rob-desktop:~$ 

```

Then the core dumped msg when I tried to launch evolution

robi

---

### Post by abhiroopb on 2008-05-18
try launching as root:

sudo evolution

---

### Post by beanco on 2008-05-18
> **abhiroopb said:**
> try launching as root:

sudo evolution
got this
```

rob@rob-desktop:~$ sudo evolution
Password:
CalDAV Eplugin starting up ...
Segmentation fault (core dumped)
rob@rob-desktop:~$ 

```

---

### Post by abhiroopb on 2008-05-18
Try this:

evolution --disable-eplugin --offline

(sorry if this seems a bit hit and miss but I'm basically trying out a list of things I think it can potentially be).

---

### Post by abhiroopb on 2008-05-18
I checked other threads and the best option seems to be re-installation (as a badly formatted message may be the culprit), but like you said you need evolution and can't uninstall it. So I suggest posting a bug report or waiting for other advice on this.

---

### Post by beanco on 2008-05-18
ok, I was agraid of that...

how to back up all the mails in the inbox and outbox? and all the contacts/email addresses?

robi

---

### Post by abhiroopb on 2008-05-18
A couple of things, it is easy enough to backup evolution, however, restoring the backed up files may cause the SAME problem again! So, I suggest you wait on this thread, as perhaps someone has the answer.

In any case ALL evolution personal files are located in /home/<user>/.evolution

---

### Post by beanco on 2008-05-18
> **abhiroopb said:**
> A couple of things, it is easy enough to backup evolution, however, restoring the backed up files may cause the SAME problem again! So, I suggest you wait on this thread, as perhaps someone has the answer.

In any case ALL evolution personal files are located in /home/<user>/.evolution

well I am having the same problem with FF and epiphany so I think it is not related to evolution per se.

I hav a thread on the browsers going too but you ar the only one rigth now asnwering... Kind of suck cos I need to get things working well again.

robi

---

### Post by abhiroopb on 2008-05-18
What exactly is the problem with FF? Perhaps we can sort that out at least!

---

### Post by beanco on 2008-05-18
> **abhiroopb said:**
> What exactly is the problem with FF? Perhaps we can sort that out at least!

```
rob@rob-desktop:~$ firefox
Segmentation fault (core dumped)
```

same for epiphany too!

robi

---

### Post by abhiroopb on 2008-05-18
firefox -safe-mode

could be one of you're extensions.

---

### Post by beanco on 2008-05-18
how do you launch in safe mode?

robi

---

### Post by abhiroopb on 2008-05-18
thats the command.

Just type it in: firefox -safe-mode

---

### Post by beanco on 2008-05-18
core dumped



robi

---

### Post by abhiroopb on 2008-05-18
really sorry but I'm totally at a loss. What about other programs? Try installing something or running other programs.

---

