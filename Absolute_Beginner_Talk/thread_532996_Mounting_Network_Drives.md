---
title: "Mounting Network Drives"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by mcduarte2000 on 2007-08-23
Hi, I want to connect to a small network server I have at home that uses Samba. This is where I store all my documents, photos, movies, etc. I achieved to create a shortcut on the desktop to it, but, it seems most applications can't access it (ex: Picasa, AmaroK, etc), which made me feel very frustrated.

I searched the foruns and it seems I should edit the fstab file (I already learned how to do that), and put something like:

```
//192.168.1.10  /media/moon  smbfs  rw,username=XXX,password=xxx,uid=1000,gid=1000  0 0
```

Well, but it simply doesn't work. One of the problems I find is that the server doesn't have a password and a user to login, it's open to everybody inside the network.

Could some good soul tell me, step by step, what I should exactly do to be able to give access to all applications to my network drive?

Thanks a lot,

Miguel

---

### Post by Dr Small on 2007-08-23
Why don't you setup an openssh-server instead?

---

### Post by emperor on 2007-08-23
Check the samba server to see what is shareable using:

$ smbclient -L yoursambahostsname

[http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html)

---

### Post by mcduarte2000 on 2007-08-23
Nice, It works, just as follow up for the next guy with the same problem, the proper code (sort of) is:

```

//192.168.1.10/Volume_1 /media/moon smbfs auto 0 0

```

Sort of, because I can read the drive, but can't write on it... What is missing? I tried, without luck to:

```

//192.168.1.10/Volume_1 /media/moon smbfs rw,auto 0 0

```

Thanks,

Miguel

---

### Post by Aishiko on 2007-08-23
hmmm, I'm thinking of converting my second old Server board into a Lunix based server with say 3 or 4 40gig drives Formated as FAT32 just so I can get back into practice with having a real interactive computer network again.  (plus I love doing things like that :) ) and I have a windoze only user in the house so it would let her back up things as well, as I know she'll never switch unless M$ goes belly up, rots in the sun and no-one ever supported Windoze again.

---

### Post by yellowband on 2007-08-23
if you find you can get the functionality you want from samba, consider using NFS instead.  It is surprisingly easy and fast to set up. with a simple entry in your client's fstab file, you can mount any network share.  that share, then looks like any other directory on your cpmouter, and programs like amarok have no trouble using them.  

not too sure how to use NFS with windows though.  i thik you need a program install in windows to access nfs shares.

---

### Post by mcduarte2000 on 2007-08-23
> **yellowband said:**
> if you find you can get the functionality you want from samba, consider using NFS instead.  It is surprisingly easy and fast to set up. with a simple entry in your client's fstab file, you can mount any network share.  that share, then looks like any other directory on your cpmouter, and programs like amarok have no trouble using them.  

not too sure how to use NFS with windows though.  i thik you need a program install in windows to access nfs shares.

Thanks, but can't, the Samba server is a DNS-323 from D-LINK. I don't want to play with the Linux of the machine... Just really wanted that the Linux on my computer could access the files properly with it (as Windows does). ;)

---

### Post by mcduarte2000 on 2007-11-10
The final solution:

```

//lua/Volume_1	/mnt/lua	smbfs	user,rw,sync,auto,exec,uid=miguel	0	0

```

---

