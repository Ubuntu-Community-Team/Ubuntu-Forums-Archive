---
title: "Small network problem (on Edgy)"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-11-02
After my pc boots up (which takes some time, but that's an other issue), I never have any network.
I always have to go to System > ... > Network and then deactivate my wired connection, activate it again and then, only then I have network.

So I get it working anyway, but is there any way to avoid doing this over again after every boot?

---

### Post by boban on 2006-11-02
I assume you are reviving your IP from DHCP server...

I don't offer you a real solution to your problem, but some workaround. You can make script with:

```

#!/bin/bash
ifconfig eth0 up
dhclient eth0

```

First line is needed only if your network card is down on boot... (You can check if it is with ifconfig command, just after booting).

Add this script to your start up programs (f.e. in this way: [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/))

And the long booting time is maybe caused by network card configuration issue... (you can remove "quiet" option on kernel you use to boot in /boot/grub/menu.lst and see where boot up process hangs)

Btw. I've got the same issue in windows :P (but I don't use it often, so it's not a real problem)...

---

### Post by Ecthelion on 2006-11-03
First of all, tx for your post. 

I've tried both tricks: the script and removing the quiet option.
Unfortunately, none of them seems to make any effect:
When I start up without the quiet in /etc/grub/menu.lst
(I've removed it only from the first option, which is the one I booted)
I just get the same as ever.
That's strange because I would think that I would see the old booting up message passing, like I saw them while booting dapper.
Anyway, I don't expect my network to be the problem at boot:
see the thread about my booting issue: [booting issue]("http://ubuntuforums.org/showthread.php?t=291525")

Starting with the script didn't made any difference too...
(I 'installed' it like they said in your link)
Still it's good to know how to make those script start up with your pc.

So tx for your post, but the problem remains. :-k

---

### Post by boban on 2006-11-03
> **Ecthelion said:**
> 
When I start up without the quiet in /etc/grub/menu.lst
(I've removed it only from the first option, which is the one I booted)
I just get the same as ever.


It is VERY strange... Maybe your screen brightness is too low to see messages? (because nothing else reasonable comes to my mind right now)

After looking through your other post I think it's some hardware issue that edgy can't handle correctly... I know that is not the answer - but perhaps you should stick with dapper for now... 

I think I can't help you more with your problem... I hope someone else will have idea how to help you...

---

### Post by Ecthelion on 2006-11-03
What am I supposed to see when I remove that quiet option?

> After looking through your other post I think it's some hardware issue that edgy can't handle correctly... I know that is not the answer - but perhaps you should stick with dapper for now...

:D  8)  :D  ;) 

There is NO [-X way I'm going back to Dapper, Edgy may be on the Edge and still have problems,but I just love it.
Even with longer boot times and a small network problem.

Which doesn't mean I'm not going to try and make those little problems go away :) 

EDGY ROCKS!\\:D/ 

tx for the help

---

### Post by boban on 2006-11-03
> **Ecthelion said:**
> What am I supposed to see when I remove that quiet option?


You are suppose to see boot up messages (f.e. alsa starting, cups starting, etc). That way you can figure out which part of boot up process "hangs" (if any).


And I agree with you - EDGY ROCKS :mrgreen:

---

### Post by Ecthelion on 2006-11-03
> You are suppose to see boot up messages (f.e. alsa starting, cups starting, etc). That way you can figure out which part of boot up process "hangs" (if any).

Well I'm afraid that even with Brightness set on 90%, I only see what I see usually: the Ubuntu Logo "Ubuntu" and then an indicator which says the boot progress (hangs on 0 for 2 minutes, then gets filled very fast)

When I press Ctrl-Alt-F1, then I got the message "Starting up" followed by some [error reports]("http://ubuntuforums.org/showthread.php?t=291525")

That's all.

I suspect that it should boot up as quickly as that progress bar gets filled up, without hanging for 2 minutes...
But thats not the case... :-k

---

### Post by Ecthelion on 2006-11-03
Alright I think I have to solution for this small problem...
Maybe it sounds stupid, but I changed my login options, who were atomatic login, to timed login...
That seems to be enough for the network issue...
Maybe my pc is too fast for my network...
Or maybe I changed something else while trying, which made the problem go away...

But i think it's the timed login...

Anyway tx everyone for your help...

And if you don't know what to do there's still my [boot time issue]("http://ubuntuforums.org/showthread.php?t=291525") ;)

---

