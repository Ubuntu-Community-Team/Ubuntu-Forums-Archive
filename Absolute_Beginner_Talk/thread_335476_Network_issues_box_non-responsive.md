---
title: "Network issues? box non-responsive"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2007-01-10
So I've recently setup my own Ubuntu 6.10 server, I installed open-ssh and have been configuring it via ssh ever since. I have been following [this guide]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p4") since to install all the normal server stuff (apache, mysql, etc). so far this is what I've done.

- installed some apps via apt-get (apache, mysql, bind9, etc)
- setup a static ip (192.168.0.100)
- did some re-configuring of bind9 (following what the guide told me to)
- changed the hosts file and the hostname

here is my problem, when I download something (wget) the network connection just freezes and then the box becomes unresponsive. I endup having to reboot the box to get access to it again. I tried shutting down the dns (bind9) server, thinking that had something to do with it but now. It's happened now 3 times...

any ideas what could be causing the problem and host I can resolve it? thanks in advance.

---

### Post by Aberrix on 2007-01-10
can anyone help?

---

### Post by riven0 on 2007-01-10
Just bumping this up in case a more knowledgeable person happens in... but as a last resort, have you tried trying to re-installing wget?

---

### Post by Aberrix on 2007-01-10
> **riven0 said:**
> have you tried trying to re-installing wget?

I guess I haven't thought of that? could that be causing the problems? I've done a apt-get update and apt-get upgrade(?)

when it happens it just freezes, the box is non-responsive to pings and anything else.

---

### Post by Aberrix on 2007-01-10
I just installed and configured proftpd (via [this guide]("http://ubuntuforums.org/showthread.php?t=79588")) and tried to upload the file I was trying to wget (which was ispconfig) and the server looks like it took a dumb again... non-responsive...

this is becoming frustrating...

---

### Post by Aberrix on 2007-01-10
bump

---

### Post by erok2112 on 2007-01-12
This might sound silly but...
have you tried a different NIC?

Usually, I like to take it down to the basics if I'm hitting the wall.

Eric

---

### Post by Modernity on 2007-01-12
Double check your Network Settings again, sometimes you might notice something that doesn't sound right.

---

