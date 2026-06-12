---
title: "xmms - not opening on desktop"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Corvair on 2006-07-25
Hi,

When I launch XMMS it does not open on desk top.
But when I look in System Monitor it is listed and running.

If I try launching from Terminal I get this message:
Message: device: default and xmms does not open.

Any clues on what I did this time?

I know enough to get in trouble but not enough to get out of it.

---

### Post by T700 on 2006-07-25
Do you perhaps have more than one instance of it running?  You might try logging out of the session and then back in.

Paul

---

### Post by Corvair on 2006-07-26
It is listed only once in the System Monitor and running. No other sighn of it openned anywhere else (that I can see or hear).

---

### Post by byen on 2006-07-26
Ok.. try this: what happens when you restart and type the following in the Terminal :```
xmms
``` Can you give us the output it gives you...

regards,
byen

---

### Post by Corvair on 2006-07-26
I did a restart and went to Terminal and did sudo xmms as you suggested.

This is the result:

claude@ubuntuClaude:~$ sudo xmms
Password:
Message: device: default



And xmms is not listed in the System Monitor.

---

### Post by byen on 2006-07-26
Hmm.. this is interesting. Usually xmms works well on most setups. Can you tell us how you installed it? Is it possible for you to completely remove xmms via the Synaptic and reinstall it?

---

### Post by Corvair on 2006-07-26
I tried installing it from synaptic and also from Applications before with the same result.
I just went to synoptic and did a complete uninstall and reinstalled it.

I clicked on the xmms button up on the tab section and I don't see or hear anything on the screen, but it is listed and running in the System Monitor.

I did an end process in System Monitor to stop it from running. Then I went to Terminal and got the same result as listed before. 

I had sound problems before. after that was fixed, While listenning to xmms it froze. and I could not get it to show up since then.

---

### Post by Corvair on 2006-07-26
I had installed options on xmms:

1- coverviewer
2- flac
3- infinity
4- skins

They were removed when I removed xmms, but not completely removed.
So I reinstalled them and did a complete removal individualy on each one and comletely removed xmms again and shutdown the computur completely.
Then I restarted and reinstalled xmms alone. 

Now I can start xmms both from Terminal and from the xmms button, 
and I get the music playing also.

But the display I get on screen is not the regular xmms window.
I get a small window called GNU/LINUX and the DEBIAN name and symbol.

How can I get the regular version?

---

### Post by Corvair on 2006-07-26
Everything is normal, except that I am viewing DEBFSKIN. I am not sure how I got it instead of the dark looking skin. How do I get the other skin?


options--> skin browser--> debfskin.

Thanks for the help.

---

### Post by Corvair on 2006-07-26
I learned something else tonight.

I loaded the skins option from synaptic and now I have a big choice of skins, of which I have the dark one (none) :mrgreen: [http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif)

Everything is normal with XMMS.

---

### Post by staticprevails on 2006-10-13
Hi all this is my first post here, I'm a newb to Linux.  I'm having the same problem, sort of...  When I click on XMMX in the Applications menu, it does not launch or show up on my desktop.  It shows up as "running" in the System Monitor.  When I type "sudo xmms" in Terminal, it launches and works.  It was working fine last night. Any ideas?  Thanks!

  vince@MyBox:~$ sudo xmms
  libmikmod.so.2: cannot open shared object file: No such file or directory
  Message: device: default

---

### Post by staticprevails on 2006-10-13
> **staticprevails said:**
> Hi all this is my first post here, I'm a newb to Linux.  I'm having the same problem, sort of...  When I click on XMMX in the Applications menu, it does not launch or show up on my desktop.  It shows up as "running" in the System Monitor.  When I type "sudo xmms" in Terminal, it launches and works.  It was working fine last night. Any ideas?  Thanks!

  vince@MyBox:~$ sudo xmms
  libmikmod.so.2: cannot open shared object file: No such file or directory
  Message: device: default

nm, I just did a full restart and it works now.  that was strange. . . All is good now.  :)

---

