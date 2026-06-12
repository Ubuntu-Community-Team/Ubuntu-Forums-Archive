---
title: "Download speed unusually slow"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Mr Greencastle on 2007-04-08
(Ubuntu Edgy 6.10, broadband)

I am new to Ubuntu, I had Vista but I didn't like it. The problem is my download speed is really slow when using synaptic, apt-get, aptitude or the update manager, usually between 12-40 kB/s. I recently did a fresh install and updating/synaptic etc. is getting annoying.


I use firefox my download speed is between 300-600 kB/s (tried on many websites), I've disabled ipv6, but don't think thats the problem, I am running XP on dual boot and download is fine aswell. (websites load fast)

It's a wired connection.

Can anyone give me easy instructions to help speed this process up?

Thanks in advance

---

### Post by Origin415 on 2007-04-09
Is it just apt-get/synaptic/etc or is it Firefox in linux as well?

It may just be that you have a slow connection to the ubuntu repository servers, for whatever reason, you might live far away, for example.

---

### Post by josephus on 2007-04-09
You can try changing the repository you are downloading from.  There are many mirrors, try choosing one which is close to you.

If you want more details, try reading this thread [http://ubuntuforums.org/showthread.php?p=2278944](http://ubuntuforums.org/showthread.php?p=2278944)

---

### Post by Mr Greencastle on 2007-04-09
No, just synaptic etc.

I hope its not that, I live in Canada...

Come to think of it, they were perfectly fine when I was doing the initial updates after the install (400 kB/s) then they just slowed down and haven't sped up...

---

### Post by freebird54 on 2007-04-09
I hesitate to check on this - but did you perhaps disble ipv6 only on FireFox (with the about:config option) or systemwide?  Just a passing thought (from the same place as 'check its plugged in' on other problems.. :) )

---

### Post by bwhite82 on 2007-04-09
Install netselect from the command line or from synaptic:

[INDENT]sudo aptitude install netselect[/INDENT]

Then go [here]("https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive"), select a list of mirrors closest to your location. Utilize them in netselect to find out which is the fastest mirror for you:
(EXAMPLE: )
[INDENT]sudo netselect -vv [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) [http://mirror.optus.net/ubuntu/](http://mirror.optus.net/ubuntu/) [http://mirror.isp.net.au/ftp/pub/ubuntu/](http://mirror.isp.net.au/ftp/pub/ubuntu/)[/INDENT]

The mirror with the *lowest* score is your best bet. Then simply update your sources.list with the new mirror.

---

### Post by Mr Greencastle on 2007-04-09
I disabled ipv6 system wide, aswell as in firefox.

---

### Post by Mr Greencastle on 2007-04-09
I'll try the net select one.

---

### Post by freebird54 on 2007-04-09
Yeah - I thought the slow repos were more likely - but I've been caught assuming before.  Hope a mirror change works for you.

---

### Post by Mr Greencastle on 2007-04-09
Ok so mine was 
[ftp://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/](ftp://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/)

I did a 
         sudo gedit /etc/apt/sources.list

...

What exactly do I replace?

---

### Post by josephus on 2007-04-09
which repository are you currently using?
```

cat /etc/apt/sources.list
```

---

### Post by Mr Greencastle on 2007-04-09
Um, I see

[http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) 

and

[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) 

don't really know if thats what you mean...

---

### Post by josephus on 2007-04-09
replace your /etc/apt/sources.list with
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://ca.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://ca.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://ca.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 


```

This sources list was generated using [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

I assumed that you are using edgy and running i386 kernel, if not go to that link and choose a different option.

---

### Post by Mr Greencastle on 2007-04-09
Ok, so I did that, and it didn't change:

            Fetched 4898kB in 2m48s (29.1kB/s) 

The speed is still slow, I think I already did that auto generate thing before when you told me...

---

### Post by josephus on 2007-04-09
try the american server

---

### Post by Mr Greencastle on 2007-04-09
Yeah I went and generated a list for the US

It worked, thanks, can't believe it was that simple... Have had this problem for days...

The server up here in Canada is probably made from maple syrup and poutine :lolflag:

---

### Post by josephus on 2007-04-09
which province are you in?  i just tried the canadian server and it seemed fine.

---

### Post by Mr Greencastle on 2007-04-09
Alberta, its probably because I'm in the West.

I'm from Ontario myself, though.

---

### Post by raydekok on 2007-04-10
i have the same problems. but when i tried the us servers i gat for a moment fast download in synaptic but after a while it wend back to 5000 b/s that is SLOW i've got normaly a downlaod in firefox of 350 to 600 kb/s

---

### Post by josephus on 2007-04-10
if you try downloading a package from here:

[http://us.archive.ubuntu.com/ubuntu/pool/](http://us.archive.ubuntu.com/ubuntu/pool/)
(or wherever your sources.list is pointed to)

using firefox do get the same download rate as synaptic?

---

### Post by freebird54 on 2007-04-10
My Edgy install pulls from the US servers - my Feisty install pulls from the Canadian servers.  Both vary from 39 - 600 depending on the day, time, phase of the moon -but usually run 250-350.  Sometimes they are so fast that it can't report the speed!

I suspect you have moe of an issue with your ISP - or your configuration - than your source.

BTW - Ontario at the moment - Alberta when possible again.... :)

---

### Post by flip314 on 2007-04-15
I get consistently get ridiculously slow speeds (5KB/s to 20KB/s) with the Canadian mirror.  I max out my connection (~150KB/s) on the US mirror.

I'm in Alberta, BTW.  Maybe the Canadian mirror is faster out east. :D

---

### Post by freebird54 on 2007-04-15
Is it maybe a Telus thing?  Are they trying to discourage you out there?  Is it a sinister plot to merge you with Montana?  Inquiring minds.... :D

Be happy there ARE alternatives!

---

### Post by josephus on 2007-04-15
i was thinking of conspiracy as well, but moreso along the lines of Quebec jealous of Albertan oil exacts revenge by limiting traffic to ubuntu servers ;>

---

### Post by Stillness on 2007-04-20
> **flip314 said:**
> I get consistently get ridiculously slow speeds (5KB/s to 20KB/s) with the Canadian mirror.  I max out my connection (~150KB/s) on the US mirror.

I'm in Alberta, BTW.  Maybe the Canadian mirror is faster out east. :D

Exact same here. I am in Toronto Ontario, and recently the download speeds from the Canadian mirrors have been horrible. The connections constantly stall and it peaks at 40k/s - it's usually around 30K a second - I switched back to the US mirrors and it's cruising at around 150K/s avg.

---

### Post by mattymattysidebyeach on 2007-04-21
extremely "maple syrup" and (cold) poutine speed in AlBerta from the ca server here as well.

fyi , seems to me that this is only recent, and i remember the d'load speed as being quite fast as recently as a few months ago.

...switched to us server and getting upwards of 100 from as slow as 16 (ugh) ... reminds me of the 14.4Kb dialup/slip days -

---

