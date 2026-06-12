---
title: "MacBook Core Duo Users:  Having trouble with Suspend-To-RAM??"
date: 2007-05-02
forum: Apple Intel Users
---

### Post by benanzo on 2007-05-02
I run Ubuntu 7.04 "Feisty Fawn" on my first-gen MacBook Core Duo (not Core2Duo or MacBook Pro).  I recently read in another post that there has been some serious difficulty in getting suspend to ram working reliably.  Ever since I began installing the Feisty betas I have had no problem with it.  All the features work reliably including suspend with lid close ONLY if on battery power, screen brightness changes depending on if it's plugged in/on battery, CPU frequency scaling to 50% for each core if on battery power, etc.  With these features I get a little over 3 hours on one charge.  I know that's not as good as Mac OS X's 4 hours, but it's decent for me.

I really want to figure out why it works for me (I've never modified anything) and not for others.  I recently investigated a little and installed Feisty fresh on another partition.  A couple things I was looking for:

1) Screen resolution - NOPE.   have to install 915resolution and reboot to get 1280x800.
2) Touchpad - Basic.  Scrolling,tap-to-click etc work.  modify xorg.conf to get advanced features.
3) Power management: this works.  Suspend to ram, etc all work good out of to box for me.
4) Wireless:  Works.

I am a little confused why it's working for me and not others.  If there's demand I'll post some logs.

---

### Post by mustang on 2007-05-02
Hi benanzo,

thank you for going out of your way to make this thread. Thanks also for taking the time to investigate the problem for those of us with no suspend. 

If you have the time, you could start by comparing your lspci, lspci -vv, and dmesg outputs with the ones posted here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

It might be the case that there are multiple revisions of a macbook within each generation and the developers who wrote the code for suspend might have been only dealing with one specific revision (which you happen to have). You could check this by seeing if there's any differences between the lspci outputs (use "diff" if it's too difficult to check with your eyes).

edit: some characteristics about the setup i'm running (doubt they effect suspend to ram but who knows)

-core duo, first generation
-I'm running a beta which is upgraded to the final version.
-i'm dual booting (mac osx has its own hfs partition, ubuntu has its own ext3 partition)
-I upgraded my ram from 512 to 1024 mb (the new ram was taken out of another macbook)
-i am using a ~1 gig swap partition

---

### Post by benanzo on 2007-05-02
I grabbed the outputs from several of the people who posted here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92635)

Most of them weren't run as root so my output has more info, but it should still help.

Find the diffs here:
[http://www.starlitworld.com/diffs/](http://www.starlitworld.com/diffs/)

---

### Post by mustang on 2007-05-03
Thanks benanzo for posting the diffs.

That's interesting that my (manish) lspci output differs in that I get a lot of "Capabilities: access denied" entries. I don't know if that's abnormal though. Is there some permission issue at stake?

Your lspci output matches up well with stephen's (formatting issues make it seem otherwise).

Not sure what to make of the dmesg diffs though.

---

### Post by mustang on 2007-05-03
Oh wow oh wow. So tantalizingly close!

Going off my initial suspicions that there was some permission problem at work, I booted up the 2.6.15 feisty kernel and logged in as root and tried to suspend. Nada---same old problem (backlight off, hd off, cpu on). Similar deal with 

echo "mem" > /sys/power/state (which for some reason, I cannot even do as sudo)

I then booted up with vanilla kernel 2.6.21 with [this]("http://www.mail-archive.com/mactel-linux-devel@lists.sourceforge.net/msg00198.html") patch applied. Logged in as root, tried 

echo "mem" > /sys/power/state

....and **it worked!** For the first time in nearly five months, my macbook suspended under linux. The CPU *finally* turned off. It also woke up but the backlight was off. Turning up the brightness keys had no effect. Neither did restarting X. 

So I'm just nearly there, I just need to figure out how to tie gnome's power management suspend script to the command above executed as *root*. I also need to figure out how to restore the backlight. 

Once again, thank you so much benovo for posting this thread or else I'd never known to try suspending as root. Hopefully someone might be able to chime in on solutions for the remaining problems.

edit: well that's odd, i tried two more times and it didn't work. stay tuned for details...

edit2: yep, doesn't work at all now. CPU stays on. Don't know how to explain the one time it worked.

---

### Post by benanzo on 2007-05-03
I get the <access denied> entries when I run lspci as normal user.  when I use sudo I get all the information.

---

