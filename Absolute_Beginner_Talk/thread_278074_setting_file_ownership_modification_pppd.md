---
title: "setting file ownership modification pppd"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-10-15
According to:
[http://www.tldp.org/HOWTO/PPP-HOWTO/root.html](http://www.tldp.org/HOWTO/PPP-HOWTO/root.html)

the file /usr/sbin/pppd 

should be set as follows:

-rwsr-xr-x   1 root     root        95225 Jul 11 00:27 /usr/sbin/pppd

but the most I can get the file to "see" using the command from the above URL is 

-r-sr-x---

by sudo-ing

chmod u+s /usr/sbin/pppd

I'm a newbie, and even though I've done:

ls
ls | more
ls | less 

trying to get pppd to show itself/ownership in the command line format, I've been force to use the file manager and see permission.

Please give me the correct ls command and the man pages for file ownership, which don't appear as

mark@Lexington:~$man file
or
man ownership (something to do with Compaq computers, mine is a Dell)
man permissions

etc. What's up with that?

The file owner is ROOT and the Group owner is PPP

---

### Post by dbd on 2006-10-15
I'm not 100% sure what you were asking, but I think ln -s is the command you were looking for, and ln -s|less may be even more helpful. man ln will tell you more.
Also
sudo chmod 755 /usr/sbin/pppd
will do what you want.

Also, I'm not sure if it was intentional, but don't double post, it annoys people, and also answers to your question get spread around.

---

### Post by Mark_in_Hollywood on 2006-10-15
Thanks for the fast response. I did not intend to post twice. The ONLY reason I'm doing any posting at this forum is I can't get the modem to hold onto pppd. The result of that problem is that right in the middle of the modem sending the post to this forum, the modem died. I had to dial-in again and then post, believeing that the first post had gone astray. Sorry. Again, thanks.

---

