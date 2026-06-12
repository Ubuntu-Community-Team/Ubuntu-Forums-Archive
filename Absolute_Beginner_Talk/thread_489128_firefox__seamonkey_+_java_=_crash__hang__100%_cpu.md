---
title: "firefox / seamonkey + java = crash / hang / 100% cpu"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by nanotube on 2007-07-01
hey all
i'm having this weird problem with the java plugin for firefox. here are all the details and all the things i have tried.

1. basic background: it used to work just fine, but at some point a few weeks ago it stopped working. i don't recall that i installed/changed anything, but at this point i obviously may not have perfect memory of the occasion... i'm running feisty, with gnome. no beryl. 

2. what happens is that when i go to a site with a java applet in it, firefox will start eating up 100% of cpu, and hanging. I have discovered that if i wait for about 3 minutes, it finally finishes doing what it is doing, and loads the applet. subsequently, i can load java applets without waiting - but only until i quit the browser. then it has to go through the 3 minute cpu chugging session again upon the next start.

3. this also happens with seamonkey, using the java plugin.

4. when starting with a fresh profile (moving the ~/.mozilla folder out of the way), things are a bit different: i get the little java logo in the place on the page where the applet should be, it says loading, but still nothing happens. sometimes, but not all the time, it also starts eating 100% cpu. but it still fails to do anything.

5. moving ~/.java folder out of the way doesn't do anything.

6. this happens both with the repositories version of firefox, as well as with the official mozilla build (as installed with [ubuntuzilla]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla")), both with fresh profile and with the old one.

7. i have tried uninstalling/purging the sun-java-bin sun-java-jre and sun-java-plugin packages and reinstalling, both version 5 and version 6, and there's no change.


please, can anyone think of anything else i could try to make it work? it would be mighty nice to have working java plugin again! thanks a lot to anyone who can help!

edit: updated item 2: browser recovers after about 3 minutes of eating cpu and hanging.

---

### Post by nanotube on 2007-07-01
*bump*

---

### Post by nanotube on 2007-07-02
bump again...

---

### Post by Raineer on 2007-07-02
I tend to have more luck with Firefox installing the 1.5 version plugin from Sun's website... Just a sec and I'll get the link

I followed [these]("http://java.com/en/download/help/5000010500.xml#selfextracting") instructions to get mine up and running well. I don't know why but a lot of people report issues with other packages (I had some trouble too).

---

### Post by Seisen on 2007-07-02
Are you running a 64-bit computer?

---

### Post by nanotube on 2007-07-02
> **Seisen said:**
> Are you running a 64-bit computer?

no, just regular old feisty 32bit...

---

### Post by nanotube on 2007-07-02
> **Raineer said:**
> I tend to have more luck with Firefox installing the 1.5 version plugin from Sun's website... Just a sec and I'll get the link

I followed [these]("http://java.com/en/download/help/5000010500.xml#selfextracting") instructions to get mine up and running well. I don't know why but a lot of people report issues with other packages (I had some trouble too).

hm, well, since it /used/ to work just fine and then stopped, i suspect that there's a config file or something that messes things up that just needs to be removed. i'd rather stick with the repositories version of java and solve the problem, if i can, instead of going out-of-repo. i'll keep this in mind if all else fails, though, so thanks. :)

---

### Post by nanotube on 2007-07-02
bump? :)

---

### Post by alienexplorers on 2007-07-02
I have a simular problem that when I run firefox with tabs open. Also java and flash running I get extremely high cpu readings and then it hangs.

---

### Post by nanotube on 2007-07-02
i updated the original post. i have found that after 3 minutes of eating cpu, browser recovers, and java applet loads. subsequently, while the browser is open, applets load just fine without delay, but only for the duration of the session, until quitting the browser.

i hope that helps someone diagnose the problem...

---

### Post by nanotube on 2007-07-03
bump...

---

### Post by nanotube on 2007-07-04
bump

---

### Post by ellgor on 2007-07-04
Hi,

Have found that the best java application is the J2re 1.4(Blackdown) which is on the synaptic manager (with all the repositries enabled) there is a mozilla plug in right underneath and I would load that as well. It is self loading and during install you will get a licence to agree to, after that it loads automatic, it doesnt enable all plugin's but it loads the main applet with no bother, hope this helps.

Regards, Ellgor.

---

### Post by agurk on 2007-07-14
nanotube, if you're still watching this topic, you might want to try creating a fresh Firefox profile.
Note that this will deprive you of your settings, bookmarks, history, cache, certificates, etc.

1. Close Firefox
2. Move the content in your ~/.mozilla/firefox folder to a safe place
3. Start Firefox

Just move the old files back again if it didn't help.

---

### Post by nanotube on 2007-07-15
> **agurk said:**
> nanotube, if you're still watching this topic, you might want to try creating a fresh Firefox profile.
Note that this will deprive you of your settings, bookmarks, history, cache, certificates, etc.

1. Close Firefox
2. Move the content in your ~/.mozilla/firefox folder to a safe place
3. Start Firefox

Just move the old files back again if it didn't help.

hi agurk
thanks for your comment - but if you'll note the original post, bullet item 4, this has been tried without success. :|

for now, i have just decided to live with the 3 minute wait time to launch the first java applet of the session... but if you have any other ideas, i'd be glad to hear them.

---

### Post by agurk on 2007-07-15
Ouch, sorry, missed that.

I have a couple of more suggestions; try creating a new computer account to see if it works, and also try disconnecting any peripheral equipment other than mouse and keyboard.

Another long shot would be to add your computer's hostname to your /etc/hosts file, something that has solved a couple of (although non-java related) hanging problems for me in the past. Like this:
```
127.0.0.1 localhost your_hostname
127.0.1.1 your_hostname
```

**Edit**: Oh, and try disabling ipv6 if you haven't already:
> gksudo gedit /etc/modprobe.d/aliases

Change

alias net-pf-10 ipv6
to
alias net-pf-10 off

Reboot.

Validate with
lsmod | grep v6
Should return nothing.

---

### Post by nanotube on 2007-07-24
thanks, i have yet to try these, (been away most of last week) but once i do i'll post back here with the results!

---

### Post by fabianwong on 2008-03-09
I had this problem. firefox uses 100% cpu for three minutes when visiting a java website.

This is because the loopback interface is not plumbed with the address 127.0.0.1

"ifconfig lo" shows no address and "route" shows no route. The below is wrong.

root@kitchen:/etc/rc.d# ifconfig lo
lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@kitchen:/etc/rc.d# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
root@kitchen:/etc/rc.d#



Add the address 127.0.0.1 to the lo interface and add a route.

/sbin/ifconfig lo 127.0.0.1
/sbin/route add -net 127.0.0.0 netmask 255.0.0.0 lo

"ifconfig lo" now shows the address 127.0.0.1 and "route" shows a route. The below is correct .

root@kitchen:~# ifconfig lo
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


root@kitchen:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
loopback        *               255.0.0.0       U     0      0        0 lo
root@kitchen:~#

Note. I've snipped out my other interface details .

---

### Post by nanotube on 2008-03-11
well, the lo interface has the ip address properly on my machine
i didn't see the loopback route (although connecting to localhost worked fine), so i added it as per your suggestion. that didn't help, unfortunately. 

i still haven't tried turning off ipv6... i don't use java-d websites much at all, and i don't reboot much either, so haven't gotten around to it. i'll try that next.

---

### Post by doorknob60 on 2008-03-19
I have similar problems on my computer, although not as bad. My CPU usage shots to 100% (when I load Runescape) and stays there until I stop using Java. Luckily, the browser only hangs for a few seconds at the most and then it works fine. Also, I've yet to see if Hardy makes a difference (just switched), but I'm gonna hppe for the best :) I'll check back here because this is really annoying (I use Java a lot).

---

### Post by doorknob60 on 2008-03-19
Things seem to be going much better in Hardy than they were in Gusty for me :D I'm finally pretty satisfied with Java's performance in Ubuntu on this computer.

---

