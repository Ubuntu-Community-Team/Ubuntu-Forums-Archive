---
title: "Ubuntu Server dosen't seem to work for my needs."
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-02-01
Dear All, 

I've turned back here for one final question..

I've managed (after numerous attempts, failing, re-installing, breaking something, re-installing, you get the drift) to set up a Ubuntu box, getting access to the drives (My Network places) from my XP machine, etc... Messing with SAMBA, and LDAP, and all the other wonderful things that various websites show you tutorials.....but there is one thing I keep getting stumped on, unless I'm doing something wrong I don't know...(or it might be because I'm not as knowledgeable with networking as I thought I was)

Ok, long story short, messing around with Domain with NTServer2000 and XP Machines, when I start my XP Machines, I get a drop down that asks me which domain I want to connect to, being a home setup, I have two options, the local machine, and the current NT Box I've got running...

As said above I really want to switch to a Linux box, but for the life of me, no matter what I do, no matter which .conf file I tweak, I am starting to come to the conclusion, I'm not able to get the Linux Box to list in that drop down to allow the user to log into the Linux box, and not the NT box (as I wanna run the two along side each other while testing/playing etc).

I've read numerous posts on various sites saying that you 'dont' connect to a linux box, you bind to it? that bit stumps be straight away.

I think my final question is, before I hold my hands up and say it it way out of my league, will I be able to achive on my XP machine, a domain name that lists the Linux box for the user to connect too, as well as my NT box?

I've tried various sites, and various methods for altering config files (all of which I replace relevant items to match my requirement) I am still hitting stumbling blocks, like being able to add users to LDAP from command prompt, but not being able to add them using WebMin from my XP machine....

I think the problem I have, the various tutorials I've come across, all seem to have a bit of what I need, and I don't think the system likes me overlapping them....

Where do I turn, I would really like this setup, but I've been trying this for over a week now, at about 4-5 hours at a time. That like 35 hours of my life, and not being able to achieve my requirements, and it is starting to frustrate me now....

Can anbody help me?

Regards
Paul.

---

### Post by randomnumber on 2007-02-01
You confuse me.

I think you are trying to connect a xp machine to a ubuntu machine. (darn you for making me boot XP again, just kidding)

What I do is install a ssh server in ubuntu and use a program like filezilla ( [http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/) ) to gain access to the files. This used more for getting files accross the internet but it should work for now.

I tried some of the smb stuff but I can not get it work correctly yet. I only spent 20 min working on it. 

If you are wanting to share files from ubuntu to ubuntu it can be done the same way excluding the filezilla part. You just get the ip of the computer and connect to it. 

Any way you have something for me to work on.

hope this holds you over for awhile. I generally on moving files across the internet and not worry to much about local intranets.

---

### Post by dcstar on 2007-02-01
> **peejaygee said:**
> Dear All, 

I've turned back here for one final question..

I've managed (after numerous attempts, failing, re-installing, breaking something, re-installing, you get the drift) to set up a Ubuntu box, getting access to the drives (My Network places) from my XP machine, etc... Messing with SAMBA, and LDAP, and all the other wonderful things that various websites show you tutorials.....but there is one thing I keep getting stumped on, unless I'm doing something wrong I don't know...(or it might be because I'm not as knowledgeable with networking as I thought I was)

Ok, long story short, messing around with Domain with NTServer2000 and XP Machines, when I start my XP Machines, I get a drop down that asks me which domain I want to connect to, being a home setup, I have two options, the local machine, and the current NT Box I've got running...

As said above I really want to switch to a Linux box, but for the life of me, no matter what I do, no matter which .conf file I tweak, I am starting to come to the conclusion, I'm not able to get the Linux Box to list in that drop down to allow the user to log into the Linux box, and not the NT box (as I wanna run the two along side each other while testing/playing etc).

I've read numerous posts on various sites saying that you 'dont' connect to a linux box, you bind to it? that bit stumps be straight away.

I think my final question is, before I hold my hands up and say it it way out of my league, will I be able to achive on my XP machine, a domain name that lists the Linux box for the user to connect too, as well as my NT box?

I've tried various sites, and various methods for altering config files (all of which I replace relevant items to match my requirement) I am still hitting stumbling blocks, like being able to add users to LDAP from command prompt, but not being able to add them using WebMin from my XP machine....

I think the problem I have, the various tutorials I've come across, all seem to have a bit of what I need, and I don't think the system likes me overlapping them....

Where do I turn, I would really like this setup, but I've been trying this for over a week now, at about 4-5 hours at a time. That like 35 hours of my life, and not being able to achieve my requirements, and it is starting to frustrate me now....

Can anbody help me?

Regards
Paul.

Ok, you have to grasp the concept that Microsoft will only allow you to join ONE Domain, and any other resources have to be a part of that Domain (or "Trusted" by that Domain).

You basically have to make your Ubuntu box part of your existing Domain, or set up a new Domain (in the Samba config) and then join all of your Windows workstations to it.

You will have to search out detailed instructions for these options.

---

### Post by peejaygee on 2007-02-01
I've stumbled across 

[http://www.enterprisenetworkingplanet.com/netos/article.php/3457461](http://www.enterprisenetworkingplanet.com/netos/article.php/3457461)

which at first instance, appears to be a nice way to go about it.

I've done what it says up to 

[Join the Samba BDC to the NT4 domain] 

and executed the command

net rpc join -S server -UAdministrator%password <---replaced that with the proper password, and I get the error

[2007/02/01 18:15:16, 0] passdb/secrets.c:get_trust_pw(535)
  get_trust_pw: could not fetch trust account password for trusted domain HOMENETWORK
[2007/02/01 18:15:16, 0] rpc_client/cli_pipe.c:get_schannel_session_key(2418)
  get_schannel_session_key: could not fetch trust account password for domain 'HOMENETWORK'
[2007/02/01 18:15:16, 0] utils/net_rpc_join.c:net_rpc_join_ok(70)
  net_rpc_join_ok: failed to get schannel session key from server server for domain HOMENETWORK. Error was NT_STATUS_CANT_ACCESS_DOMAIN_INFO
Unable to join domain HOMENETWORK.

I'm a stumped with that, I've looked in my AD on my NT Server, and sambaserver is showing as a created user, so I'm guessing it is comminucating, and I've added the computer LINUXSERVER as a computer in my AD..

What am I doing wrong?

Regards
Paul.

---

