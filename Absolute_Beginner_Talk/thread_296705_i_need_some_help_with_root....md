---
title: "i need some help with root..."
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by speedingbullet on 2006-11-10
actually I have a few questions, but let me say what im trying to do here. Back when I had windows on the computer im using right now, I occasionally played an MMORPG called planeshift. It would run fine if I closed some of my applications. But now that it has Ubuntu, the linux version of plane shift is playing to slow for me to be able to even type anything in on the login screen. I attempted it on my main user account, but then I remembered I had a games account that already came with ubuntu, and I figured since it was named "games", it would be designed to play games more than anything else, and do a better job than my main account would. However, It wont let me log on because it first says something about the home directory not being directed to something, and when i click on the continue thing, It says that my session only lasted 10 seconds and the error log file to it says permission denied...

so here are my questions:

1. will the games account do a much better job?

2. how do I make a home directory for that games account?

3. how do i get full access to this root user account, i really need to know.


thanks...:)

---

### Post by digby on 2006-11-10
1. the games account is not an actual user, and it wouldn't improve performance in any case.  the problem sounds more like a video card issue.  have you installed your video drivers correctly?

2. to create a new user / home dir, the easiest way is to use the 'Users and Groups' tool under system > administration

3.  I strongly recommend using sudo rather than enabling the root account, but if you understand the danger, it can be done by running sudo passwd root

more info on root and sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

