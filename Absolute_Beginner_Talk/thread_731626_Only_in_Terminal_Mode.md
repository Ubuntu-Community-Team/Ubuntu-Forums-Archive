---
title: "Only in Terminal Mode"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Gideony on 2008-03-22
Today I did a little experiment and it went terribly wrong.  I decided to upgrade my 7.10 partition to the new Hardy Heron and it managed to kill it pretty good.

So I decided to just go ahead and install Ubuntu 7.10 through Parallels on my Mac and leave it at that for now.

It worked.  But when I got all my sources turned on and ran the update, it downloaded all the patches, etc and then I told it to reboot.

And now it boots into Terminal mode and I don't have a clue how to get it into the UI or how to keep it going into the UI.

I have tried "xstart" to no avail, and really don't have any other idea of what to do.  It does show the Ubuntu loading screen before going to he text, and I'm not seeing any error message.

Any help would be appreciated.  Thanks!

---

### Post by etotheipiplusone on 2008-03-22
Maybe I'm wrong, but isn't it 'startx'?

---

### Post by mikewhatever on 2008-03-22
Have you tried 'startx' instead?

---

### Post by Gideony on 2008-03-22
I'm about to find out.

The first bit of help I found on this topic said "xstart."
But I just found another piece, right as you replied, that said "startx"

If this works, (it's booting up now) the key will then be "how do I get it to do that automatically"
...

Seems to be working.

Cool.

Gotta love the internet...  when you finally figure out what terms you should even be search for, you find someone handing out bad advice.

So, will this take care of it or do I need to do something to keep this from happening again?

---

### Post by Gideony on 2008-03-22
Okay... wow.  Yikes.

These updates managed to fry things pretty well.  :sighs:

I really want to use Ubuntu more, but this learning curve is killing me.  Having to construct my own sound drivers, things exploding at random times and not having a clue how to move back or what is even causing said problems.

It is frustrating.

It now starts by saying "this session is running as a privileged user."  I say "Continue" and my desktop settings are all gone.  It works for a brief moment and then seems to "freeze."

Any advice would be appreciated.  Thanks.

---

### Post by Gideony on 2008-03-22
Okay.. the lock up ended, and then I get strange messages about the desktop running.  I am trying to get the exact text, but it freezes again as it begins to work.

I think somehow the user situation is messed up.  I never logged in, as I used to...  but I can't seem to switch users, either.

Okay.. when I tell it to switch users I get the following message;

"GDM (GNOME Display Manager) is not running."

Thanks

---

### Post by mikewhatever on 2008-03-22
You must have been in the recovery mode when you typed startx. Reboot into the regular mode and login with your username and password.

---

