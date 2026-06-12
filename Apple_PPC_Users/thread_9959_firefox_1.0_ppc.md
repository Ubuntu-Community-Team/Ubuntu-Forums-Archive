---
title: "firefox 1.0 ppc"
date: 2005-01-03
forum: Apple PPC Users
---

### Post by tiiim on 2005-01-03
is there a quick an easy way to upgrade to a powerpc version of firefox 1.0?

Cos' ubuntu os the pre-release version? or should i wait until the next major release of Ubuntu?

---

### Post by diabolo on 2005-01-05
Here's how I did it. Fairly easy but... Be forewarned, this probablly isn't the proper way to do this, and it might even hose your system. I'm still a Linux novice in many respects so I don't know all the ramifications messing around with apt-get...

1. Change all instances of the word "warty" in the /etc/apt/sources.list to "hoary". 

2. Do "sudo apt-get update".

3. I used synaptic to choose mozilla-firefox 1.0 for install. You could do it from the CLI, though.

4. I went back to /etc/apt/sources.list and changed it back to "warty" - just the reverse of step 1.

5. Do "sudo apt-get update" again.

I now have Firefox 1.0 and everything seems to work fine...   :-|

---

### Post by tiiim on 2005-01-05
[QUOTE=diabolo]Here's how I did it. Fairly easy but... Be forewarned, this probablly isn't the proper way to do this, and it might even hose your system. I'm still a Linux novice in many respects so I don't know all the ramifications messing around with apt-get...

1. Change all instances of the word "warty" in the /etc/apt/sources.list to "hoary". 

2. Do "sudo apt-get update".

3. I used synaptic to choose mozilla-firefox 1.0 for install. You could do it from the CLI, though.

4. I went back to /etc/apt/sources.list and changed it back to "warty" - just the reverse of step 1.

5. Do "sudo apt-get update" again.

I now have Firefox 1.0 and everything seems to work fine...   :-|[/QUOTE]
 lol sounds interesting but should i do it...

---

### Post by adamw on 2005-01-27
Be forewarned, your system could lose apt-get sanity (at least, that's what the wiki says).  I tried setting to hoary and then "update", and my machine was hosed faster than you can say "hoary".  Fortunately when hoary becomes stable this should be doable.  On a side-note, are you able to install themes with Firefox 1.0 now that you have it installed?  Because I sure can't on the warty release of Firefox, and man, is it UGLY. :???:

---

