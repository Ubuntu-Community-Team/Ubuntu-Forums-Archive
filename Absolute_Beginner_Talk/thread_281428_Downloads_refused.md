---
title: "Downloads refused?"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-21
In different cases, such as when I sudo apt-get update, I get this:


Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release.gpg](http://dl.google.com/linux/deb/dists/stable/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

Also, when I go to update my Add/Remove, I get this:
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://www.getautomatix.com/apt/dists/dapper/Release.gpg:](http://www.getautomatix.com/apt/dists/dapper/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
[http://dl.google.com/linux/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/deb/dists/stable/Release.gpg:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Does anyone know what is wrong?

---

### Post by OptimusPrime on 2006-10-21
I thought I had Linux figured out, then it throws this oddball at me.  Can anyone help?

---

### Post by Kurt` on 2006-10-21
It looks like all the domains referenced in /etc/apt/sources.list are resolving to your own computer...

What is the output of this command?

# host security.ubuntu.com

---

### Post by CupofDice on 2006-10-21
Did you just add the google repository because when I did that through Synaptic (trying to get Picasa) I ran into a similar problem.

---

### Post by OptimusPrime on 2006-10-21
wesley@wesley-laptop:~$ # host security.ubuntu.com
wesley@wesley-laptop:~$ host security.ubuntu.com
security.ubuntu.com has address 82.211.81.138
;; Warning: Message parser reports malformed message packet.
wesley@wesley-laptop:~$

---

### Post by Kurt` on 2006-10-21
> ;; Warning: Message parser reports malformed message packet.
Ok, that is very bad. I'm not sure how to fix it or debug it, but that should be resolved before attemping to fix the apt-get update problem (as it is likely the cause).

---

### Post by DragonView on 2006-10-21
Ye.I got the same problem when downloading the patchs and softwares..Can only use explorer..

---

### Post by OptimusPrime on 2006-10-21
Well, does ANYONE know how to fix this problem?

---

### Post by OptimusPrime on 2006-10-21
I can't install anything, and I can't update either.

---

### Post by OptimusPrime on 2006-10-21
What does this even mean?

wesley@wesley-laptop:~$ host security.ubuntu.com
security.ubuntu.com has address 82.211.81.138
;; Warning: Message parser reports malformed message packet.

---

### Post by j0sh0 on 2007-01-23
i know its not much of a consolation, but I have the same problem too (although instead of the IP 127.0.0.1, mine says 1.0.0.0), and haven't yet been able to fix it, but I have found that if you ping the server name before you try the apt-get it will connect (so long as ping returns the valid IP address and ttl)

eg
ping archive.ubuntu.com
ping security.ubuntu.com
sudo apt-get install foo

hope this alleviates the problem somewhat (even though its not 100% surefire)

---

### Post by edubarr on 2007-01-31
I have seen the same problem with a friend's computer. It won't do any updates or let him install any software. His network card is a sis900 and it even didn't work at all until he blacklisted ipv6.

Hope someone finds a definite solution for this.

I was thinking that we could just use the ip address instead of the domain name for the servers. I haven't tested it out on the computer with the problem, but I can't image that it will mistake the actual ip addresses.

You can try it by editing your sources.list and replacing the archive.ubuntu.com with the ip you get from host.
Example:
deb [http://195.248.90.38/ubuntu](http://195.248.90.38/ubuntu) dapper main universe multiverse restricted
instead of
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main universe multiverse restricted

Hope it works, at least until a definite fix is found.

---

### Post by SonOfaSpirit on 2007-12-17
*PART ONE*

Hi, with the help of many others I've been able to fix this problem for good.
First bring up a terminal (shell prompt) with something like "Konsole" found under "System Tools" in the applications bar.  Second, completely purge anon-proxy with the following command:

**sudo apt-get purge anon-proxy**
    <AND ENTER YOUR PASSWORD>

*(The above command works on my Ubuntu 7.10 OS)*
*(OR if you are running a system that does not do the sudo thing type the following:*

**su**
    <ENTER YOUR ROOT PASSWORD>
**apt-get purge anon-proxy**


*PART TWO*

Then type the following:

[B]export HTTP_PROXY=
export http_proxy=
[/B]
    <and you are done!>

Note: To save yourself trouble like this simply don't install anon-proxy; it just messes things up.  Use something like Tor instead if you need an anonymous proxy route to the Internet.  It is located at [http://www.torproject.org](http://www.torproject.org) or (formerly) [http://tor.eff.org](http://tor.eff.org). On their site they also note that you should download the software from their own site rather than Ubuntu's repositories because the software is the latest and greatest when retreived from torproject.org rather than the "universe" or "multiverse" repositories that the Ubuntu people provide.

If this still doesn't work then also try what Movius posted on [http://forums.debian.net/viewtopic.php?p=1209](http://forums.debian.net/viewtopic.php?p=1209) when he said the following:

[COLOR="DarkRed"]PostPosted: 2007-11-11 13:57    Post subject: Another thing  	Reply with quote
Another thing you have to do is look with the "ifconfig" if the lo {loopback} is activated,
in affirmative case

gedit /etc/network/interfaces

and then

delete or put a # in the lines to make it like this :

# The loopback network interface
# auto lo
# iface lo inet loopback


Good luck[/COLOR]

If you do choose to use Movius' suggestion make sure that you ONLY put the # sign in front of text; if you delete it and you want to change it back to what it was you may not remember what used to be printed there.  The number sign (#) simply "comments out" the instructions, so that the instructions for the computer are translated to be simply notes to the computer operator rather than actual commands to act on.  Following these instructions will fix your problem.  It worked for me.  But DO NOT do what Movius has said to do UNLESS Part One and Part Two combined are unsuccessful.  Part#1+Part#2 should work on most every system.  Use Movius' suggestion only if Part#1 and Part#2 do not work for you.

Anyhow, I'm apt-getting away now.  Yay!  L8r

P.S. Regarding Movius' post: You can replace gedit with whatever text editor you want.  The command runs a text editor which opens the file */etc/network/interfaces*

---

