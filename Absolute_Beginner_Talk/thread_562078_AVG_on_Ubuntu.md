---
title: "AVG on Ubuntu"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by FrankBlourtango on 2007-09-28
I did the install from [http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty). I went great. But when I click to Update it tells me I don't have permission to exectue avgupdate.. :(

---

### Post by wieman01 on 2007-09-28
> **FrankBlourtango said:**
> I did the install from [http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty). I went great. But when I click to Update it tells me I don't have permission to exectue avgupdate.. :(
Try "gksu avg" from command line?

---

### Post by por100pre1 on 2007-09-28
You can also use [avast]("http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb") instead. Is gratis too and doesn't ask for super user privileges. Use [this link]("http://www.avast.com/eng/home-registration.php") to register for a gratis key.

---

### Post by ajgreeny on 2007-09-28
Just out of interest, why are these two (AVG and avast) better than clamav and the GUIs available for that?

---

### Post by FrankBlourtango on 2007-09-28
I don't know that any are better than others.  I'm just trying to get SOMETHING to work.

I tried the gksu avg   I don't get any error or anything but it doesn't look like it's doing anything.

---

### Post by Amazona aestiva on 2007-09-28
> **FrankBlourtango said:**
> I don't know that any are better than others.  I'm just trying to get SOMETHING to work.

I tried the gksu avg   I don't get any error or anything but it doesn't look like it's doing anything.

You should try:
```
gksudo avggui
```

---

### Post by qamelian on 2007-09-28
> **ajgreeny said:**
> Just out of interest, why are these two (AVG and avast) better than clamav and the GUIs available for that?

I can't think of one reason. Although I like both Avast and AVG on Windows machines, clamav is always my first choice on my Linux boxes. In a recent test of multiple AVs, ClamAV tied for first place with Symantec and Kaspersky as the only AVs to detect 100% of the viruses in the test set of malware used. McAfee came in second with only 89%.

---

### Post by FrankBlourtango on 2007-09-28
Well gksudo avggui  did the trick.  Thanks  Amazona!!

Now what did that do?  Give me SU rights to the avg gui ?

---

### Post by bigken on 2007-09-28
you could also type this in a terminal 

sudo adduser username avg

---

### Post by Amazona aestiva on 2007-09-28
> **FrankBlourtango said:**
> Well gksudo avggui  did the trick.  Thanks  Amazona!!

Now what did that do?  Give me SU rights to the avg gui ?

It gave you root permission to everything.

---

### Post by HermanAB on 2007-09-28
If you are just playing and learning, then that is cool, but seriously, unless you are serving email to a bunch of other machines, you don't need anti-virus on Linux (and if you do serve email to other users, then you need a whole mail system with Spamassassin and ClamAV).

Here is why: [http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

You are running Linux, relax and enjoy it.  You don't need to worry about Windows crud.

Cheers,

H.

---

### Post by Perfect Storm on 2007-09-28
I'll second what HermanAB said. It's a waist of good space. :guitar:

If anything you need on the safe side (mostly used for servers) is rootkit.
Get rid of the anti-virus and install; chkrootkit and rkhunter, it's in the repo.

---

### Post by qamelian on 2007-09-28
> **Artificial Intelligence said:**
> I'll second what HermanAB said. It's a waist of good space. :guitar:

If anything you need on the safe side (mostly used for servers) is rootkit.
Get rid of the anti-virus and install; chkrootkit and rkhunter, it's in the repo.

While an anti-virus might not be necessary to protect your linux box, you could still forward infected emails to someone using Windows. If you never forward emails, then fine but most people I know do forward at sometime or another. Not using an anti-virus is irresponsible and is like saying that only other drivers on on the road need to watch their driving.

---

### Post by Kilz on 2007-09-28
> **qamelian said:**
> While an anti-virus might not be necessary to protect your linux box, you could still forward infected emails to someone using Windows. If you never forward emails, then fine but most people I know do forward at sometime or another. Not using an anti-virus is irresponsible and is like saying that only other drivers on on the road need to watch their driving.

Yes hence why they said if you run a mail server. Most of the linux anti virus applications are command line scanners that only work if you ask them to check files. They dont constantly scan. Besides. If you are a single user, why would you chose to forward infected attachments to friends? The reason most things are pased on in Windows is because the machine is infected. Since you have Linux, you wont be infected, so you will have to purposely send the infected file.

---

### Post by skymera on 2007-09-28
ok it isnt needed for linux. you can get if your paranoid.

you should get it if you download files ans pass them tyo YOUR windows box.

who cares if you send bad emails to other people?

they should have their OWN AV

---

### Post by bruce89 on 2007-09-28
Viruses aren't distributed in e-mails these days I notice.

---

### Post by skymera on 2007-09-28
some are.

unless you are stupid enough to click it.
you are safe.

Limewire isnt smart either, Spider Man 3 FULL MOVIE! 600kb.? i wonder...

---

### Post by Kilz on 2007-09-28
> **skymera said:**
> some are.

unless you are stupid enough to click it.
you are safe.

Limewire isnt smart either, Spider Man 3 FULL MOVIE! 600kb.? i wonder...

In this case I would say let the person who was stupid enough want to download illegal content get what they have coming.

---

### Post by qamelian on 2007-09-29
> **Kilz said:**
> Yes hence why they said if you run a mail server. Most of the linux anti virus applications are command line scanners that only work if you ask them to check files. They dont constantly scan. Besides. If you are a single user, why would you chose to forward infected attachments to friends? The reason most things are pased on in Windows is because the machine is infected. Since you have Linux, you wont be infected, so you will have to purposely send the infected file.

And if your mail client isn't passing the message through an anti-virus, how are you going to know if it is infected? Every Linux email client I have used can be configured to pass messages through your anti-virus during your mail check. If you don't do this you could be passing on infected messages.

Yes, the windows user should have their own AV, but that doesn't excuse you from being irresponsible and not scanning received messages before passing them on to someone else. Whether or not you are running your own mail server has nothing to do with this. It's about taking responsibility for information you are disseminating.

---

