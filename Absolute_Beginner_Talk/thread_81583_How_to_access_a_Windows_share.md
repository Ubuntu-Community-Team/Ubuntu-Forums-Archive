---
title: "How to access a Windows share?"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by arsbadmojo on 2005-10-24
I am running ubuntu 5.10 - and I saw that there was already a thread discussing this being a potential bug in the 5.10 forum, however - a poster there posted a workaround that isn't working for me, so I'm not sure if this is a legitimate bug, or if (more likely) I'm just doing something wrong.

When I click on Places->Network Servers there is an icon for "Windows Network" however, selecting that results in a blank window.

If I try to use Places->Connect to Server...->change type to "Windows Share" I have tried using both hostname and IP address in the "server" field, the share name in both the "Share" and "Folder" fields and then click connect - nothing happens. No error, no hourglass, nothing.

The shares I am trying to connect to are in a Workgroup. Is it possible that I need to create an account on the Windows server with the username/password of my ubuntu account?

---

### Post by arsbadmojo on 2005-10-26
Anyone?

---

### Post by wishyjr on 2005-10-26
is there a specific folder 'shared' on windows that you need to point it to? sorry, i dont really know what im talking about, just bored at work! :)

i do know that there is an article in issue 5 of tux magazine on this which you can download for free at tuxmagazine.org or something.

---

### Post by SilentCacophony on 2005-10-26
> The shares I am trying to connect to are in a Workgroup. Is it possible that I need to create an account on the Windows server with the username/password of my ubuntu account?

Hi. I have seen that do so clears up some people's problem with shares, so it's worth a try.

Also, check that *System > Administration > Network Settings*, in the *General* tab, has the proper workgroup name set in the domain name.

Oddly enough, on my setup, shares worked right out of the box on Breezy, though I remember having to set it up on Hoary...

---

### Post by arsbadmojo on 2005-10-28
[QUOTE=SilentCacophony]Hi. I have seen that do so clears up some people's problem with shares, so it's worth a try.

Also, check that *System > Administration > Network Settings*, in the *General* tab, has the proper workgroup name set in the domain name.

Oddly enough, on my setup, shares worked right out of the box on Breezy, though I remember having to set it up on Hoary...[/QUOTE]

I did this, the workgroup is just "workgroup" (really original eh?) but still nothing.

I then thought maybe I needed to make an entry in the hosts file (even though I have tried both the hostname and IP of the Windows PC) and still nothing.

If I go to Places->Connect to Server, change the Service Type to "Windows Share" do I need to complete all of the fields? All but "Server" are listed as "optional"

They are:
Server (in here I have put the hostname and IP with no change)
Share (I put the share name)
Folder (The folder name and the share name are the same, I have tried leaving this blank and the share name)
User Name (I've tried an account on the Windows PC and leaving this blank)
Domain Name (I've always left blank)
Name to use for connection (Didn't know what this was, left it blank)

Always the same thing; nothing. No hourglass, no error.

Same when I try to Browse the Network.

---

### Post by arsbadmojo on 2005-10-28
Is there any way to do it from a command line?

I'm from a Windows background, so I would do "net use * \\server\share" but I know the Linux file system doesn't use drive letters so much, so I really have no clue.

I've heard of samba, a long time ago when I was trying to figure out Red Hat to do the exact same thing someone told me I needed to configure samba.

Maybe I'll do a "man samba" from a command line and see what happens.

---

### Post by arsbadmojo on 2005-10-28
Wow, 7 pages...OK....

The smbd daemon provides file and print services to SMB clients, such as Windows blah, blah....

I don't think I need that unless I want to access the Linux shares from Windows - basically the opposite of what I'm trying to do; correct?

The smbclient program implements a simple ftp=like client. This is useful for access SMB shares on other compatible servers (such as Windows NT)

....booya Grandma, that looks like what I need......

---

### Post by arsbadmojo on 2005-10-28
OK, partial success! I did this from a command line:

smbclient -L [hostname] -U "Windows Account"

and was prompted for my password, which I supplied, and I'll be damned it it didn't give me a list of the shares. Cool...

OK, so how do I get to them? Can I...I know this is the wrong term, but 'map a drive' as it were?

---

### Post by arsbadmojo on 2005-10-28
GoogleFu says I should use this command:

mount -t smbfs //winbox/share /mnt/share -o rw,username=windows account,password=password 

but goes on to say:

Make sure you have a directory called /mnt/share before you try the mount. 

And I looked, and I don't have such a folder, and don't know how to create one. You'd *think* a "New Folder" option would be available under Applications->Accessories->File Browser, but no such luck.

Kinda stuck here.

---

### Post by arsbadmojo on 2005-10-28
Well, I was able to make a share directory.

I got "permission denied" the first time, so I used sudo before the mkdir command and that worked, but it didn't like my mount command. :confused: even when I used the sudo option.

---

### Post by thinhlegolas on 2005-10-30
Check this out, it was very helpful to me

[http://ubuntuguide.org/#mountunmountnetworkfoldersall](http://ubuntuguide.org/#mountunmountnetworkfoldersall)

---

### Post by Mustard on 2005-10-30
Here is another link that may prove useful.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

