---
title: "limewire and frostwire"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-02-12
any knowledge would be helpful please.I have frostwire and limewire installed on my ubuntu edgy.neither one of them do anything when I click on the icon in applications>internet.so if there is anybody out there that might know something please help!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by rsambuca on 2007-02-12
You require java do be installed for these to work.

---

### Post by Timmy66 on 2007-02-12
I installed the latest version of jave last night

---

### Post by sda5150 on 2007-02-12
I was having performance issues with Frostwire. The application sometimes wouldn't start, sometimes it would close for no reason, sometimes it would freeze, sometimes it would throw me to the login screen.

In the end it was a faulty RAM module that was causing these symptoms. Why, not sure, maybe these apps require more memory that other apps on my machine? not sure.

---

### Post by rsambuca on 2007-02-12
Also, if you have beryl installed you have to run a special script to run frostwire at the same time.

Which java version do you have running?

---

### Post by Timmy66 on 2007-02-12
version 1.5

---

### Post by rsambuca on 2007-02-12
Is that the sun-java5-jre?  Just try this in the terminal```
sudo apt-get install sun-java5-jre
```

---

### Post by Timmy66 on 2007-02-12
couldn't find the sun package.that was the message that I got

---

### Post by rsambuca on 2007-02-12
No problem.  You will just have to enable the "multiverse" repositories first.  Perhaps the easiest way is to go to your Main Menu and click:

System -> Administration -> Software Sources

Make sure to check the box that says "Software restricted by copyright or legal issues (multiverse)

After that you can enter in a terminal```
sudo apt-get update
```
and then ```
sudo apt-get install sun-java5-jre
```

That should do it.

---

### Post by Spike-X on 2007-02-14
> **rsambuca said:**
> Also, if you have beryl installed you have to run a special script to run frostwire at the same time.


Can somebody talk me through this please?

Also, when I start Frostwire, it never connects, it just stays on 'Starting Connection'. What do I need to do to get it to connect? I'm using the 64-bit version of Ubuntu, and Frostwire is a 32-bit program. Would that be the problem?

---

### Post by rovernaut on 2007-02-14
your connection problem is probably a fire wall blocking it.
 Disable your firewall if running one ans see it it connects.If it does then you may have to forward a port or configure your firewall to allow limeware

---

### Post by Spike-X on 2007-02-14
I'm not running a firewall. I'll try port forwarding. Thanks!

---

### Post by Spike-X on 2007-02-14
Ok, I've done port forwarding, but it's still stuck on 'Starting Connection'.

---

### Post by ThrobbingBrain66 on 2007-02-14
[http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire](http://ubuntuforums.org/showthread.php?t=315222&highlight=frostwire)

give that howto a shot.  it should sort you out.

---

### Post by Spike-X on 2007-02-14
Thanks!

I actually found that solution through other means - I found a thread that had a link to a list of alternate sources, but the link was broken. Then I got the brainwave to copy the list from my Limewire installation on Windows (which looks to be the same as the one on the link you posted there), and it worked!

---

