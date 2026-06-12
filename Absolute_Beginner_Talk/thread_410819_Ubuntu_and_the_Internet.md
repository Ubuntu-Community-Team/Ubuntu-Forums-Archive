---
title: "Ubuntu and the Internet"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-16
Is Ubuntu 6.10 inherently reliant upon the Internet for proper operation?  This past weekend, I used the OS which has always been quite snappy on my 3.0 Ghz machine (2 mb ram) with no problems, downloading packages, installing them, configuring them (with varying degrees of success), etc.

I use the computer for onsite field recording, and, so, left my home for a project site where I do not have access to the 'net.

Other than that one change, I cannot think of another change to the system.

However, certain functions of the OS seem to have slowed to a crawl.  Just booting up takes perhaps five minutes - seems to hang on the "windows manager" screen, where you have the small box with a few icons in it after entering your user ID and Password but before the desktop icons have appeared.

I had set up a virtual machine running WinXP.  Worked fine this wekeend.  Tried to start it up this morning sans the 'net, and it took (I'm not kidding) 10 minutes until it was fully loaded.  Once loaded, it seemed to operate at normal speed.

I cannot imagine what else could have caused this slow down, but will not be home again until next weekend, so I figured I'd ask the question here (I'm on another machine, if you were wondering).

Thanks for any advice.

Caruseo

---

### Post by LaRoza on 2007-04-16
I use Ubuntu at home with no Internet connection and I have no problem.

How fast is the CPU of these connectionless machines?

---

### Post by Seisen on 2007-04-16
Is this a desktop or a laptop?

---

### Post by carusoswi on 2007-04-16
This is a desktop machine - 3.0 Ghz Pentium (IV I believe, will have to check), 2mb RAM, modern, speedy FSB (sorry, I'm not with the machine today, so I can't give you accurate details, but, it is a modern, up to date, recently purchased, "powerful" machine, plenty of disc space, etc.

It is set up as a dual boot, XP Pro and Ubuntu 6.10.  I have VMWare setup on Ubuntu to also run a virtual XP machine.

I am really quite stumped at this.  Once it loads up, things seem to run ok.  I can open aps in Ubuntu and they seem to run ok, and, as I mentioned, once the virtual machine finally gets up and running, XP seems to run ok.  I can open win aps and they seem to load within a normal length of time.

If I boot straight into XP, that loads up fine, also, so I don't think it is a hardware related problem.

Thanks for any suggestions as to what may have happened.  It does not make any sense to me at all.

Caruso

---

### Post by Happy_Man on 2007-04-16
Hmmm.... what else did you do with this computer after you took it off from the internet, but before this problem cropped up? Were you editing config files?

---

### Post by carusoswi on 2007-04-16
> **Happy_Man said:**
> Hmmm.... what else did you do with this computer after you took it off from the internet, but before this problem cropped up? Were you editing config files?

I packed it in the suitcase I use to carry it, and I drove for a couple of hours, unpacked it, plugged it in, ran a straight winxp session, then, booted into Ubuntu.

I am too new to be editing any code unless I'm doing it the easy way by copying something from this forum and pasting it into the terminal window.  Obviously, that didn't happen since I don't have an internet connection at my current location.

Is there some sort of repair routine I can run to restore anything that somehow got broken?

Thanks again for the reply.

Caruso

---

### Post by sailor2001 on 2007-04-16
on boot up, ubuntu is looking for your Internet connections and that will take a while before it gives up and continues booting....you can force load faster by using keys ctrl/c at the point where  the boot tries to find Internet

---

### Post by carusoswi on 2007-04-17
Thank, I will give that a try.
Caruso

---

### Post by carusoswi on 2007-04-17
> **sailor2001 said:**
> on boot up, ubuntu is looking for your Internet connections and that will take a while before it gives up and continues booting....you can force load faster by using keys ctrl/c at the point where  the boot tries to find Internet

Thinking out loud . . . why would my VMWare session load so very slowly?  Is the machine looking for the internet during that process as well?  Will the same key combination help at that point also?
Thanks again.
Caruso

---

### Post by dstew on 2007-04-17
Sometimes you can tell why booting takes a long time by looking at the diagnostic messages that the boot process saves. After you boot, enter at a terminal:

dmesg | less

This allows you to look at the messages, and to page up and down. A big time gap can give you a clue as to what is causing the problem.

EDIT: A common problem is the ipv6 protocol. If you do not need it, it can be disabled. See: [http://ubuntuforums.org/showthread.php?t=329463&page=2](http://ubuntuforums.org/showthread.php?t=329463&page=2)

---

