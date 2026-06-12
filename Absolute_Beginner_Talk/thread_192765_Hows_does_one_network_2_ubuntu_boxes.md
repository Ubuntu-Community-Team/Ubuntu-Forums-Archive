---
title: "Hows does one network 2 ubuntu boxes?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-09
Hi,

I know how to network ubuntu and xp but I think it best to ask about ubuntu and ubuntu.

The connection is via a router.

Thanks.

---

### Post by hotbrainz on 2006-06-09
I just used accessories ----> networking and then set IP addresses. It was done. Then i pinged the sytems and they identied each other. As I have LAMP servers in both i can move data through that between the systems :)

---

### Post by steve.horsley on 2006-06-09
Network in what sense?

Simplest is probably ssh. This will allow file transfer, remote login and remote X GUI applications.

---

### Post by angkor on 2006-06-09
[QUOTE=u.b.u.n.t.u]Hi,

I know how to network ubuntu and xp but I think it best to ask about ubuntu and ubuntu.

The connection is via a router.

Thanks.[/QUOTE]

nfs for shares and ssh for maintenance?

[http://nfs.sourceforge.net/nfs-howto/intro.html#WHAT](http://nfs.sourceforge.net/nfs-howto/intro.html#WHAT)

---

### Post by u.b.u.n.t.u on 2006-06-09
Thanks, 

Do I need to install Samba to network 2 ubuntu boxes?

What is ssh?

I have two computers. They are both running ubuntu 6.0.6. They are both connected to the internet through the same router/modem.

I want to access box "2" from box "1".

nfs looks awfully complicated.

There must be an easy way to do this.

Thanks.

---

### Post by dvarsam on 2006-06-09
Dear "u.b.u.n.t.u.",

[QUOTE=u.b.u.n.t.u]Do I need to install Samba to network 2 ubuntu boxes?
What is ssh?
I have two computers. They are both running ubuntu 6.0.6. They are both connected to the internet through the same router/modem.
I want to access box "2" from box "1".
NFS looks awfully complicated.
There must be an easy way to do this.[/QUOTE]

If you want an easy way to Network your 2 Ubuntu PCs, I have figured out how to do this with NFS & SSH...

Please read the article here: [http://ubuntuforums.org/showthread.php?t=186063](http://ubuntuforums.org/showthread.php?t=186063)

Be patient & read it up to the end...

Good Luck!

P.S.> I have NOT experimented yet with "samba"... (btw: I have _just_ managed the NFS...)

---

### Post by u.b.u.n.t.u on 2006-06-09
dvarsam,

Thank you. I will read up on that tomorrow. (Rather late here).

Samba is needed for nix-windows networking, which I know how to do.

---

