---
title: "upgraded to 9.04 and doesn't recognize password"
date: 2009-05-26
forum: Apple Hardware Users
---

### Post by heluani on 2009-05-26
Hi there I just upgraded a working 8.10 ubuntu on an Powermac G5 to Jaunty. The upgrade seems to have been fine, and when I boot (as always I can only boot with video=ofonly) I get a login prompt. The problem is that it doesn't recognize either my password nor my root password. Here are the things I tried

1) Tried booting to Linux single and Linux single video=ofonly and Linux init=/bin/bash and all the combinations of all these to no avail, the monitor goes dead, blinks a number of times and then turns itself off

2) Tried switching at the user prompt to a console with CTRL+ALT+FN+F1 but the monitor switches itself off (I can get back with no problems to graphics with CTRL+ALT+FN+F7)

The really freaky thing is

3) Tried booting an old 8.04 live cd but it just loops at stage 1, and gives me the options for l. linux c. CDROM over again.

Any suggestions will be great.

R.

---

### Post by heluani on 2009-05-26
Well, I suppose the 8.04 disk is faulty. 

I can boot to a black screen passing break="bottom", I know I'm getting a shell cause when I type reboot it actually reboots. So I'm changing passwords blind and adding even some users but when I boot with graphics it keeps telling me that I'm typing the wrong password!

Any help?

R.

---

### Post by heluani on 2009-05-27
Well, I could burn a 9.04 live cd and access my file system, edit the shadow file directly, but now I can't boot from HD anymore... this is frustrating, I guess I'll have to re-install this system. I am frustrated that I could never just hit "upgrade" under ubuntu without having a regression.

R.

---

