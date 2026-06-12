---
title: "&gt;5 Kb/s download speeds"
date: 2012-01-27
forum: Apple Hardware Users
---

### Post by demii on 2012-01-27
Greetings.

I recently installed Kubuntu 11.10 onto my Early 2008 MBP (4,1). I notice when I download things, I often only get speeds up to 5 Kb/s. As of this writing, I'm downloading digiKam via apt-get and I'm only getting these minimal speeds. 

Browsing the internet is fine and zippy, though I have problems sometimes with watching streams or videos. 

Do anyone have any suggestions?

---

### Post by pauljwells on 2012-01-29
Check in Software Sources that you are using a local mirror for the repositories, or just try using the main one if the local one is slow.

---

### Post by demii on 2012-01-31
Where may I find Software Sources? Under System Settings, the closest thing I see is Information Sources but I see nothing dealing with repositories.

---

### Post by demii on 2012-02-12
Bump.

Whenever I want to download something, I always have to stop and start the download because it constantly drops down to ~5Kb/s. Most videos also refuse to buffer. I do not have this issue on my OSX side. I am currently in Japan, if that makes any difference.

---

### Post by winh8r on 2012-02-12
Take a look here:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")


look for the heading "Download Server" and follow the instructions there and check to see if it improves.

Hope this helps you.


Do a system update using update manager after changing the repository, this will aloow you to see the direct connection speed to your new mirror.

---

### Post by demii on 2012-02-13
Thank you for the reply. However, I did the Kubuntu equivalent and chose the "Select Best Server" option under my Software Sources menu, but downloads are still ~5Kb/s :/

---

