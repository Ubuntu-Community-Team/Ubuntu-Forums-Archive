---
title: "slow file copy speed on network"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ThunderRd on 2008-01-26
I have several XP clients and one 7.04 box connected via a D-Link 10/100 ethernet switch.  Each one of the windows boxes can copy files to any other windows box at high speed; not theoretical speed but close enough, about 9.9 MB/s.

However, I experience EXTREMELY slow copy speeds both to and from the linux box which shares through Samba.  It is reproduceable.  For example, I wanted to copy a 4 GB file and several others, total of about 5 GB.  The machine wanted 170 minutes- if I am correct that is only about 30 MB per minute.  There is something wrong.

100Mbits/s = 12.5MB/s = 750MB / minute. I know I can't get theoretical speeds but there is a big difference from 750/m to 30/min.

What information do you need to help me solve this?

---

### Post by dcstar on 2008-01-26
> **ThunderRd said:**
> I have several XP clients and one 7.04 box connected via a D-Link 10/100 ethernet switch.  Each one of the windows boxes can copy files to any other windows box at high speed; not theoretical speed but close enough, about 9.9 MB/s.

However, I experience EXTREMELY slow copy speeds both to and from the linux box which shares through Samba.  It is reproduceable.  For example, I wanted to copy a 4 GB file and several others, total of about 5 GB.  The machine wanted 170 minutes- if I am correct that is only about 30 MB per minute.  There is something wrong.

100Mbits/s = 12.5MB/s = 750MB / minute. I know I can't get theoretical speeds but there is a big difference from 750/m to 30/min.

What information do you need to help me solve this?

Disable IPv6 and also investigate making SAMBA use CIFS, you may also want to check if the ethernet card is auto-negotiating correctly with the switch.

---

### Post by ThunderRd on 2008-01-27
> **dcstar said:**
> Disable IPv6 and also investigate making SAMBA use CIFS, you may also want to check if the ethernet card is auto-negotiating correctly with the switch.

OK now, I posted here because it's for "absolute beginners"  ;)

Disabling IPv6 looks like something I can handle but there are a lot of conflicting reports on whether it's a good idea; I'll investigate.  I live in Asia and some countries like Japan are using it.  I'll have to find out more.

The gigabit ethernet on the mainboard seems to be negotiating correctly.  Both the board and the switch are indicating a 100Mbit connection.  Also, it works fine between the windows machines, and it works fine on this machine when it is booted into windows.  The problem only arises when I run this box in Linux.

Make SAMBA use CIFS; well I know it's a file system but can you tell me more about how and why I should do this?  I can't seem to understand the homework on this.

---

### Post by ThunderRd on 2008-01-29
Want to know what I hate more than anything?

I make a post in a forum titled "absolute beginners" asking a valid question.  Someone posts back in *nix techspeak that requires clarification for an "absolute beginner" like me (on *nix, not computers).  I ask for the clarification, and the poster doesn't respond.

Can I make a respectful request that posters responding in this particular forum please keep the forum title in mind when responding?  I mean, why have such a forum if it's over our heads?

Thank you.

---

### Post by moonlightcheese on 2008-02-15
some of this is just searching yourself.  try various different phrases relating to your question in the search bar and do a lot of reading.  then try google, of course.  actually, if you had bothered to research the issue (i've been looking for days) then you'll notice that tons of other users have slow network speed issues similar to yours and with various network hardware and setups (crossover cable or switches, various settings and changes).

keep in mind that any information provided to you is given out of the author's free time and no one *has* to provide an answer.  if i happen to find *the* answer i'll post the information that worked for your convenience, but realize that you need to do some searching and sticky reading before demanding anything out of a forum's user base.

---

### Post by ThunderRd on 2008-02-16
My problem isn't that I'm not appreciative.  I DO do my homework here and in other locations; I post when I need something explained, clarifed, or otherwise provided.

My complaint is that this is a forum titled "ABSOLUTE BEGINNERS", and I believe that the responses should be somewhat moderated for their content.  In other words, is it understandable to an "absolute beginner"?  Is the OP knowledgeable enough to interpret the information?

What is an "absolute beginner"?

 If I were more proficient (at *nix), I would be posting in the other forums.  I posted here to obtain an answer that I can understand.

BTW I'm not stupid, just inexperienced.

---

### Post by peabody on 2008-02-16
> **ThunderRd said:**
> 
What is an "absolute beginner"?
.

I think you hit the nail on the head there.  It's a subjective interpretation.  I'd agree that the person who responded wasn't helpful, but at the same time, you can't expect every member of the board to act like a well trained tech support rep.  We try, but we're no guarantee.  Your objections are duly noted.

Anyway, in response to your previous question and what information we would need, could you do us the favor of opening up a terminal window, and typing the command:

ifconfig -a

and then copying and pasting the output into a code block?  Thank you.

---

