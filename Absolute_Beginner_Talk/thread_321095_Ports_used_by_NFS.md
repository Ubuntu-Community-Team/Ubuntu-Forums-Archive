---
title: "Ports used by NFS"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-18
Hello Folks , 
                  I wanted to know which ports are used by NFS , 

I know that 
2049 : NFS 
111   : potmapper 

I wanted to know which other ports are involved 

Thanks in advance

---

### Post by JayTee on 2006-12-18
RPC Portmapper		TCP and UDP 111
NFSD			TCP and UDP 2049


Yes, these ports are used by default but you might want to refer to this link so as to understand how NFS is setup and uses the portmapper.

[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#FIREWALLS](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#FIREWALLS)

"The other daemons, **statd, mountd, lockd, **and **rquotad**, will normally move around to the first available port they are informed of by the portmapper."

---

### Post by lance_klusener on 2006-12-18
So there is no way to figure out which ports will services "stats mountd and rquotad" use . Cant we make them use static ports .

---

