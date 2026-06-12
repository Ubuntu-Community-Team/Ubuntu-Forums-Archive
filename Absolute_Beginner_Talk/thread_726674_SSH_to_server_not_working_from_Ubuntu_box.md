---
title: "SSH to server not working from Ubuntu box"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by nrasch on 2008-03-16
All:

I have a Ubuntu server w/ SSH installed on it.  I can SSH into the server no problem using Putty from a XP/Vista windoze box.  However, when I try to SSH into the server from my Ubuntu 7.1 laptop I keep getting a connection time out error.

I even tried to be sneaky using a win32 putty.exe via Wine to connect, but the same issue still occurs.

Since the Windoze comp can connect to the Ubuntu server via ssh, I'm guessing some setting is lacking on my Ubuntu laptop [the client].  Anyone have any clues as to what needs to be fiddled with?

Many thanks!
Nathan

---

### Post by Oldsoldier2003 on 2008-03-16
> **nrasch said:**
> All:

I have a Ubuntu server w/ SSH installed on it.  I can SSH into the server no problem using Putty from a XP/Vista windoze box.  However, when I try to SSH into the server from my Ubuntu 7.1 laptop I keep getting a connection time out error.

I even tried to be sneaky using a win32 putty.exe via Wine to connect, but the same issue still occurs.

Since the Windoze comp can connect, I'm guessing some setting is lacking on my Ubuntu box.  Anyone have any clues as to what needs to be fiddled with?

Many thanks!
Nathan

can you connect in a simple terminal window?
```
ssh <server_ip> -l <username>
```

---

### Post by finer recliner on 2008-03-16
can you ping the server from your laptop?

is there a router involved in your setup? if so, explain the setup in detail.

---

### Post by kevdog on 2008-03-16
Yes post the setup 

and do the following

ssh -vvv <other crap you would normally type here>

the -vvv option shows verbose output.

Putty Keys are not synonymous with OpenSSH keys.  Hence you might need to generate an explicit OpenSSH key and add it to the authorized_keys file on the server to get the Ubuntu client to connect.

Write back if you need more details.

---

### Post by nrasch on 2008-03-17
> **Oldsoldier2003 said:**
> can you connect in a simple terminal window?
```
ssh <server_ip> -l <username>
```

Nopers.  When I try 

ssh 192.168.1.5 -l nrasch
 
*or*

ssh 192.168.1.5 -l nrasch@192.168.1.5

a window opens and the command cursor just sits there and blinks.  After a long while it times out.

Here is what I get when I do a -vvv option:

ssh 192.168.1.5 -vvv -l nrasch@192.168.1.5
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.5 [192.168.1.5] port 22.

---

### Post by nrasch on 2008-03-17
> **kevdog said:**
> Yes post the setup 

and do the following

ssh -vvv <other crap you would normally type here>

the -vvv option shows verbose output.

Putty Keys are not synonymous with OpenSSH keys.  Hence you might need to generate an explicit OpenSSH key and add it to the authorized_keys file on the server to get the Ubuntu client to connect.

Write back if you need more details.

KevDog && finer recliner <<

ping works fine.  the laptop doesn't have any firewall rules setup.  both the server, my laptop, and xp box all sit on the same 192.168.1.0/24 network.  i would assume--but am prepared to be corrected!--that since the windoze box can ssh in i don't have any network/routing issues messing things up.

[Edit: output of the -vvv command is listed in the response just above this one.]

i'll do some googling on the OpenSSH key and try that. :)

many thanks for the fast(!!) replies.

Nathan

---

### Post by kevdog on 2008-03-17
I think those assumptions are correct -- I think its probably a key issue.

---

### Post by nrasch on 2008-03-17
> **kevdog said:**
> I think those assumptions are correct -- I think its probably a key issue.

KevDog:

Just noticed your from Denver.  I just moved from Colo Spgs to China.... small world!

Anyhow, I was at the end of page 2 of [http://www.debuntu.org/ssh-key-based-authentication-p2](http://www.debuntu.org/ssh-key-based-authentication-p2) and still having no luck.  Then, just for fun I booted off of the LiveCD.  Wham!  Got a SSH connection to the server no problem.

So.... maybe my profile or an udpate has messed things up.  I'm going to vote 'no' on a bad update, or there would be tons of people having the same issue.  

Would you happen to know where my SSH settings might be lurking?  I'll blow away my ~/.ssh folder.  Any other places I need to clear out?  I'll probably remove and reinstall the openSSH stuff too, or is that too much of a windoze solution?  ;P

[Edit: Created a new user and logged in as him.  Still no SSH from the command line.... same old timeout.]

Thanks!
Nathan

---

### Post by Oldsoldier2003 on 2008-03-17
> **nrasch said:**
> KevDog:

Just noticed your from Denver.  I just moved from Colo Spgs to China.... small world!

Anyhow, I was at the end of page 2 of [http://www.debuntu.org/ssh-key-based-authentication-p2](http://www.debuntu.org/ssh-key-based-authentication-p2) and still having no luck.  Then, just for fun I booted off of the LiveCD.  Wham!  Got a SSH connection to the server no problem.

So.... maybe my profile or an udpate has messed things up.  I'm going to vote 'no' on a bad update, or there would be tons of people having the same issue.  

Would you happen to know where my SSH settings might be lurking?  I'll blow away my ~/.ssh folder.  Any other places I need to clear out?  I'll probably remove and reinstall the openSSH stuff too, or is that too much of a windoze solution?  ;P

Thanks!
Nathan

blowing out the .ssh folder should be sufficient. if you are a gnome user, you could just install seahorse and have it take care of setting up your publickey with the ssh server.

---

### Post by nrasch on 2008-03-17
OldSoldier2003, KevDog, and Finer Recliner:

First, many thanks to all three of you for the fast and excellent help!  This was my first post, and I'm impressed.  :)

I finally solved the problem by restoring an image of my system I had made a few days ago.  Clearing out the SSH stuff and even reinstalling all the SSH components still wouldn't work.  There was jut something about my system's setup that the server didn't like.  

Now that I'm using a previous image everything is working great.  I'll reapply security updates tomorrow and see if that breaks anything.  If I find out anything new I'll report back here so hopefully some one else doesn't have to mess with the same issue.

Best regards,
Nathan

---

### Post by kevdog on 2008-03-17
I'm curious to know what the actual problem was, very strange.

---

