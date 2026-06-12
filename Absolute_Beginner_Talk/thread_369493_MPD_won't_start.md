---
title: "MPD won't start"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-24
I installed MPD and get the following reply when I enter MPD at the terminal :

unable to bind port 6600: Address already in use
maybe MPD is still running?

Has anyone else had this problem and how did you fix it?  I followed the How To post and edited the mpd.conf per those instructions but no luck.  I posted this in the media section and got no answer so I thought I would try here.

---

### Post by robophred on 2007-02-24
There is a terminal command to list the programs running, but I forgot it...
Open system->control center->system monitor, and look for mpd from there.
Or you can try to stop it running by doing
sudo killall mpd
If there are no instances of mpd running, it will say so.  Else it will close them and not say anything.

Oh, and what is 'mpd'?

---

### Post by rggavubt on 2007-02-24
> **robophred said:**
> There is a terminal command to list the programs running, but I forgot it...
Open system->control center->system monitor, and look for mpd from there.
Or you can try to stop it running by doing
sudo killall mpd
If there are no instances of mpd running, it will say so.  Else it will close them and not say anything.

Oh, and what is 'mpd'?

MPD is music player daemon which I installed using synaptic.  I entered the command above and entered my password and then it jumped back to the prompt.  When I then entered mpd to try to start it I got the following :

cannot setgid for user "mpd" at line 188: Operation not permitted

---

### Post by robophred on 2007-02-24
It probably did successfully stop the mpd if it didn't give any response.

Does mpd need to be started up in sudo?

---

### Post by rggavubt on 2007-02-24
> **robophred said:**
> It probably did successfully stop the mpd if it didn't give any response.

Does mpd need to be started up in sudo?

I used sudo mpd and returned right to the terminal.  I guess it restarted.

---

### Post by robophred on 2007-02-24
If it is a service, try 'killall'ing it again, and try
sudo /etc/init.d/mpd start

Actually, best to first try
man mpd

and see if it has any information about how to start it up.

---

### Post by rggavubt on 2007-02-25
> **robophred said:**
> If it is a service, try 'killall'ing it again, and try
sudo /etc/init.d/mpd start

Actually, best to first try
man mpd

and see if it has any information about how to start it up.

I did man mpd and found out one of the commands in the how to post was incorrect.  The 
"sudo mpd –create-db" command should have read "sudo mpd --create-db".  Thanks a lot, your "man mpd" command saved me a lot of headaches!!:popcorn:

---

### Post by rggavubt on 2007-02-25
> **rggavubt said:**
> I did man mpd and found out one of the commands in the how to post was incorrect.  The 
"sudo mpd –create-db" command should have read "sudo mpd --create-db".  Thanks a lot, your "man mpd" command saved me a lot of headaches!!:popcorn:

It should show two dashes in front of create....the space between the two dashes doesn't show up on screen.

---

