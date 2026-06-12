---
title: "ssh2 error"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by lynxus on 2006-09-12
Hey guys,
I get the following error when trying to connect to one of my servers.

The other servers connect fine, But for some reason ssh2 just isnt requesting teh hist key / crashing with this server.
Everyone else who should connect to it can. So it must be ubuntu / client side.

Error :

warning: tcsetattr failed in ssh_rl_set_tty_modes_for_fd: fd 1: Interrupted system call

More detail :

Oh and if i sudo ssh2 **.**.**.** it connects, but connects as root .. And i cannot do that!

gsmart@gsmart-laptop:~$ ssh2 ***.***.***.***
warning: Need basic cursor movement capability, using vt100
Host key not found from database.
Key fingerprint:
xenev-rinah-nufyf-kenam-tezub-gabon-kiled-tadof-koreg-ruvaz-zoxyx
You can get a public key's fingerprint by running
% ssh-keygen -F publickey.pub
on the keyfile.
warning: tcsetattr failed in ssh_rl_set_tty_modes_for_fd: fd 1: Interrupted system call

Received signal 2. (no core)
gsmart@gsmart-laptop:~$



Any ideas?
Cheers
G

---

### Post by Slychilde on 2006-09-12
> Host key not found from database.

It appears you are missing a key for the user you're attempting to connect as.  You will have to make one and put it on the server.  You can learn more about making keys [here]("https://help.ubuntu.com/community/AdvancedOpenSSH").  I'm not sure, something is missing; they may just be in the wrong place.

> Oh and if i sudo ssh2 **.**.**.** it connects, but connects as root .. And i cannot do that!

Why can't you connect as root?  ...Is this your server?

---

### Post by lynxus on 2006-09-12
It is my server, Well the "team" server .. anyway..


Ive resolved it..

Apparently its a bug in ssh2 when you connect to a new server and unable to getkey.

to fix this you either need to recompile with a ( dodgy patch ) or type:

strace ssh2 server.mydomain.com

Once teh code stops scrolling press y  then once again when it stops scrolling press e  then once again press s
once its stopped again, press ctrl+c  then close the terminal 

reopen and ssh2 normal again

It SHOULD connect fine the second time.
if not.. Try the above again. ( Sometimes takes a second try )

Hope this helps any future searchers ;)

---

