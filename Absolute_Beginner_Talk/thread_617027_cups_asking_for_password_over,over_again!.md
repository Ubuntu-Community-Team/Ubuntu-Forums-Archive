---
title: "cups asking for password over,over again!"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-11-18
and cupsys is a member of shadow and lpadmin, and so is my username. :(

---

### Post by cmnorton on 2007-11-19
What steps did you take to get to this problem?

I've set up an SMB printer on my Ubuntu laptop, and I get prompted for username/password for every Windows server on our domain. However, once I've set that printer up, I am not prompted again. So, the prompting is happening -- my guess -- through some Windows browse discovery, and once you've made the connection to the printer you are setting up, you should not get prompted again, unless you're going back to set up more printers.

---

### Post by lunaz on 2007-11-19
Actually I found the solution, then another problem.

The server is being moved to a laptop and typing pws on the number pads from other computers doesn't work... :)

Now I got local printing working from 192.168.1.102:631's web interface and the command line, but printing from the other ubuntu computer doesn't work after installing the printer in system>admin>printing.

---

