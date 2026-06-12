---
title: "[SOLVED] Gmail Problem: Cannot Send Attachments"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-14
I can't send attachments in Gmail. It lets me pick a file to send fine, but when I actually click send, it shows at the bottom "sending request to Server" loading, but it never gets anywhere and it never sends.

I am using Feisty, Firefox 2.0.0.4, default install of Firefox (no extensions), I have tried disabling Firestarter (firewall), the attachment is < 10 mb, I have cleared the cache, I have allowed pop-ups, and I have logged into the secure server. I also set up Evolution and tried sending them through that way, also with no success, although I'd rather access my mail via the web, that was just an experiment.

The closest I could find to my problem was a thread [http://ubuntuforums.org/showthread.php?t=10487&highlight=gmail+attach](http://ubuntuforums.org/showthread.php?t=10487&highlight=gmail+attach) that mentioned gnutls and libgnutls11 but that post is a year old, so I didn't know if that would be a problem anymore. 

Lately, mostly at night, I've been getting a bit of disconnects/network down time. It will last anywhere around 20 minutes and come back up. But when I am actually connected, the connection seems fast, and otherwise hunky dory. I'm guessing it is just a maintenance period.

I also recently set up a router. I don't know if these last two things are related, but I'm trying to provide every detail I can think of.

---

### Post by jimbob on 2007-07-14
Try taking your router out of the loop for a minute and see if you can send a Gmail attachment.

If not, try sending a small text file as an attachment to your next post (ex: /etc/network/interfaces) and see if we get it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by keyboardashtray on 2007-07-14
Good idea - I'm going to test sending an attachment here first before I try disconnecting my new router.

...it didn't work. It went through all the motions in the load bar at the bottom, but after it was done it said "Upload Errors"

hmm, on to the modem I guess.

---

### Post by keyboardashtray on 2007-07-14
Ok, I've disconnected the router, and I still wasn't able to send an attachment in Gmail. I will now try here again.

It failed again, I got the message "upload errors" just like last time.

I appreciate the help, though :) any other ideas?

---

### Post by jimbob on 2007-07-14
Very strange.  What kind of network are you using; cable, DSL?

Do you have another OS on the same box you could try?  I'm really not sure if it is a network problem or something in your Ubuntu installation that would cause that.

Can you connect another computer to that same network and see if that works?

Just trying to narrow things down a bit.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by keyboardashtray on 2007-07-14
Well, I think I have it solved - sort of. I went into Windows, tried it from there, was getting the same problems. Then I tried attaching the super-small text file you had me make to try attaching here - and that one worked (there)! So then I came back here (Ubuntu, Firefox), and tried the super-small text file. And it worked. Well, then I tried an .ogg file again, and just gave it a long time... seven minutes later, it did upload. 

So it must be related to the internet problems I've been having lately, because it never used to take that long. I'll have to take it up with them, maybe they choked my connection - I don't know.

Thanks for the help, now I know I just need to give it a really long time. Now I've got other fish to fry...in these restarts, all of a sudden its doing these forced check-discs, which it wasn't doing before, and the last one had all kinds of scary messages. But thats for another post.

Thanks again, jimbob!

---

