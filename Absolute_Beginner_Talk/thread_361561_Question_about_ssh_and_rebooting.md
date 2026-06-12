---
title: "Question about ssh and rebooting"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by YamiKaitou on 2007-02-14
Even though I have gotten the ssh and ftp dameons installed, that is all I basically know how to do. So, I have a problem that will go into effect in a few weeks that I wish to manage.

I have the server version of ubuntu installed at home. I use it to only run a counter-strike server. I already set it up and I have been using it for a month or 2 now. The thing is that I prefer to have this comp hardwired to the router and my personal comp doesn't have to be. So, my family is going to be moving soon, and I am trying to get a way that I can still have this server wired to the router but the router be in a different room than my personal comp, thus giving the server no monitor to use. So, I installed the ftp to it so I can edit the files easily. That is okay. But I want to be able to restart the server via ssh whenever I want. The thing is that if I start my counter-strike server from within ssh, will it continue to run on the server or will it stop once I close my ssh connection? If it will close, how can I get it to start the game server as soon as I reboot the comp?


Summary: My comp will have no monitor in a few weeks, so I have to control everything via ssh and ftp. My comp has a game server that I always have running. If I need to restart the comp for some reason, is it safe to do so via ssh even though I can't stop the game server? Also, is there a way that I can get the game server to start by itself without me having to tell it to start? If I start the game server via ssh, will the server stop once I end my current ssh session or will it continue to run?

Any help is appreciated.

---

### Post by darkfame on 2007-02-14
The answer to your "problems" are screen.

sudo apt-get install screen

When it's done installing, start it simply by typing screen.
Start up the counter strike dedicated server as usual and hit Ctrl+A followed by a D.
This deattaches you from the screen and you can safely log off the ssh session without terminating the dedicated server running inside screen.

When you later log back in, type screen -x to resume your session.

Read up on the screen man pages (man screen) for more advanced ways to use screen.

Good luck! :)

---

