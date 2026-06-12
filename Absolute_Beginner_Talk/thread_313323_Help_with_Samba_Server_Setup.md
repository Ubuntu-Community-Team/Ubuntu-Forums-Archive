---
title: "Help with Samba Server Setup"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Ionix on 2006-12-05
Hi let me get you into the whole picture first

I have setup my Samba Server and have customize the smb.conf as the  one pasted on [http://pastebin.ca/268846](http://pastebin.ca/268846) .

I have remote access to the samba server using PuTTY. It shows that all my services is running, including smb.

I have also set chmod 766 to /var/samba/Kaiyang.

Now on Windows XP. I setup a network call XQNET the same as the one for samba. Now I can see both machines on "My Network Place", but I cannot access the samba server..

Windows XP give me this warning msg.

\\Xqsvr200611 is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.
The network path was not found.

The *.logs on linux box are nmbd and smb... all all showing normal msg... nothing is wrong in there.

I have also tried accessing \\*ip address, but it's not working either.


So I am actually stuck at this point. Will hope to get help from here. Thanks...
](*,)

---

### Post by Ionix on 2006-12-05
*Bump

---

### Post by dann0 on 2006-12-06
I usually create a samba-share like this:
[public]
        comment = Public stuff
        path = /public
        available = Yes
        public = Yes
        writeable = Yes
        browseable = Yes
        create mask = 0777

You also have to add yourself as  samba user:
$ sudo smbpasswd -a username

I always use the same username and password in samba as in linux.
(that way, you can access your home-directory to)

Then you can connect from windows with your linux username and passsword.

---

### Post by Ionix on 2006-12-06
Tired the same username/password thing...

It's not working, please advise in the more technical aspect. More like did I forget to do anything, is my smb.conf wrong etc...?

Thread Status: Unanswered

---

### Post by Iowan on 2006-12-06
> **Ionix said:**
>  is my smb.conf wrong etc...?

Post it...

---

### Post by burek on 2006-12-06
[http://www.linuxquestions.org/questions/showthread.php?t=458914](http://www.linuxquestions.org/questions/showthread.php?t=458914)

last post

---

### Post by Iowan on 2006-12-06
[SIZE="1"][FONT="Arial Narrow"]Sorry...[/FONT][/SIZE] I missed the [link]("http://pastebin.ca/268846").
 I presume you've run **testparm**?  I'm unsure what the defaults are for some parameters - like **security=** or **passdb backend =**.  The problem seems to be in authentication - perhaps some of these parameters need specific values assigned.

---

### Post by Ionix on 2006-12-06
I don't think I remember seeing those settings. Mind showing me how to configure your samba settings?

And also is it necessary for me to actually create a workgroup network on my windows xp so that i can see my Samba Server?

---

### Post by Iowan on 2006-12-06
I copied the original first, then modified the settings in the default **smb.conf** - a sample of which is in the link in **burek**'s post.  

My server's **smb.conf** is kinda junked up - I'm about halfway between a workgroup and a Samba PDC, so the parameters are kinda mixed.  I'm afraid it would cause more confusion than it answered, but I could post it (or PM it to you) if you think it'd help.  There are other examples around the forum, too.

Although not absolutely certain, I suspect the XP machine will need to be in the same workgroup that Samba is serving, so I suppose the answer to your question is **yes** (although it sounds like you've already done so...)

---

