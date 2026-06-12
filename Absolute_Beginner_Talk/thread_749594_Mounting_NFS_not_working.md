---
title: "Mounting NFS not working"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-04-08
Im using NFS.

192.168.0.12    Client     /media/shared/shared123           desired mount point
192.168.0.14    Server   /home/username/shared123       location of folder


I can get it to make a smb mount but everytime i try to mount it permanently i get an error with server permissions.

Any help on this will be greatly appreciated.

Saj

---

### Post by Joeb454 on 2008-04-08
Just curious, but have you tried mounting the folder through the GUI instead of the command line?

I could have totally misunderstood that, and you may be using the GUI anyway, but just for clarification purposes :)

---

### Post by saj0577 on 2008-04-08
Nope i dont see an option to. I right clicked it and clicked mount but its set as a smb://192.168.0.14......

Is that right for a permament link?

Saj

---

### Post by saj0577 on 2008-04-08
And on another computer i cant even see the shared folder in the Network Servers list.

Saj

---

### Post by bodhi.zazen on 2008-04-08
What protocol are you using ? You put NFS in the title and are talking about mounting with smb (samba).

What command exactly did you use to successfully mount the share ?

---

### Post by saj0577 on 2008-04-08
I Just right clicked ti and selected mount (on the computer that i can see it in the network list). But the server only has nfs installed not samba.

Saj

---

### Post by Jose Catre-Vandis on 2008-04-08
So have you installed the client software for nfs on your client:
```
sudo apt-get install portmap nfs-common
```

Have you exported your share on the server?

The syntax for mounting an nfs share should be as follows:
```
XX.XX.XX.XX:/files /media/mountpoint
```

Check out this thread for a full howto
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by saj0577 on 2008-04-09
sudo mount 192.168.0.12:/home/user/shared /home/user/shared

mount.nfs timed out

No luck :( i installed the portmap and nfs-common

Saj

---

### Post by saj0577 on 2008-04-10
Installed portmap and nfs-common on both server and client....

Saj

The Guides dont seem to be much help as they alll say the samething and when i do what they say it does not work.

---

### Post by Jose Catre-Vandis on 2008-04-12
You must be missing something somewhere. Post back with what you did on the server to set up nfs serving, each command and the folder assignments, and then what you did on your client. Also, what is the OS on your server and what is the OS on your client?

---

### Post by saj0577 on 2008-04-12
Okay i will do the above soon.
Ubuntu 8.04 on both now (was 7.10 on both when tried it)
I will start it all again and write down each step I do over this weekend so you can try and give me a helping hand. (using 7.10)

Cheers for the support
Saj

---

### Post by isparkes on 2008-04-13
Had a look at this?

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

I'm all out of ideas, but this guy sounds like he knows what he is talking about...

---

### Post by saj0577 on 2008-04-13
Cheers il take a look now.

Saj

---

### Post by saj0577 on 2008-04-13
Thats about SMB not NFS shares mate, but i will see if their is anything relevant in there.

Saj

---

### Post by komputes on 2008-07-05
OK, I'm not sure here, and this may sound totally ridiculous but have you already created the "shared" directory on the client machine? I think the directory/folder needs to be there as a mount point.

---

### Post by dancro on 2008-07-06
> **Jose Catre-Vandis said:**
> So have you installed the client software for nfs on your client:
```
sudo apt-get install portmap nfs-common
```

Have you exported your share on the server?

The syntax for mounting an nfs share should be as follows:
```
XX.XX.XX.XX:/files /media/mountpoint
```



Thank you, thank you, thank you.
This information has allowed me to resolve my mounting problems.  

Once again the forums have provided the answer.
After exporting on the server and mounting by server hostname on the client, I got a lengthy message about file type and others details about the mount command.  All of which was not enough to lead me to a solution.  

Your tip did it for me.

Thanks again.
Dan

---

