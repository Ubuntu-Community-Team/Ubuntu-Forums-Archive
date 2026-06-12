---
title: "SMB connection failed"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by ras on 2006-04-11
I am trying to mount a windows share at work onto my ubuntu laptop but am having trouble.  The /etc/fstab entry for the share is:

//agren.local/agren /net/agren.local/agren smbfs rw,auto,user,credentials=/home/austin/.agren.local.credentials,uid=1000,gid=1000 0 0

When I do $ sudo mount //agren.local/agren
I get:

austin@austinlt:~$ sudo mount //agren.local/agren
cli_negprot: SMB signing is mandatory and we have disabled it.
14655: protocol negotiation failed
SMB connection failed

I dont understand what this means.  Does this mean that my network admin has disabled negotiating with samba?  I have checked and rechecked my fstab file, my credentials file, and other stuff, but can find no solution.

Please tell me what you all think.

-ras

---

### Post by ras on 2006-04-11
Ok, I figured it out.  I had to use the 'cifs' filesystem instead of 'smbfs'.

The fstab entry that worked:

//agren.local/agren /net/agren.local/agren cifs rw,auto,credentials=/home/austin/.agren.local.credentials,uid=1000,gid=1000 0 0


-ras

---

### Post by steve.horsley on 2006-04-11
That's worth remembering. Thanks for the update.

---

