---
title: "[SOLVED] unmounting problem"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by lanchongzi on 2007-09-25
I connected my Sony Ericsson M600i to my PC
because it couldn't unmount in Ubuntu i installed Kubuntu - because before it worked fine with Kubuntu

but now I get this

Unfortunately, the device system:/media/sdb (/dev/sdb) named 'Johannes' and currently mounted at /media/Johannes could not be unmounted. 
Unmounting failed due to the following error:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Moreover, programs still using the device have been detected. They are listed below. You have to close them or change their working directory before attempting to unmount the device again.
                     USER        PID ACCESS COMMAND
/media/Johannes:     root          1 ....m init
                     root       2384 ....m udevd
                     daemon     3907 ....m portmap
                     root       4056 ....m getty
                     root       4057 ....m getty
                     root       4061 ....m getty
                     root       4062 ....m getty
                     root       4063 ....m getty
                     root       4064 ....m getty
                     root       4189 ....m syslogd


what can I do?

---

### Post by ddrichardson on 2007-09-25
If you leave it a little while does it unmount? It seems similar to bug [#107550]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/107550")

---

### Post by lanchongzi on 2007-09-25
actually it did

on my phone it was not displayed anymore
so ijust unmounted it and it worked

thank you anyway :)

---

