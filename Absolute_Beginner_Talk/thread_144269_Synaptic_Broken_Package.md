---
title: "Synaptic Broken Package"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by beej101 on 2006-03-13
I try to run "Mark All Upgrades" from the Synaptic manager but I get the error
message to fix the broken package first.  How do I fix this? I've tried all the obvious buttons but it doesn't remove the error.  I am using 5.04.
Thank for any help.

---

### Post by Xian on 2006-03-13
From the Synaptic main menu:
Edit > Fix Broken Packages

---

### Post by Zelut on 2006-03-13
So I'm guessing you did the Edit > Fix Broken Packages (is that what you meant by 'obvious buttons'?

You might get more info on the issue by trying it from the terminal.  From the terminal try (and post output here):
[B]sudo apt-get update
sudo apt-get upgrade[/B]

---

### Post by beej101 on 2006-03-14
yes i've tried Edit->Fix Broken Package.  it did the job this time, i was told the network im connected to is having a problem that's why.

i try to avoid apt-get commands and opt for the gui based synaptic because it guards against dependency issues.  i've been burned using apt-get before, having removed certain dependency that was required by the system.

...but yea thanks!

---

### Post by Zelut on 2006-03-14
I wasn't suggesting you switch from the GUI to the command prompt, I just thought apt-get on the terminal would be a little more verbose about the issue and we could better troubleshoot it.

Hopefully the network getting cleared up will fix your issue then.

---

