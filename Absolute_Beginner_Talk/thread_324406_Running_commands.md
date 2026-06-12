---
title: "Running commands"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2006-12-23
At the risk of sounding completely helpless here, could anyone tell me how I go about running a command? For instance, when installing easyubuntu, it tells me I need to run this command:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

I have no clue where to *run* that at. Any help would be appreciated, and PLEASE bear with me while I bombard you with dumb questions :)

---

### Post by jincast90 on 2006-12-23
> **herrma29 said:**
> At the risk of sounding completely helpless here, could anyone tell me how I go about running a command? For instance, when installing easyubuntu, it tells me I need to run this command:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

I have no clue where to *run* that at. Any help would be appreciated, and PLEASE bear with me while I bombard you with dumb questions :)

Start of by copying the command using the ctrl+c command.

Then go to Applications>Accessories>Terminal

Then press ctrl+shift+v in the terminal, and press enter. Your command should now be running.

---

### Post by DaveBorealis on 2006-12-23
> **herrma29 said:**
>  could anyone tell me how I go about running a command?

Hello,

Go to 'Applications -> Accessories -> Terminal' and type the command in the window that pops up.  Come back if you have any further questions!  :) 

Best regards,
Dave

---

### Post by herrma29 on 2006-12-23
thanks guys, I actually figured it out by doing a little searching. When I tried to do the command that I mentioned though, it gave me this:

gpg: no valid OpenPGP data found.

Any clue?

and when I tried to make my windows partition viewable, it gave me this:

Connecting to www.ubuntu-nl.org|81.171.100.21|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:01:35 ERROR 404: Not Found.

When I tried to acquire the script to automatically mount my partition...I'll dig around some more for help, but if you have any answers for me, feel free to chime in.

---

### Post by rccharles on 2006-12-23
> **herrma29 said:**
> thanks guys, I actually figured it out by doing a little searching. When I tried to do the command that I mentioned though, it gave me this:

gpg: no valid OpenPGP data found.

Any clue?

and when I tried to make my windows partition viewable, it gave me this:

Connecting to www.ubuntu-nl.org|81.171.100.21|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:01:35 ERROR 404: Not Found.

When I tried to acquire the script to automatically mount my partition...I'll dig around some more for help, but if you have any answers for me, feel free to chime in.

To access your windows partition, see:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Robert

---

### Post by Sef on 2006-12-23
> PLEASE bear with me while I bombard you with dumb questions

We love to answer dumb questions here, so please post them. :mrgreen:

---

