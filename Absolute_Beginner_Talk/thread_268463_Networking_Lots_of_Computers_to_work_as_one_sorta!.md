---
title: "Networking Lots of Computers to work as one sorta!"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-09-30
Hey there, this is my first time on a forum ever so please correct me if I have done anything wrong.

I don't really know if what I want to do is possible or have a name so I am just going to do by best to describe. I have tried searching but with no luck .

So I have a few machines at the moment running Kubuntu 6.06 LTS, and a server running ClarkConnect Home 3.2. What I want to do is setup the server so that I can manage user's etc and then have all the other machines use the server for all the user and the "/home" stuff etc.

Sort of like in a windows envierment with a domain.

I don't mind not using ClarkConnect it's just a hangover from windows. Although I do like it because It's very lite.

So first off can I do want I want to do? If so can I do it with ClarkConnect or not? If not with kubuntu anything else?

Any Help will be awesome.
Thanks.

---

### Post by kidders on 2006-09-30
Hi there,

It looks like you want all your computers to authenticate users against a centralised source, and store their home directories centrally too. One way to do that is to use LDAP and NFS. If you wanted to, you could use Samba to actually create a Windoze domain ... using LDAP as your user authentication mechanism makes this an option in the future.

The LDAP/NFS setup is quite involved ... post back if you like the idea, and I can explain in more detail.

---

### Post by guysmiley25 on 2006-09-30
Thank's very much for that, I'm still not too sure what I am doing but at least I know what to read up on. It has been bugging me for days.

Can LDAP be used between different linux distros? And will it make it so say a person logs on to one machine, creates a document then saves it logouts then the next day on a different machine and it still all the same. that sorta what I want to achive.

Yes I do like the Idea and some help will be awesome.

---

### Post by kidders on 2006-10-01
Yep, LDAP is pretty platform-independent ... even Windows can chat with an LDAP server! I use it to provide a central user/password database for Gentoo/Ubuntu/OSX/Windows boxes, so it's quite handy. In addition, other apps like mail servers/clients are often happy to use it.

The actual filestorage is a separate issue really. How you handle it depends on your requirements. If all your machines are running Linux, you can get it running immediately by doing something like this:

[LIST=1]
[*]Install an NFS server on one computer. It will become your profile server.
[*]Tweak its /etc/exports file to read something like **/home 192.168.1.0/24(rw,async,root_squash)**
[*]Modify every client's /etc/fstab to include something like **fileserver1:/home /home nfs defaults 0 0**
[/LIST]

This will cause each client computer's /home to be replaced by the one from the server, so before doing anything else, you should:

[LIST=1]
[*]Log out.
[*]Log back in as root (ie someome whose home isn't in /home).
[*]Do a **mv /home /home_orig**
[*]Do a **mount /home**
[*]Log out again.
[/LIST]

This will allow you to "merge" all the home directories more easily.

The problem with doing this right away is that, if the actual UIDs of your users on client machines don't match the UIDs of the same users on the profile server, NFS will deny people access to their own /home directories. This is why centralised authentication is important. So, before tinkering with LDAP, you need to sync all the UIDs. *Do not log in as an ordinary user before doing this!* It's worth noting that this is only a problem when you are _switching_ to a centralised user db.

[LIST=1]
[*]Look at the profile server's /etc/passwd. It contains all the server's UIDs.
[*]On the clients, change the ones that apply to **real people** to match those on the server. Once LDAP is working for you, you will be deleting these.
[/LIST]

Anything in the /home_orig directory that the changed users used to own will become inaccessible to them as a result, but the root user can put anything important back into the new /home directories later, and fix up the ownerships with **chown**. Having taken this extra step means that, if you accidentally screw something up when configuring LDAP, you won't get completely lost in the mess mismatching UIDs can create.

By the time you're done, you should have:

[LIST]
[*]All users authenticating against a single source, logging into any networked computer with the same password.
[*]All users forced to use a /home that is instantly updated on all computers.
[*]Password changes affect all computers.
[/LIST]

Then, you can start looking into performance issues, such as how to optimise NFS shares to work faster.

I hope this is of some help to you. Some things about switching over (as opposed to using a scheme like this from day one) confuse many people.

---

### Post by guysmiley25 on 2006-10-02
Thank you very much for the information, I am going to try it out after i've done a backup. One more question is that if I create a new user on the server will that user be able to logon to the computers on the network or do I have to create the user on then other machines as well and change the UID's? If so maybe there is a script or program that can manage it or is that what LDAP does?

I gonna start having a play now

Cheers

---

### Post by kidders on 2006-10-02
Oh no... the only reason you have to fiddle with UIDs is to *migrate* to the  centralised authentication scheme. You can leave that step out altogether if you like, but it can be helpful way of letting you deal with one set of problems at a time, if you know what I mean.

When you switch over, all your users might suddenly have different UIDs ... some users may even exchange UID with another user, making files owned by one appear to be owned by the other. If you eliminate that issue before actually implementing LDAP-based authentication, you'll have one less thing to worry about. So, it's not an _essential_ step per se.

Once LDAP is active, local user/group information is largely irrelevant. If you add a user to the centralised database, that user will be able to log in anywhere. If you add a user locally to a single client machine however, he will only have access to that computer.

I hope that clears things up for you ... sorry for being a bit unclear.

---

### Post by guysmiley25 on 2006-10-03
Cheers for that. Your help has been excellent. I am just about to start trying it out today. I found this website that has been useful as well [http://cs.dixie.edu/ldap/server/ldap/](http://cs.dixie.edu/ldap/server/ldap/) with out your help I would have not found it.

I am going to try setting up for windows and linux as well so then the option is there. I also decided to flag ClarkConnect as it was very limited. So I will use the ubuntu server.

But one other question I was pondering that you may be able to help with is that I would like my users to have a website and ftp access to there /home/username. maybe have like a /home/username/www for there website. Any tips will be awesome.

Also if I have the client machines setup like so, can you still login to the client locally if maybe network access was down or something? Or maybe for laptops, but I was thinking with laptops that it might be better to sync them with the servers /home/username insted?

One more thing that I don't really care about but just wanting to know for the sake of knowing, What about machines connect via VPN can that be done?

Sorry for all the question, But really thanks for spending the time to help me out. I'll be sure to pass on what I've learnt to help others.

Go Linux!!!

---

### Post by kidders on 2006-10-03
> **guysmiley25 said:**
> Cheers for that. Your help has been excellent.
Hehe no problem :-)

> **guysmiley25 said:**
> I found this website that has been useful as well [http://cs.dixie.edu/ldap/server/ldap/](http://cs.dixie.edu/ldap/server/ldap/)
That HOWTO doesn't seem too bad. Getting started with LDAP is pretty hairy, so there's no real easy way around all the messing about :-(

> **guysmiley25 said:**
> I would like my users to have a website and ftp access to there /home/username. maybe have like a /home/username/www for there website.
This one *_is_* easy! First, search /etc/apache2/mods-available for a file called **userdir.conf**. Tinker with it until it looks the way you want it. Then check that the file is symlinked to the /etc/apache2/mods-enabled directory (ie it is switched on), and restart apache.

Issue your users with these instructions:

[LIST=1]
[*]Make sure your home directory's "world execute" bit (o+x) is switched on. This allows the web server to traverse /home/username, even if it can't see what's in it.
[*]Create a directory called public_html (or whatever you decided to put in apache's config) in your home directory and give it at least world execute permissions.
[*]Create a file in public_html called index.html, index.cgi, index.php.... and chmod it to at least 644. (Type **cat /etc/apache2/apache2.conf |grep ^DirectoryIndex** to find out what index pages can be called.)
[/LIST]

Any user can temporarily switch off his website by "chmod o-x"-ing it.

To get FTP access going (something I would definitely not recommend), all you need to do is install an FTP server. The rest should, in theory, just work.

> **guysmiley25 said:**
> Also if I have the client machines setup like so, can you still login to the client locally if maybe network access was down or something? Or maybe for laptops, but I was thinking with laptops that it might be better to sync them with the servers /home/username insted?
If a client machine can't access the authentication server for some reason, only local users (ie those in /etc/passwd) can log in, unless of course you turn that feature off altogether. Obviously, there is no way around this, as it would defeat the purpose of having centrally stored user profiles/etc.

> **guysmiley25 said:**
> What about machines connect via VPN
The idea behind VPN is that connected computers behave exactly as though they were part of your LAN. If you can get VPN (eg OpenSwan) to cooperate for you (I've never had the patience!!), then you should experience no problems. The only thing your clients would need to be aware of is that their PCs would need to be told where to look for user profiles & authentication information. You would tell them to do the following:

[LIST]
[*]Make sure they're not using any of the UIDs you've chosen for **your** LDAP users on **their** computers for some reason. If they are, local file ownerships will appear screwed up while your network is handling authentication on their machines.
[*]Tweak their /etc/ldap.conf, /etc/nsswitch.conf, etc. as you do with your own LAN clients. You could perhaps write a little script to do this for them.
[*]Tweak their /etc/fstab so it knows how to mount the shared profile storage.
[/LIST]

**Edit:** Think of this as "joining a domain" in Windows terms ... except Windows has a pretty-looking interface that makes the config changes automatically, and makes you reboot ( ... grumble).

**Edit:** For Windows, don't let me forget to tell you about simulating a Windows domain server with Samba. The thing to google is "Samba PDC howto". All this stuff (LDAP authentication, central profile storage, Samba-based domain management) is terribly advanced btw ... are you *sure* you're only a beginner?!

I hope this continues to be helpful! Let me know if anything confuses you.

---

### Post by guysmiley25 on 2006-10-05
Thank you that is very helpful. Thanks a million.

I will how ever ask why you would not reconmend FTP? is it easy to hack or something? I think I will stick to ssh since it can do the same stuff as FTP anyways.

OK now for my problems. I set up the NFS server on the server and exported the /home path.

"/home 192.168.0.1/24(rw,async,root_squash)"

Then on one of my client machines straigh after I install xubuntu before I rebooted from the live CD i mounted the partition where I installed it.

I renamed /home to /home_org. then created and new /home

then added to my fstab file

192.168.0.1:/home /home nfs 0 0

Rebooted and all was good.

Then did the same with another machine but no such luck. thought It could be been becasue I was stilled logd in on the other machine so I turned it off. Still no such luck. so I went to log back in to the first machine and now it would work either.

both are saying something about not finding the /home stuff.

Ahh HELP!!! I have not installed anything else havnt done any LDAP or anything yet. but all the UID's username and passwords are the same for each machine. just that first user you have to put on.

Any ideas what it could be. I going to keep playing around with it for the mean time althought I can not think of what to do.

Thanks heaps for the help so far it have been great.

**EDIT:** ok it seams that I just have to wait ages before I login. anyway to speed this up? Maybe it's because it is still mounting the NFS share while i am trying to login. Maybe there is a way to make sure the share is mounted before the login screen come's up or somthings? any ideas?

---

### Post by kidders on 2006-10-06
> **guysmiley25 said:**
> Thank you that is very helpful. Thanks a million.
No problem :-) Glad I could help.

> **guysmiley25 said:**
> I will how ever ask why you would not reconmend FTP?
FTP is perceived as being easily hacked, so I imagine opening the FTP port on your server would attract attention to it. In reality, FTP *can* be conducted securely, but not all clients support that. On the other hand, SSH is a much more full-fledged means of giving users access to their data. For file transfers, FTP is *way* faster, but SSH lets people do lots more stuff :-)

> **guysmiley25 said:**
> OK now for my problems.
Thankfully, your NFS problem is easily solved. Your export only allows access to a single machine with IP 192.168.0.1.

To start with, I suggest granting access to your entire local subnet. Once things are working as they should, you can work on curtailing access if you want to, by individually specifying the IPs you want to let mount the remote filestore.

> **guysmiley25 said:**
> it seams that I just have to wait ages before I login. anyway to speed this up?
I wonder if this is NFS-related. Sometimes, NFS can take a while to mount a share. I don't remember off-hand exactly why this happens, but it is easily solved. (It happened to me once a few years ago ... if I could only remember why!!) Google will help far better than I can hehe.

On the other hand, it could be LDAP-related. When a computer can't access an LDAP server, it sits and retries over and over. This only applies to you if you've specified LDAP as the _highest_ priority authentication mechanism in your /etc/nsswitch.conf. If you do that, you have to live with the consequences when something fails :-? 

Any help? Let me know how you get on!

---

### Post by guysmiley25 on 2006-10-06
Ok solved here's my solution incase you or anyone else is interested. I googled around and not finding anything that helped, but I did find the people mentioned stuff about portmap. Then I thought do I have portmap installed? Turned out I didn't so I installed that and success. NFS is way faster now.

Thanks for the help!

Ok so now my next step is to install samba and Ldap and setup domain etc for windows.

On that site I posted at a earlyer date. They said to complie samba so that I would have the required parts. Is that required or dose getting samba by apt enough. Or maybe you can install the required featers as packages? Any ideas? Also I was wondering when you have window all setup does or can you have it so that /home/username is username's My Documents or H: or whatever? I have not see any clear indication that that is what happens? Also I will assume that the user's password for windows and linux will be the same and that if they change on one they change on both. Is that correct?

Thanks heaps for your time it has helped me move more and more into the linux world and I'm loving it!

---

### Post by kidders on 2006-10-07
> Then I thought do I have portmap installed?
Damn and blast... I shuda remembered that! Sorry.

The short answer to your post is "Yes" ... you can have things work pretty much any way you want :-) May I suggest something like this ...

[LIST]
[*]A Samba PDC with an LDAP Active Directory.
[*]Use NFS to share a centralised /home to Linux boxes.
[*]Use Samba to share /home/username as the "H: drive".
[*]Use LDAP authentication in Linux.
[/LIST]

That way, Windoze and Linux share the same users/passwords/homes, as you suggested.

There are a few things worth noting though:

First, Samba will appear (to Windows) to be a WinNT4 domain controller. This becomes a little awkward when you decide you want to start playing with your Windows domain policy. Another thing that comes to mind is that you may have trouble with Linux "system" groups. Here's a quick explanation:

Say you have a user called guysmiley in your LDAP database. You'll have no trouble adding him to Microsoft system groups, such as "Domain Administrators", because these groups are all stored in the Active Directory. However, you will also want to be able to add or remove him to/from Linux system groups, like "video", "disk", "audio", etc. My solution has been to add those to the LDAP database as well. That way, not only will guysmiley have the same password/home on all Linux boxes, but he will have exactly the same group memberships too. PM me if you don't know how to go about doing this... it can be a little hairy!

As regards compiling from source, you can do that if you *want* to, but I don't think it would be necessary. On some distros, it might be, but probably not on Ubuntu. The idea is that you would be able to deliberately select (or drop) specific features of the application to alter its capabilities.

Once you're done with Samba and LDAP, you can then start exploring other applications that have LDAP support, such as email, or things like the Microsoft Address Book.

---

### Post by guysmiley25 on 2006-10-10
Ok so I have started trying to install LDAP today following this guide

[http://cs.dixie.edu/ldap/server/ldap/page2.php](http://cs.dixie.edu/ldap/server/ldap/page2.php)

so I installed slapd

$ sudo apt-get install slapd

and it also installed theses

libiodbc2 libldap-2.2-7 libperl5.8 libslp1 perl perl-modules ssl-cert

It asked me for a admin password so I put one in. But the thing is that in that guide where is says "Choose these settings in the Debian initialization script" I assumed that I would prompt me for it during the install but no such luck. Apart from the admin password bit. Is there something else I'm ment to do? I'm not sure if I should keep contiuning or not.

Also domain part do I just make one up? I am currently having problems with my domian and host stuff I can't connect/ping computers on my network my there host name. I am aware of the hosts file but my machines get there IP via DHCP and even if they did have static IP's I would not want to configure the hosts file on each machine every time somthing cahnged. I have DHCP install on the same machine I want slapd installed. And I have masquerade setup as well.

Any help will be awesome.

---

### Post by kidders on 2006-10-10
Wow, this is turning into quite a thread!

So, first thing's first ... let's sort out this host naming thing :-)

My recommendation is to use a centralised approach here as well ... install Bind (a pretty standard DNS server) and see if you can configure it so:

[LIST]
[*]It only knows about the computer it's running on. Don't give it any addresses for your DHCP clients.
[*]It responds to DNS lookups by computers on your network. Tweak your DHCP server settings so it tells clients about your own DNS server.
[*]It forwards requests it can't handle to your ISP's DNS servers. Set the DNS server's own DNS server (hehe) to 127.0.0.1 to prevent odd behaviour.
[/LIST]

This will very marginally speed up DNS lookups on your local network, since your computers won't have to go fishing around on the web to look up sites' IPs. Restart your DHCP server and bring all DHCP clients' network interfaces down & back up again, to refresh the leases.

It's pretty vital, when messing with DHCP and DNS to give things **_short lifetimes_** (ie 10-30 mins), at least during testing. If you don't, changes you make will take far too long to propagate (ie up to 2 days).

Once you've gotten this far, try setting up pseudo-static network addresses for your clients. This means that, although their IPs will technically be dynamic, we'll arange things so they turn out the same each time.

Add lots of sections like this to your DHCP server conf, and restart all your networking again:

```

host laptop {
        ddns-hostname "laptop";
        hardware ethernet 00:11:22:33:44:55;
        fixed-address 192.168.5.116;
}

```

Now, regardless of what your laptop, say, would like to be called, or what address it would like to have, your DHCP server will force it to use these settings.

Finally, see if you can get DNS updates working. If you go googling for help, ignore anything security-related (such as keys) for the moment, 'til you've got things working. When you're ready, set up key-based DNS updating and block unknown DHCP clients. The result is a network where:

[LIST]
[*]All computers have predictable names & IPs.
[*]Your DNS server updates itself immediately, should you decide to change something.
[*]All your clients use your DNS server to look things up.
[*]Your system tries to resist DNS-based DoS attacks and won't offer unknown computers free information about your LAN.
[/LIST]

Test your setup by (a) Trying to ping the DNS server by name, (b) getting a client to ping itself by name, (c) switching on another client and seeing if the other realises it's there, (d) trying to ping a www site you haven't accessed in at least a week.

**NB: Whatever you do, never let your DNS server bind to an externally accessible network interface!**

---

### Post by kidders on 2006-10-11
Now for something about LDAP, hehe :mrgreen:

About a hundred million things can go wrong when you're setting up LDAP-based authentication, so go slow, and don't try to do too much in one go.

Step one is to ignore authentication altogether and see if you can get LDAP to work at all. Invent a domain for yourself ... preferably one with a short name, for later compatibility with Microsoft domain-based networking, should you want to go down that road. Find at least two HOWTOs, and see if you can (with the help of your brain) combine the two sets of instructions (which will almost never be the same!) into a one sensible string of tasks.

Here is a rough outline:

[LIST=1]
[*]Create your domain manually, with the server offline. This is done in a "language" called LDIF.
[*]Create a few "organisational units" for users, computers, groups, etc ... the basic structures of a network & authentication scheme.
[*]Modify your slapd config to include access details for a superuser. Don't try to add details about this user to the LDAP database.
[/LIST]

Now, start your LDAP server. At this point, it will be about as intelligent as a turnip ... all it will let you do is "bind" to it using your superuser's access details, which might look something like:

Username: cn=God, dc=mydomain, dc=com
Password: whatever

Conventionally, the superuser is called "Manager", which is a good enough reason *not* to call yours that.

Now, try adding a proper user to your database. Avoid using one that already exists on your system. The problem with doing this is that, for LDAP to model memberships of system groups, such as "video" or "audio", it needs to know about these too, which will cause all kinds of grief if their UIDs are not consistent throughout your network. Experience has taught me that the following (albeit a little ugly) is very, very advisable:

[LIST=1]
[*]Sync all your GIDs for system groups, such as "www-data", "named", "audio", "plugdev", etc.
[*]Duplicate all these groups in the LDAP database. Do not remove them from local group lists.
[*]Now sync all your UIDs that do **not** refer to real people, and duplicate these in LDAP as well. Reboot all affected machines and play with them a little, to satisfy yourself there have been no odd side-effects.
[/LIST]

Now you should be free to add a user. Test him by installing LDAP-based authentication support on a computer, and adding "ldap" to the "shadow", "password" and "group" lines in /etc/nsswitch.conf. LDAP-based authentication will begin to be used immediately ... you don't need to reboot or restart anything.

If you can log in as the newly-created user & see his (usually automatically created) home directory, you're in business. Type "groups" to make sure all is as expected.

From this point, forget your /etc/passwd, /etc/shadow, /etc/group, etc., etc. files ever existed! Possible next steps are to get LDAP & a mail server talking (fairly easy), or LDAP and samba (complex), or maybe LDAP and your address book/email client (a walk in the park).

**A note:** You will have to manually handle the addition of new system groups from now on, particularly if you place LDAP authentication ahead of others in /etc/nsswitch.conf (which I recommend, for simplicity). This will only affect you if you install something like a mail/web server, an antivirus application, etc., after starting to use LDAP.

I hope I haven't left anything out ... I was kinda running through what I remember from the last time I did this in my head, as I was typing ... but my memory is weird these days!

**Edit:** I *did* leave something out. I should have emphasised the need to retain duplicated system group & user information. Doing this allows your system to remain functional in the event it loses access to the LDAP server. You won't be able to log in as anyone useful (except maybe root), but at least your computer won't grind to a complete halt!

---

### Post by TheMono on 2006-10-11
I'm bookmarking this for when I get around to doing this myself at some point.... This thread has some of the most high quality questions and answers I've seen on this forum ever. 

Have you thought about writing an Ubuntu Howto? I mean, looking at the rest of this thread, you virtually have already lol.

Threads like this just make me feel good about this community.

---

### Post by kidders on 2006-10-11
Hi TheMono,

Thanks for your encouraging comments! What do you think, guysmiley ... should we throw together a HOWTO? :-k

---

### Post by guysmiley25 on 2006-10-11
Thanks TheMono not bad for my first forum eh. But all the credit goes to kidders, kidders has been excellent. Putting up with me and investing his time.

Yes kidders I think putting a How To together is a excellent idea, anything to contribue to the community and anyone else wanting to learn. I try my best to contribue. I would like to think that it would be quite good as that i'm trying to set it up at the moment and I don't like to do any steps without fully understanding them. So with all my crazy questions and your experience and skill to expain I believe the end product will be beneficial to a wide range of people.

---

### Post by guysmiley25 on 2006-10-11
Ok I don't really want to take a 90 degree turn here but I am. Maybe i'm getting myself in too deep.

So I've installed bind9 using these gudies here

[http://www.linode.com/wiki/index.php/Install_BIND9_in_Ubuntu_(Breezy)](http://www.linode.com/wiki/index.php/Install_BIND9_in_Ubuntu_(Breezy))
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

That second one will be real useful in the future because it does more than just DNS. Both guide where the same but it was good because One is for Dapper and the other Breezy so now I know it is the same for both.

When I search "apt-cache search bind" I found there was bind and bind9. What is the difference. I assumed that bind9 was newer and becasue I found ubuntu guides on bind9 and none on bind I went with bind9.

The other thing is that the gudie says to move the config files, and change the permissions and stuff. quote "For security reasons we want to run BIND chrooted so we have to do the following steps" Why is that? Surly if it was a problem it would come like that? unless there where certain configurations that it would not work with. And that is what my concern is.

Anyways I have done that trusting there jugment, I'm sure they would oh said somthing.

Ok so now i'm going to try and set it up as you recommeded. I have not found any good guide for how to do this but I am going to keep hunting. Is there a name for this type DNS configution. Searching for "bind how to" give you lots of what I have just done lol.

With this part of stuff
```
host laptop {
        ddns-hostname "laptop";
        hardware ethernet 00:11:22:33:44:55;
        fixed-address 192.168.5.116;
}
```

I have reason to believe that stuff like this goes in the /var/lib/named/etc/bind/named.conf. Just becasue there is stuff in there that looks like that. Guessing!!! But i'm not up to that yet so thats ok.

Now whats scary is do all these files correspond to the configuration of bind?

db.0
db.127
db.255
db.empty
db.local
db.root
named.conf
named.conf.local
named.conf.options
rndc.key
zones.rfc1918

!!!

Just wanting to make sure I was on the right track?

It's really weird with Clark Connect and Windows doing DHCP and DNS was quite easy, it makes you think, what was I missing out on? Even though linux has been difficult to get going and once your done it you know it and you have way more control over things.

---

### Post by kidders on 2006-10-12
You're doing well :-)

I'll try to be as brief as possible though ... I'm sure you're tired as hell of reading my long-winded posts!!

> **guysmiley25 said:**
> For security reasons we want to run BIND chrooted
This is often referred to as a "chroot jail". In simple terms, you create a Linux system within a Linux system, in such a way that it would be impossible for the inner one to gain access to the outer one. This eliminates the risk of falling victim to an unknown security-related glitch in the DNS server. Since you won't be serving the internet with your Bind install, it's not really something you need to be too worried about, but if you've already done it, you might as well leave things as they are. Personally, I wouldn't have bothered (lazy me!).

> **guysmiley25 said:**
> I have reason to believe that stuff like this goes in the /var/lib/named/etc/bind/named.conf.
Not exactly. The idea is:

[LIST]
[*]You make local name resolution files (in /etc) irrelevant by centralising all your DNS information with Bind.
[*]You deliberately leave out any information that has to do with DHCP-assigned IP addresses.
[*]You configure Bind to allow "updates", and set your DHCP server up to perform them.
[*]Now, when a DHCP client is assigned an address, it is added automagically to your DNS database. When the computer is turned off, the address is removed again.
[*]Thus, you can always refer to computers by name, and will never run into silly difficulties, just because one of the IP addresses changed.
[/LIST]

The chunk of text you quoted belongs in the DHCP configuration file. It takes things one step further by fixing the IPs that computers will be assigned, but there's no reason you'd *have* to do things that way.

> 
db.0
db.127
db.255
db.empty
db.local
db.root
named.conf
named.conf.local
named.conf.options
rndc.key
zones.rfc1918

Eeeep. If I start trying to explain that on here, we'll both get twisted up in knots! May I suggest a real-time chat ... that way, I could explain the fundamentals of DNS more easily.

> It's really weird with Clark Connect and Windows doing DHCP and DNS was quite easy
Yep... I'd say it certainly was!! The trouble with Linux is that it's usually impossible to do *anything* unless you know more than you ever wanted to about how it actually works :-( Think back to partitioning your disks, choosing which filesystems you wanted to try, etc., etc. You're in the deep end, right from square one!

Trust me though ... once you get your head around all the jargon, it's easy. I swear :???:

---

