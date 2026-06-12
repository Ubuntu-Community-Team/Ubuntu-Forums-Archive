---
title: "How to NFS"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-19
I thought I would submit this thread just in case anyone has problems with NFS.  I have asked questions about NFS on the forum and got little response. The guides on the Internet as a whole assume that it is easy and nothing ever goes wrong.  I know differently.   What is presented is a **very basic** guide, there are links at the end which will tell you how to make this less rough and ready....  but that is not the objective of what follows -

There are two parts to NFS, the Server and the Client.  The server is where the files are that are to be shared.  The client is the computer that wishes to share them.

**THE SERVER**
Best to set up the Server first.  To do this decide where are the files that you want to share and then 
System / Administration / Shared Folders 
and add the directory to be shared.  I use a directory at /home/shared/  Identify which computer is allowed to share the files and make the entry.  Ubuntu will most probably install NFS files at this point if something is missing.

Setting a shared folder will make an entry in the /etc/exports file for you, so no need to do it.

Check to see if NFS is working with```
 rpcinfo -p
```.  Look down the list for portmapper, nfs, nlockmgr and mountd.

Make sure that there is at least one file in the directory you are going to share or it will be difficult to test.

Then get the server up and running with 
```
sudo /etc/init.d/nfs-kernel-server restart
```

Read carefully for any error messages.  There will be one saying that sub directories have not been checked but this is not an issue.  Anything else needs to be checked and fixed before moving on.

That is all there is to the server.


**THE CLIENT**

On the client decide where you want to find the files that you are sharing.  Create a directory for this, say /home/common/

Then mount it

```
sudo mount 192.168.1.99:/home/shared  /home/common
```

The IP address here is that of the server.  /home/shared is the directory on the server to be shared and  /home/common is where you are going to find the files on the client.

The command line will then go away and return the command prompt. When this happens all should be working and if you use a file browser you should find the shared files in the directory you have identified.


**PROBLEMS**

Problems ......  if it does not just work then try the following - 

Read the links below .... or ....

On the client make sure that it can see the server.

```
rpcinfo -p 192.168.1.99
```

should give you a list of the services running on the server.  If you do not see this then you know that the client cannot reach the server.  This is then a network problem rather than NFS.

If you test the path from the client to the server and from the server to the client you may learn a bit more.

```
tracepath 192.168.1.99
```

will show you where the traffic is going or where it stops.  ping can do the same but without the information.

I had Firestarter installed and found it necessary to Stop the firewall.  Adding NFS to the policies did not help at all.  For me there was some fundamental problem with Firestarter which I have not yet resolved.


**LINKS**

This is where I found the best information to dig me out of the holes.

[http://www.linuxconfig.org/HowTo_configure_NFS](http://www.linuxconfig.org/HowTo_configure_NFS)
I liked this article very much.  It told me how to look for problems.
There is a small typo in the prerequisites – the space between file and systems can go.
Note the option on the page left to make a print friendly version.

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)
A bit dated in places and not written from the perspective of no prior knowledge.  Everything is there though.

If you spot any errors please let me know and I will edit to correct .......

---

### Post by ofb on 2007-11-19
Thanks. Here's some 'two cents' observations from my recent setup in 7.10.
[http://ubuntuforums.org/showpost.php?p=3780127&postcount=3](http://ubuntuforums.org/showpost.php?p=3780127&postcount=3)

Note: That post describes a very simple LAN composed of secondary NICs and a crossover cable. Anyone with a setup less separated from the internet must take security precautions with NFS. Also both machines have identical users -- hence no extra setup for users/groups/NIS, that a more complex situation would require.

---

### Post by LlNUX on 2007-11-22
Hi expatCM

thank you for a feedback :-) Its always good to have some feedback from people which reading this articles. ( tha I found this is just a coincidence )I'm glad that this articled help you.

typo is fixed now:-)

[http://www.linuxconfig.org/HowTo_configure_NFS](http://www.linuxconfig.org/HowTo_configure_NFS)

lubo

---

