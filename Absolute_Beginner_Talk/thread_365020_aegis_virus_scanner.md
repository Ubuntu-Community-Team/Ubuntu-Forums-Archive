---
title: "aegis virus scanner"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by sasquatch606 on 2007-02-19
I just installed aegis virus scanner and it keeps telling me that I need to update to a newer version and it runs through and tells me to restart aegis and then it keeps doing it.  Is there a command to update it through the terminal?  I'm new to Linux so I apologize.  Also, how would I unistall it if I wanted to?

---

### Post by zvacet on 2007-02-19
Try 
```
sudo apt-get update
```
You can uninstall it with synaptic.

---

### Post by viper on 2007-02-19
Possibly try Automatix, then install Clam AV. Works very well..........

---

### Post by mahiyar on 2007-02-19
I used AVG anti virus from this how to [http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg+antivirus](http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg+antivirus), worked flawlessly.

---

### Post by nonewmsgs on 2007-02-19
is a virus scaner necessary?

---

### Post by tronica on 2007-02-19
I don't use one, but it sure can't hurt

---

### Post by CCBalla10 on 2007-02-19
> **sasquatch606 said:**
> I just installed aegis virus scanner and it keeps telling me that I need to update to a newer version and it runs through and tells me to restart aegis and then it keeps doing it.  Is there a command to update it through the terminal?  I'm new to Linux so I apologize.  Also, how would I unistall it if I wanted to?

try uninstalling it and installing again using sudo apt-get install aegis-virus-scanner....had to do it and it worked the second time.  Good Luck

---

### Post by ramjet_1953 on 2007-02-19
Unless you are sharing files with a Windows machine, or have a Windows partition, you don't really need a virus scanner. All it does is chew-up system resources.

Your best bet is to install Firestarter and have it running while you are on-line. It will alert you if someone is trying to penetrate the firewall.

Regards,
Roger :cool:

---

### Post by matchstich on 2007-07-22
> **CCBalla10 said:**
> try uninstalling it and installing again using sudo apt-get install aegis-virus-scanner....had to do it and it worked the second time.  Good Luck


i tried this a couple of times anf it still won't update.

---

