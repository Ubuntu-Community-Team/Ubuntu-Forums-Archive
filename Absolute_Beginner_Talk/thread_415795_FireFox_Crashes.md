---
title: "FireFox Crashes"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Bakerconspiracy on 2007-04-20
Everytime I open FireFox, it Crashes. It will open for a 15 seconds, not load any of my home pages then crash. I have tried reinstalling it via apt-get, but it seems to heavily integrated into Ubuntu for that. I have used opera and konqer but just prefer Mozilla. Any ideas on how to get it running again?

---

### Post by nanotube on 2007-04-20
in your profile it says you are using kubuntu 4.10, is that true? if so, the firefox in those repositories will be pretty old... get a fresh install of the official mozilla build following the instructions under the first link in my sig (go to install firefox section).

---

### Post by Bakerconspiracy on 2007-04-20
Did what you said. Looks like whatever the bug is, it was retained. I made a complete new dir in my /usr/lib/ with the new firefox in it. Still crashed. Here is what the terminal read out is:
andrew@alienware:/usr/lib/fox$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Bus error (core dumped)

I don't know how to get the error log in firefox though...
any help apreciated

Edit: It probably has something to do with a plugin then, since the new firefox picked it up. Should I just go about deleting my plugins?

---

### Post by Bakerconspiracy on 2007-04-20
Fixed it, Thanks for the ideas nanotube.

---

### Post by nanotube on 2007-04-21
> **Bakerconspiracy said:**
> Fixed it, Thanks for the ideas nanotube.

so, it was a plugin, then? in that case, it wasn't thanks to my suggestion. :) glad it all worked out for you anyway. :)

---

### Post by MattAd on 2007-06-04
I've been having a similar problem with the same error output as Bakerconspiracy, only I'm running Feisty. I've tried starting Firefox in safe mode, and this doesn't seem to prevent the problem either. Is there just something buggy in the current build of Firefox?

I'm also having a similar problem in Epiphany. I know that I installed Flash, recently. Maybe that's it?

---

### Post by nanotube on 2007-06-04
> **MattAd said:**
> I've been having a similar problem with the same error output as Bakerconspiracy, only I'm running Feisty. I've tried starting Firefox in safe mode, and this doesn't seem to prevent the problem either. Is there just something buggy in the current build of Firefox?

I'm also having a similar problem in Epiphany. I know that I installed Flash, recently. Maybe that's it?

try starting with a fresh profile without any extensions, and try to uninstall flash (since you say it may be related), and see if it goes away...

---

### Post by fakie_flip on 2007-07-01
mv ~/.mozila ~/.mozilla_backup

---

