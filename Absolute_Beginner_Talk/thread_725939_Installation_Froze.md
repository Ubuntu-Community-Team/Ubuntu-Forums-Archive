---
title: "Installation Froze"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-16
While installing Ubuntu Gusty... it froze (see attachment)
what should I do?

---

### Post by erginemr on 2008-03-16
This (esp. the nubemr 82%) is a classical example of server unerachable error, while the installer is trying to fetch the updats to the packages in the Live CD. All you need to do is to disable your network card (unplug, remove its cable, etc.) and carry on with the installation.

---

### Post by perito on 2008-03-16
i waited and it continued but gave an error (security updates unreachable or something like that) but the system installed successfully
should I do anything? or use the system as is?

---

### Post by erginemr on 2008-03-16
Also following this lik:
[http://ubuntuforums.org/showthread.php?t=580129](http://ubuntuforums.org/showthread.php?t=580129)

Changing your download server from under Synaptic - > Software Repository can also help.

---

### Post by erginemr on 2008-03-16
> **perito said:**
> i waited and it continued but gave an error (security updates unreachable or something like that) but the system installed successfully
should I do anything? or use the system as is?

Don't worry, your system has been installed succesfully. There has probably been a temporary server-down incident. Try using Main Menu -> Admin -> Update Manager to install latest security updates later today. Also make sure that you have enabled all repositories from Main Menu -> Admin -> Software Sources.

If the problem persists, try changing your repo server to a different one from Software Sources.

---

### Post by Drakkor on 2008-03-16
That happened to my installation also,just let it go,and it'll finish by itself :)

---

### Post by bumanie on 2008-03-16
My experience had been that this is due to the ipv6 problem that many have had with gutsy gibbon. The install finished fine, but you will have to probably disable ipv6 before being able to connect to the internet.

---

