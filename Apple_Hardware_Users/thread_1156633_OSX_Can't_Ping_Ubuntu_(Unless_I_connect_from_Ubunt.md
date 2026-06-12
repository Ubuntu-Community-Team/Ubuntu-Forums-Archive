---
title: "OSX Can't Ping Ubuntu (Unless I connect from Ubuntu First)"
date: 2009-05-11
forum: Apple Hardware Users
---

### Post by pkkid on 2009-05-11
This is rather annoying.  But it seems the Apple network support is lacking.  I setup an NFS share on Ubuntu and I could not for the life of me get the OSX (Mac Mini) to connect.  So I did a simple ping, and that did not see it either, kept saying Host not responding.  However the reverse (pinging OSX from Ubuntu) works fine.

Now this is where it gets weird.  I was getting tired of going back and forth to between rooms to test this out, so I turned on Remote Desktop on the Mac and then connected from Ubuntu.  All of a sudden, I can ping from the Mac to the Ubuntu machine.  And guess what.. The NFS now mounts great.

So.. I tried playing a movie and all seems well.  After leaving it alone for an hour (not using it).  I get an error message saying Ubuntu is once again not responding.. And once again I cannot even ping the machine.  Following the same steps as above (connecting via remote desktop) fixes the issue once again.  Of course connecting Remote Desktop every time I want to access the share is a bit overboard.

Anyone know what might be going on?

---

### Post by netJackDaw on 2009-05-12
If you are connecting your Ubuntu box to the network through a wireless network this might explain it. The wireless network does not start until someone logs in.

I found this thread in the forums: [http://ubuntuforums.org/showthread.php?t=910274](http://ubuntuforums.org/showthread.php?t=910274)

I have annoyances with this myself and will try this solution when I get home...

---

### Post by pkkid on 2009-05-12
Hmm,

I have been logged into my Ubuntu box the whole time.  So this doesn't sound like my issue.  I am also able to SSH into the box when I am at work.  It does sound like the same exact sympoms tho (assuming I was *not* logged in).

---

### Post by DarwinSurvivor on 2009-06-18
I am experiencing the same problem. I have a eee machine running jaunty that I am using as a server.

I installed the netbook-remix version because there's no cdrom (server-edition does NOT like installing from USB).

I can not connect to the eee via ssh, http or https until the server pings me. I am connecting from a laptop running Intrepid and have tested this on 2 networks (home and college).

It's not an O.S. incompatibility problem (both running ubuntu) and it's not the network (tried 2).

It seems as though ubuntu blocks all requests until someone local decides to connect back.


Since this is a server and will soon be out of my hands, I REALLY need to get this thing to allow all incoming connection.

If anyone knows if this is a security feature or something (and knows how to kill it), please post!

---

### Post by DarwinSurvivor on 2009-06-27
Hmm, it would seem that as long as you ping "something" (not necessarily your other computer), you can then connect from anywheres.

It's as if ubuntu requires itself to make an outgoing connection (to somewheres) before anybody can connect to it.

I also noticed that the problem returns each time the machine goes to sleep (not even a full shutdown). Very annoying :(

---

### Post by Spyduck on 2009-10-23
Sorry for replying to an old thread, but I'm having the same problem (though not the same as the last post -- the machine I couldn't ping was already running, and had outgoing connections.  But I couldn't connect to this machine until I pinged it from the other)

Both computers are running Ubuntu 9.10 beta, and when I try to ping or connect to my samba share computer (at 192.168.1.100) I get errors.  Pinging it says "destination host unreachable," and has 100% packet loss.

When I try to ping or connect to it from my macbook, or even this computer (through Windows) it seems to work, for some reason.

Pinging this from the other Ubuntu computer seems to fix it (temporarily?  I haven't tested longer than an hour since it started working).  So far, I haven't had to do this for OS X or Windows 7 (though windows' connection has other problems, occasionally, which are probably unrelated)... and even though it's working now I have a feeling it'll stop eventually, whether it's when I shut down or when this computer's IP changes.

**I'm not sure of what else to add to this message, or any logs I'd need to attach. ** I also have no idea what to google to find an answer, as this is the closest thread I could get.  Thanks for any help.

---

### Post by DarwinSurvivor on 2009-10-23
The only thing I found that seemed to fix the problem was replacing network manager with WICD. I spent about 2 solid days on IRC talking to #ubuntu, #linux, and the linux networking channels trying to find and answer and it basically seemed to come down to "Network Manager does some weird, unknown stuff".

WICD fixed the problem right away.

---

### Post by Spyduck on 2009-10-23
Thanks for the suggestion.  It seems to be working, for now.  But I haven't had it installed that long yet, so it might just be a fluke.

I'll reply again if it stops working.

(Also, I was wrong before -- the first time I must've done something already so it'd connect for a bit, as my mac couldn't connect or ping the machine a few hours later.)

---

### Post by wii552 on 2009-10-23
that's kinda weird...After all, I have pinged my ubuntu machine and SSHd to it from my macbook...

---

### Post by Spyduck on 2009-10-24
I just typed a bit of text and it didn't submit right, so here goes again.

WICD solved the problem, I think.  But now I rebooted into Windows and samba is broken.  I can't ping this computer from Ubuntu but I can ping the Ubuntu computer holding Samba files.  THe connection works for about 20-30 minutes, then just stops adn I can't reconnect.  Would this probably be WICD not working, or should I make a thread about Samba itself?

Edit: Suddenly I can't ping either :(  Nothing should've changed since I didn't make any changes yet.

---

### Post by DarwinSurvivor on 2009-10-24
You made sure to add your connection properties to WICD? Remember, wicd stores the connection information (WPA passwords, etc) separately, so after rebooting WICD won't know what networks to connect to.

If it worked when first installed, it would probably be because network manager created the connection and WICD just left it alone.

---

### Post by ljonesj on 2009-10-24
maybe u need a wake up on use network card mine seem to do fine so far

---

### Post by Spyduck on 2009-10-25
Yes, I've set the WICD connection settings.

I also have sleep disabled, so I don't think wake-on-LAN would help (also, it's connecting through a wireless USB dongle, so I don't think I can even use WOL, can I?)

It's working again today, for now, without having rebooted the system.  I did shut down Windows overnight, though, so I'm guessing this is probably a problem with Windows.

---

