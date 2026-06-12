---
title: "Bandwith limiter? - not shaper"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by gripepe on 2006-09-11
Hi there,

I would like to know if there is a way to configure my network interfaces so that i can limit the total amount of data that i downoload/upload in a per day basis.

My situation is like this: I am currently living in some university funded flats, with a broadband connection in every room, but the upload/downoload is limited to 2/1 gb per day. I would like to limit my ethernet interface so that when it reaches its maximun, i can switch to my wireless interface (within the university´s wireless network) to do some normal web browsing.

Thanks in advance

---

### Post by kidders on 2006-09-11
Hi there,

This is something I've tried to do in the past as well. Perhaps the easiest way to do this is with a cron job. You could execute a script every 15 minutes or so, that records how much your bandwidth usage has increased by since the last time. Once you get over the threshold, you could have it bring down your connection, or tinker with your default route. Then, as the time approached midnight (or whenever you consider yourself to be back to zero), you could make it put things back the way they were.

If something like this would meet your needs, let me know ... I can give you more specific help.

---

