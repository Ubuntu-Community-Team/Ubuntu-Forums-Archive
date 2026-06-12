---
title: "[SOLVED] How do I use ssh without passwords?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-10-18
I want to ssh into another computer without having to type in any passwords.  After the key generation and adding the public key to ~/.ssh/authorized_keys on the server, now when I ssh into the server instead of being asked for my user password I'm asked for my key password.  This is just replacing one password with another, I'm not sure how it's any better.

There are two ways I've read going about this:
1) Use no password for key generation.

This seems like a security flaw from my unexperienced opinion.

2) Use ssh-add to the private key into memory.

This still prompts for a password when I first want to ssh into another machine.

On a side note, I have another question about ssh keys.  I have multiple private keys for different servers.  Can I add them all into the ~/.ssh/id_rsa file one line at a time or do I need to rename them into separate local files and use the -i option when using ssh?

---

### Post by civic_si on 2007-10-18
I use this without putting a password in all the time at work for Nagios to connect to other servers and monitor important processes. I set it up to use no password since its all automated I cant put a password in. Its probably a security flaw, I have not watched Wireshark to see what gets passed when it logs in.

---

### Post by cheetaux on 2007-10-18
Try the following:

On the computer you want to ssh from, generate a key using ssh-keygen and  use the "-t rsa" option.  Don't enter a passprase:

> ssh-keygen -t rsa

Now go to the .ssh directory:

> cd ~/.ssh/

and do a **ls**, you should see a filed called i*d_rsa.pub*

Now do a secure copy of the public key to the computer you want to ssh to:

> cp id_rsa.pub *remove@computer*:/.ssh/id_rsa.key

It will ask you for your password, enter it.

Now go back to the home directory:

> cd ..

Now logon to the remote computer using ssh:

> ssh *remote@computer*

It will ask you for your password again, enter it.

Now that your are logged onto the remove coputer, go to the .ssh directory and verify that the id_rsa.key file is there.

Copy the information contained in the id_rsa.key file to .ssh/authorized_keys:

> cat id_rsa.key >> authorized_keys

Now delete the public key file
> 
rm id_rsa.key

Disconnect from the remote computer and try connecting again - you should get right in without having to enter a password.

Hope this helps.

---

### Post by bodhi.zazen on 2007-10-18
> **AncientPC said:**
> I want to ssh into another computer without having to type in any passwords.  After the key generation and adding the public key to ~/.ssh/authorized_keys on the server, now when I ssh into the server instead of being asked for my user password I'm asked for my key password.  This is just replacing one password with another, I'm not sure how it's any better.

There are two ways I've read going about this:
1) Use no password for key generation.

This seems like a security flaw from my unexperienced opinion.

>_<

So you are wanting a secure way to ssh without a password ??? :lolflag:

# 1 is the way to go as you would then at least need the key.

I was going to type up some instructions, but [color=blue]cheetaux[/color] beat me to it :twisted:

---

### Post by AncientPC on 2007-10-18
Thanks cheetaux, but I already knew how to do that (as mentioned in #1).

> **bodhi.zazen said:**
> >_<

So you are wanting a secure way to ssh without a password ??? :lolflag:

# 1 is the way to go as you would then at least need the key.

I was going to type up some instructions, but [color=blue]cheetaux[/color] beat me to it :twisted:

I want to set up an rsync script as a cron job and can't be bothered to always put in passwords.

---

### Post by bodhi.zazen on 2007-10-18
oic

You could consider expect :

Expect : Automate interactions (will pass passwords):
	
	[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

	[http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by pietro_spina on 2007-10-19
I used this guide and it works like a charm.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)
Author description:
"This document covers using cron, ssh, and rsync to backup files over a local network or the Internet. Part of my goal is to ensure no user intervention is required when the computer is restarted (for passwords, keys, or key managers)."

cheers,
-p

---

