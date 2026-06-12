---
title: "Advice on VMware"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by WipeOut on 2006-10-15
Hi,

Hopefully someone can provide some input for me..

I have two servers currently in my office.. A very old Windows2000/ Exchange2000 server and a Samba file server based on CentOS 4..

I started reading up on VMware Server and in that research found that Ubuntu is one of the recommended OS's to run the VMWare server on..

So here is my plan..

I want to setup a Ubuntu server on some newer hardare and then was thinking about migrating the windows server and the file server into virtual machines..

Then I got to thinking that maybe the performance of the file server would be an issue being in a virtual machine and also the fact that we have about 100GB of data on our file server would mean quite large virtual disks..

Has anyone run file servers in virtual VMware machines?
Does it easily handle over 100GB of data?

Thanks, for any thoughts in advance..

---

### Post by lamego on 2006-10-15
WipeOut,
if you are doing an hardware upgrade, you will probably get a much higher performance even using VMWare, the vmware virtualization does not add much overhead and may eventyally performe better than the real system (due to VM optimizations that may not be able on the quest OS).

But why don't you just move your file sharing service to native Samba on Ubuntu and just keep the Exchange with VM ?

---

### Post by WipeOut on 2006-10-15
Hmmm.. didn't think of that.. Run the Ubuntu server as the file server and then put the Windows server into a VM.. That would also save on the required memory in the new pc because I wouldnt have the overhead of three OS's only two..

Thanks for the input.. Going to have to do a little more testing I think and work out what will be best for me.. :)

---

