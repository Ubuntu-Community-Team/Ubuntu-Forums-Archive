---
title: "Firestarter question"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by mmmpancakes on 2006-08-21
Hi all. I want to make sure I'm properly taking care of my Ubuntu installation by using a solid firewall. I heard Firestarter was good, so I'm using that. I notice that I have to start the program manually everytime I boot into Ubuntu (annoying, and scary in the event I forget to start it). I notice there was a setting to have it start automatically at boot up, but it doesn't. 

Also, I notice when it does run, there's no activity log. When I run ZoneAlarm in Windows, the firewall blocks activity pretty regularly. Firestarter doesn't seem to be showing any blocked activity. Should I be concerned?

---

### Post by jdong on 2006-08-21
Firestarter by default does run at bootup in the background, using the most recent settings the GUI set. Just because the GUI isn't running doesn't mean you're not protected.


You really don't need a firewall to protect your Ubuntu install, as there are no open/exploitable ports by default.

---

### Post by mmmpancakes on 2006-08-21
> **jdong said:**
> Firestarter by default does run at bootup in the background, using the most recent settings the GUI set. Just because the GUI isn't running doesn't mean you're not protected.


You really don't need a firewall to protect your Ubuntu install, as there are no open/exploitable ports by default.

I see. I thought because I don't see the blue Firestarter bubble in the top right, that it wasn't active. I had always heard Ubuntu did indeed require a Firewall, so I appreciate you clearing that up for me very much.

---

### Post by jdong on 2006-08-21
Typically people keep their firstarter in the tray because it's cool to watch it in "real time", but the protection is always active regardless of whether or not the program is running.

There have been previous "debates" in the security forum on whether or not a firewall is necessary, and nobody's been able to come up with a good reason why the average Ubuntu user would gain any more security from deploying something like firestarter.

---

### Post by mmmpancakes on 2006-08-21
So when ZoneAlarm in Windows is showing blocked incoming activity, and Firestarter shows nothing of the sort, is that a testament to the security instabilities of Windows?

---

### Post by jdong on 2006-08-21
It's more of a testament to Zonealarm trying to sell you snake oil by scaring you in an unnecessary manner.

For example, someone probes you on port 58000. Chances are, you've got nothing running on port 58000. Zonealarm pops up an alert that says it "stopped a hacker dead in its tracks".

So, what did Zonealarm do? Absolutely nothing. If you didn't have zonealarm, Windows would've stopped the attack in the exact same way: reject the probe to 58000 because nothing is running.


From a security standpoint, the time a firewall helps you in inbound connect attempts is when there is an open port on your system. Let's say you accidentally left Windows File Sharing turned on for your public network interface. Now, if someone tries to access Windows File Sharing, Zonealarm will block the attempt. Now, Zonealarm has protected you. You can easily get the same level of "protection" by turning **off** Windows File Sharing on the public network interface. In other words, a firewall is just acting as a "mask" over your real security problems.


If you'd like to keep your computer secure from this, run regular port scans to make sure nothing is accidentally being exposed to the public. That's a much better security approach than blindly applying firewalls everywhere :)

---

### Post by mmmpancakes on 2006-08-21
Great information! Thanks for all the thoughtful replies, and know that you played a -significant- role in helping me sleep better at night!

---

### Post by TheRingmaster on 2006-08-21
is it the same thing with the clamav antivirus too. Does it stay on all the time?

---

### Post by jdong on 2006-08-21
> **jpazindustries said:**
> is it the same thing with the clamav antivirus too. Does it stay on all the time?

Only if you install the daemon... But then again, why are you running clamav? I don't see any "protection" that it'd provide...

---

### Post by ice60 on 2006-08-21
you can use these commands to see if firestarter is running and to stop and start it too.

sudo /etc/firestarter/firestarter.sh status

sudo /etc/firestarter/firestarter.sh start

sudo /etc/firestarter/firestarter.sh stop

if it isn't starting up you can put it in sessions. make sure you use gksudo firestarter and not sudo if you do put it in sessions.

---

### Post by ice60 on 2006-08-21
> **jpazindustries said:**
> is it the same thing with the clamav antivirus too. Does it stay on all the time?
i have freshclam running which is the update server so it stays up-to-date. it means you can just run it without having to update it first. it should be running if you have clam.
```
sudo /usr/bin/freshclam status
```
```
ps -e | grep freshclam
```

there's a nautilus script you can use to put the scanner in the right-click menu too.
[http://www.ubuntuforums.org/showthread.php?t=104001](http://www.ubuntuforums.org/showthread.php?t=104001)

---

### Post by Elaztic on 2006-08-22
Hey Ice60.

Thank you for the answer regarding Firestarter in startup.
Works like a charm...

Kind regards.

---

