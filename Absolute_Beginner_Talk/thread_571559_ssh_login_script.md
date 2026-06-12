---
title: "ssh login script"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by brmalub on 2007-10-09
Hi everyone - yet a newbie asking for help. I see that several others have been asking of something similar, but I am not sure that I need the same. The deal is that I have to login to get access to the internet where I live. I do this with:
                ssh -T -l username hostadress

Then it prompts me for a password. I enter the password and click enter.. wolla - logged in.

1st issue: Now I have a terminal lying open and if I close I loose acess to internet = annoying and fills up the screen.
2nd issue: I hate having to login each and every time I turn on the computer, so of course an automated way that would log me in, and perhaps get rid of the open terminal window would be excellent.

Thanks for you help, and have a lovely evening.

BrmalUB
Denmark

---

### Post by hyper_ch on 2007-10-09
For (1) try this:

```

ssh -T -l username hostaddress &

```

and for (2) I have no real solution

---

### Post by tribaal on 2007-10-09
For (2) you can easily just put the client's ssh key in your server's user account ~/.ssh/, then you won't ever need a password again (only for this particular client computer).

More detailed info can be found [here]("https://help.ubuntu.com/community/SSHHowto") (look for the "Public key authentication" section).

Hope this helps!

- trib

---

### Post by hyper_ch on 2007-10-09
tribaal:

Doesn't need that to be the other way around? His ISP would have to generate a key that he could use for auto-login?

---

### Post by brmalub on 2007-10-09
thanks for you answers. What I can tell from the thread you posted to was something about me having to place a key on the server. This is not possible to me. Is it possible to make a script that echos ssh -T -l username host & 
(dunno how to wait till I am asked for the password before I have the script type it)

Im lost here :)

---

### Post by qpieus on 2007-10-09
For your first issue of leaving a terminal window open all the time, a program called screen may be able to help. If I'm reading the screen documentation correctly, you can open up a terminal, type screen <enter> at the prompt to start a screen session, then you should be able to enter in your ssh command. With the ssh command now running within the screen session, you can "detach" that session. After you detach a session, you can then close the terminal if you want because the screen session is actually still running (you just can't see it). Later you can open up a terminal and re-attach to the session if you need to.

Here's a couple helpful looking links:

[http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

[http://opensource.apress.com/article/48/command-line-gems-screen](http://opensource.apress.com/article/48/command-line-gems-screen)

I'm not at all a screen expert, so I may have messed up my understanding of this :)
Perhaps some other folks who have some experience with screen can confirm that it'll work for your problem.

---

### Post by hyper_ch on 2007-10-10
Screen helps... so das adding a "&" at the end of the command which will go on running that command in teh background even if the terminal is closed.

---

