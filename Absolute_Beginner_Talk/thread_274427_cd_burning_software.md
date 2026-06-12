---
title: "cd burning software"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by jasonsexton on 2006-10-09
I have been using Serpentine Audio Cd Creator and it was working fine.  Recently I have been getting an error, "Writing to disc didn't start so it is still usable"  Anyone know how to fix this issue.  Or can anyone recommend another program for burning audio cd's?
thanks!

---

### Post by tagra123 on 2006-10-09
Have you tried rebooting?

K3B is a decent burning tool..

---

### Post by jasonsexton on 2006-10-09
yes, rebooting did not change anything
I'll look into k3B

---

### Post by Iron-Monk on 2006-10-09
I don't know if it is an actual problem with the cdburning tools itself but, a cd burning program i use a lot is gnomebaker. Just have used it for a long time and always liked the gui.

---

### Post by AndyCooll on 2006-10-09
Got to agree, K3B or Gnomebaker are excellent alternatives. 

:cool:

---

### Post by salguod on 2006-10-09
I use K3B, which I find is excellent, but I can only burn CDs when I open it as root. (in terminal: sudo K3B)
when I try to burn as a user I get an error message that it cannot access the burner.
Anyone know how to fix this? I attemped changing the "burning group" to my computer's group, but that did not work.
Salguod.

---

### Post by CujoQuarrel on 2006-10-09
I got around the problem by 

sudo chmod +s /usr/bin/k3b 
or
sudo chmod +s /usr/bin/gnomebaker

which ever you use

I don't care who burns CD/DVD on my computer which is the only thing I can think of why this wasn't done by default.

---

### Post by salguod on 2006-10-10
hmm. Thanks for that tip, which I tried. now I can run k3b as root with the following error:

root@powermac:~# k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
ScimInputContextPlugin()
Link points to "/tmp/kde-root"
Link points to "/tmp/ksocket-root"
~ScimInputContextPlugin()

I cannot run k3b AT ALL anymore as user. This is what I get:

powermac@powermac:~$ k3b
The KDE libraries are not designed to run with suid privileges.
ERROR: Communication problem with k3b, it probably crashed.
powermac@powermac:~$

How do I undo the "chmod +s" command"?

salguod

---

### Post by CujoQuarrel on 2006-10-10
chmod -s /usr/bin/k3b should do the trick

What I was getting was a message about not being able to get sole access to the burner messages. Looks like your prob is something different than mine.

---

### Post by CujoQuarrel on 2006-10-10
Whoops. Never tested k3b (I use gnomebaker). I see the same error messages you get now. 

Have you tried gnomebaker? It's about the same as k3b.

---

### Post by Dinerty on 2006-10-10
Bonfire is a great burning package, can be installed from:

System > Adminstration > Synaptic Package Manager search for Brasero

---

