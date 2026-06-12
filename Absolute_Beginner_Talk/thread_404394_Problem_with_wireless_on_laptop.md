---
title: "Problem with wireless on laptop"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Haruk on 2007-04-08
Okay, I just recently installed linux last night for the first time, I'm incredibly new to this, but not new to computers in general.

Anyways, I was trying to set up a static IP on it, so I went to system > networking > and preferences I think...I put in all the info I used before on windows, and then when I hit close, I couldn't connect to the internet at all. So I went back, undid everything I changed, and now it showed my wireless signal was 100%, but it said disconnected. I did not see any button that said to connect or anything...so now I can't go on the internet at all on my laptop!

I'm sure this is probably really obvious to get working, but as I said, I'm completely new to this linux stuff...but it looks great so far!

Thanks in advance!:)

---

### Post by octoberdan on 2007-04-08
Have you configured your router to use encryption? If your router is configured to allow wireless dhcp, can you connect if the interface is assigned information by the router (try the command dhclient)? Can you ping the router? What's the output from ifconfig?

---

