---
title: "Secure share with Ubuntu 7.10"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by manfarb on 2008-01-01
I've been working with Ubuntu 7.10 for a week or two now, and for the most part have it doing what I want.  I've found information about Samba to be somewhat varied, confusing, and inaccurate.  I wish there was a definitive document that would show me how to properly share a folder that a Windows XP box can access, but I want it to be secure, so the rest of the family PCs (I have 3 teenage boys with PCs) can't get to it without logging in.

Right now I've got shared folders working, but I did it with what I'm sure is a fairly common method of editing the smb.conf file and adding/modifying the "security = share" line.

I've found documentation that has me adding a user with the "smbpasswd -a username", but that doesn't work.  I've found documentation that has me change the browseable parameters and the writable parameters in the smb.conf, but that doesn't work.  I found a video on YouTube that I think was for 6.10, but that didn't work.  It sure seemed like the guy knew what he was talking about.  I think the problem is that I haven't found a document that includes all the steps.

So for now I've got an unsecured share, and I just want to make it secure.  Can anyone direct me to the right information?  And maybe this is asking too much, but I'm hoping I don't have to wade through all sorts of documentation.  I would have to believe that someone else has needed the same thing.  FYI, I've got the workgroup set to the same name on both the XP box and the Ubuntu box.  And I don't have a domain controller on our home network.

---

### Post by rivalarrival on 2008-01-02
You're want to "secure" the share by requiring authentication: people have to enter a username and password in order to access the share.

No problem!

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_home_folders_with_read_only_or_read.2Fwrite_permission_.28Authentication.3DYes.29](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_share_home_folders_with_read_only_or_read.2Fwrite_permission_.28Authentication.3DYes.29)

The "security = share" line means, in this case, "do not require authentication". You want to change this to "security = user" which will require a user to authenticate with the server.


I've had real good luck with ubuntuguide.org. It's the first source I go to when I can't figure out what I'm doing.

---

### Post by manfarb on 2008-01-02
Well I was up until 4 AM working on this, and I finally got it.  I think I had things so hosed up that I decided to do a re-install of Ubuntu and then everything went just fine.  To be honest, in all the documentation I looked at I'm not sure that any of it made it clear that you need add a user in the Ubuntu Users and Groups maintenance before running the "sudo smbpasswd -a username" command.  It's also possible that the username I was running on my XP box "man" (those are my initials) is maybe not the best username for whatever reason.  Not sure about that though.

Anyhow, after re-installing Ubuntu, I changed my XP box username to something more obscure, added that same username to Ubuntu, ran the smbpasswd command for that same username, did all the other stuff like enabling sharing and things, and it all just worked.  Didn't even have to edit the smb.conf file.

So I'm a very happy Ubuntu camper.  I've now got a P4 1.6 gig Ubuntu box with a 200 gig drive holding all my data and every morning a combination of GRSync and KCron syncing that data to a 250 gig drive, all shared out nicely to my main PC which is a XP Pro box.  And of course I have the VNC remote desktop enabled so I can VNC into the Ubuntu box from my XP box.  There's a couple of things I want to do with the Ubuntu box, like use GRSync to sync some Web sites, and I would like to be able to have VNC active at login-time, but I'll tackle those down the road.

So thanks for you help.  I'm thinking about documenting my entire Ubuntu experience in the forum.  We'll see.  I did document all my steps with that late-night re-install (it was my 3rd time) last night, so it wouldn't take much to post it.  Again, thank you!

---

### Post by rivalarrival on 2008-01-04
Switching to Linux from Windows Server was tough... There is just so much more to each task that must be configured before anything even starts to work...

Samba was a big stumbling block. PPTP client and server really kicked my butt - for awhile, I had a windows server doing nothing but acting as a VPN gateway because I was so frustrated with PoPToP that I wanted to scream!

Most of the problem was, as you mentioned, hosing up good configurations trying to find that elusive setting that makes everything else just click into place. I learned that unfortunate tactic from Win2k server. Every time you turned off a feature, like RRAS or IIS, you had to reconfigure the whole thing to restart it. So, if you foul something up, just restart and hope you get the configuration right the next time.

Glad to hear you got it working!

---

### Post by Borbus on 2008-01-04
By the way, if you want a really secure "share" you should use SFTP. There is a windows client called WinSCP. With SFTP even the contents of your file transfers are encrypted with SSH. It's safe to use it over the internet.

edit: I'll have to disagree about a Linux server being harder to set up than a Windows server. I've used both and Debian is much easier to set up than server 2003. With server 2003 I had to go through a load of stupid authentication crap to get remote desktop working. With Debian ssh just works after typing apt-get install openssh. With windows you can set up windows shares for windows clients, using a domain maybe. Doing this properly takes a long time, but you can hack it and do it insecurely quite quickly. With a linux server it might be a bit harder to cater for windows clients, but for linux clients it is so easy. Just install NFS with a single command, edit a bit of config file and mount the shares on the clients. So easy. Not to mention setting up services such as webservers etc.

---

### Post by manfarb on 2008-01-06
Thanks, but I think I'll stick with Samba.  I have to believe it's secure enough for our home network, and at least for the time being, I don't need to get to my data externally.

---

