---
title: "Mint and security"
date: 2012-03-16
forum: Any Other OS
---

### Post by mrmedia on 2012-03-16
Okay - well the question is - is mint safe? 
ie. Things like flash, java, multimedia etc are installed by default. These are not always open source. Or are in unsecure repositories.

If a hacker is going to get into your system, it will be via the browser mostly, and desktop emulation using flash or java or remotedesktop software seem to be easy once in. 

(there is a scary easy desktop duplicating service on the net that uses java I saw once)

Personally i think that extra ram on video cards is used to store software, i think that control of the isp proxy server is used to launch attacks or redirect packets to get to your browser,  etc etc.  
And possibly there is a backdoor entry to most modem routers.
Even the common nvidia video software itself may be a common backdoor.

To me it is not too far an notion to stretch the idea that intelligence or security firm services use soundcard and videocard software, flash, java microsoft products for easy and effective entry to anywhere they want, anytime. 

Well i'm not trying to change the world, and running Centos with nothing installed but necessary software - is a bit bland. 

But would anyone care to give an opinion on the security risks that Mint exposes.

I am asking here because the Ubuntu community might be a little more skeptical than the Mint forum. 

Maybe Debian or Centos/Redhat in the raw-est form can be considered truely safe.

---

### Post by Elfy on 2012-03-16
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by craig10x on 2012-03-17
the stuff that mint installs are simply licensed versions...like Oracle (formally Sun) java 6 and Adobe flash, etc...libdvdcss2 (dvd encyption decoder) is from the medibuntu site (which is well trusted)...

actually, even ubuntu installs Adobe flash in it's restricted extras package and Microsoft fonts...(after you accept the license agreement)...mint simply installs more license versions where as ubuntu tends toward the open source ones...

doesn't affect security issues really at all...

---

### Post by Dangertux on 2012-03-17
> **mrmedia said:**
> Okay - well the question is - is mint safe? 
ie. Things like flash, java, multimedia etc are installed by default. These are not always open source. Or are in unsecure repositories.

If a hacker is going to get into your system, it will be via the browser mostly, and desktop emulation using flash or java or remotedesktop software seem to be easy once in. 

(there is a scary easy desktop duplicating service on the net that uses java I saw once)

Personally i think that extra ram on video cards is used to store software, i think that control of the isp proxy server is used to launch attacks or redirect packets to get to your browser,  etc etc.  
And possibly there is a backdoor entry to most modem routers.
Even the common nvidia video software itself may be a common backdoor.

To me it is not too far an notion to stretch the idea that intelligence or security firm services use soundcard and videocard software, flash, java microsoft products for easy and effective entry to anywhere they want, anytime. 

Well i'm not trying to change the world, and running Centos with nothing installed but necessary software - is a bit bland. 

But would anyone care to give an opinion on the security risks that Mint exposes.

I am asking here because the Ubuntu community might be a little more skeptical than the Mint forum. 

Maybe Debian or Centos/Redhat in the raw-est form can be considered truely safe.

You know...For a second, I thought that this might be a serious thread about the differences in security options included with the two. Ubuntu actually has more at its disposal than Mint does by default (Mint stripped out some vital things on account of wanting to boot faster than Ubuntu).

However, that's not what this is...

First, you can't "store" anything in RAM, at least not if you want it to be persistant, RAM is volatile memory, everything in it is gone on reboot, or shortly thereafter.

Also -- "security firms" I used to work for one...They don't want anything to do with your desktop PC they have better things to do with their time.

Yes it's easy to write remote administration tools in whatever language you'd like, Java included. As far as their being backdoors in prorprietary drivers. I find this unlikely, the developers barely spend enough time on them to make the hardware work right let alone build any "backdoor" functionality into them.

I have no idea what you're talking about with your ISP and proxys but if you're that concerned, use TLS. Nobody is breaking that at line speed any time soon. 

About the only thing you're concerned about that can actually happen is yes, you can get owned through your browser. Run No-Script.

If you want a compelling argument for the insecurity of Mint versus Ubuntu next time bring up the kernel level memory protection and mandatory access controls that are not present in Mint that are in Ubuntu. However with the things you're talking about I think you're just being paranoid.

Hope this helps.

---

### Post by mrmedia on 2012-03-26
yes paranoid, no not without reason. 

I experienced first hand an ongoing attack. Yes it was on windows, but i got new isp, new network card, new hdd, new windows OS, new login, new xecurity software, new telephone line and they were on my system again in hours. 

So i have gone from "who really cares" to "oh my god". Very unnerving and something you need to experience.  

If you or they have big money and wish to get background info on someone - i am certain the German or Russian experts out there can and do do paid work.  Different psych's exist. Not just "in the movies" stuff.

Why would someone be motivated to destroying my trading account - wiping me out financially, taking total control on my PC?  Good question. But the attempt happened.  

The comment about residing in video ram is re: attack point, unrecorded processes.
But is a guess.  
The comment about getting past your router but creating a subnetwork that allows easier access to you pc's is a guess too, but if I were a government dept I would first try that.

I thank you for pointing out the security changes and features dropped by Mint. This response is "exactly" what i am looking for. 

I'm only sorry I do not have more to add, on a technical level.

I use ubuntu and am considering moving to debian proper in case ubuntu has opened some loopholes. 

The thing about security is you can always pretend the threat does not exist or your rootkit hunters have done a good job.

I am grateful that Linux and security is something the OS was built upon. My feedback is - yes it is necessary. 
Anyone that uses online banking needs to be on Linux. Any business not in China with intellectual property needs to be on Linux - clients and servers.  ie lawyers engineers 

I will not even trust a mac, because I think they have a location finding feature.  i.e. you can ask apple to find you stolen pc.  
To me this indicates that there is some code that allows the machine to be found. Question is who has this code now that it exists.  Is similar to microsoft checking licence keys while you are on the phone and doing a search.

If i were a bank - i would create a rules that the OS and all the apps need to be open source - just to ensure that that "app" is not doing more that it should.

The level of use of windows in organisations is appalling.
The IT depts are all sitting there thinking they have done a good job. Have implemented the norm.  
Somewhere along the line - probably the push via recruitment agencies - the industry has done itself a disservice and allowed security become a non issue.

---

### Post by haqking on 2012-03-26
> But would anyone care to give an opinion on the security risks that Mint exposes.

no more or no less than any other OS overall depending on how granular you go.

there are vulnerabilities and weaknesses in any OS, the largest being the user, arguments for the merits for and against the security stance of a given OS has been done many times, all anything needs is one entry point.

The end

---

### Post by winh8r on 2012-03-26
I don't know if you have seen this page:

[https://wiki.ubuntu.com/BasicSecurity]("https://wiki.ubuntu.com/BasicSecurity")

It contains a lot of very useful information that is transferrable to other operating sytems to help you to implement a security policy to help protect you and your system.

As has been said many times on this forum, security is an ongoing process, in the hands of the user. It is not just something that you do once and forget about.
**You** are responsible for the integrity of your data and the security of your system. It doesn't matter what programs and applications are installed on the machine to harden security if they are not properly configured and monitored.

There are a lot of very informative threads in the Security Discussions sub forum here:

[http://ubuntuforums.org/forumdisplay.php?f=338]("http://ubuntuforums.org/forumdisplay.php?f=338")

It is well worth taking the time to read up on how you can maximise the security protocols available to you as a user.

However , always remember that the biggest security risk to any operating system is the user.

Hope this helps you.

---

### Post by mrmedia on 2012-03-26
Well this is interesting.

I started a job as a systems engineer.   It was a small business server operation.  I got a live cd of knoppix and was looking for the server via a samba daemon and whammy the SBS raid5 disk array crashed. 2 disks lost - unrecoverable.

Well you panic - as you would - being just new in the organisation and you replace it with a new build of SBS. 

Why would this happen, well maybe microsoft are attacking their own servers so that you blow all your budget replacing the existing setup. 

I sat there petrified of using linux in the workplace for another 5 years.

You may think it is a coincidence but i do not. Maybe it is linux dudes hating against SBS.  

It was all too much of a coincidence for me at the time, to not think that someone had a hand in it. Or that someone was in the system already and were now exiting.

---

### Post by haqking on 2012-03-26
> **mrmedia said:**
> Well this is interesting.

I started a job as a systems engineer.   It was a small business server operation.  I got a live cd of knoppix and was looking for the server via a samba daemon and whammy the SBS raid5 disk array crashed. 2 disks lost - unrecoverable.

Well you panic - as you would - being just new in the organisation and you replace it with a new build of SBS. 

Why would this happen, well maybe microsoft are attacking their own servers so that you blow all your budget replacing the existing setup. 

I sat there petrified of using linux in the workplace for another 5 years.

You may think it is a coincidence but i do not. Maybe it is linux dudes hating against SBS.  

It was all too much of a coincidence for me at the time, to not think that someone had a hand in it. Or that someone was in the system already and were now exiting.

Something crashed and it was Linux fault ?

Things fail you know.

too much paranoia

Peace

---

