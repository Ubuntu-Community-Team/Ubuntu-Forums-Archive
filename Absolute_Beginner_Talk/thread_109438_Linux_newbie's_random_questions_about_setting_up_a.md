---
title: "Linux newbie's random questions about setting up an Ubuntu server..."
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by DocLandolt on 2005-12-28
So I've been a Windows guy for I don't know how long -- but I needed a little partitioning tool and downloaded the Ubuntu 5.10 LiveCD a few weeks back, and I haven't been able to get it out of my head since. Up until then, I haven't so much as laid a finger on any Linux distro, but I really didn't even know what I was missing!

So I've spent the last few weeks reading as much as I could find on Linux, and I'm about to make the transition to Kubuntu full time on my laptop! I've also been planning on building a server, and now it's DEFINITELY going to be a Ubuntu server (well, largely -- I want to have do it up right and run it all under Xen). However, before I really start this project (and before I dump ALL of my media on to a shared drive to make some room for Kubuntu), I have a ton of questions that I just can't seem to find good answers to, particularly as they apply to the (K)ubuntu. If any of you have any good thoughts or answers on anything I'm writing about, or things I might not be considering, I'm all ears...


Setup:

- What exactly 'is' a swap volume and what would I use it for?
- Why should it be a seperate volume?


Xen:

- I plan on setting up and seperating out multiple Distros under Xen -- I haven't figured out the best topology, but maybe something like: a firewall; DHCP/DNS server; file server; and at least one full distro for me to play around in...what type of configuration tends to be recommended? Of all the network goodies, what should be seperated from what, and why?
- How easy would all this be to set up for a bit of a geek, but still a newbie?
- Based on the way Xen operates, couldn't I just download 'ideal' distro setups for a DNS server and a firewall, etc. to get myself going?
- Has anyone used it on top of their Ubuntu install? How does Xen allow you to 'switch screens' between the different computers it's running?
- Could I theoretically VNC into the top layer Xen hypervisor and switch back and forth working on the different virtualized Oses?


VPN:

- How easy is it to set up a software VPN in Ubuntu?
- What kind of security vulnerabilities would I be looking at 'out of the box'?
- What kind of reliability on the connection could I reasonably expect? What would I have to do to make it 'just work'?
- At my office we have a seperate hardware VPN box for security reasons -- while it seems to be pretty stable and I don't have too many problems with connectivity, is it really necessary? Can a software VPN be secure and rock-solid reliable?


VNC:

- If I'm VPN'd in, can I just run VNC strait through and get the monitor/keyboard/mouse and whatnot of the machine I'm attached to? If I'm attaching to an Ubuntu machine, would it function relatively smoothly, with all the pretty graphics and whatnots?
- Could I connect from a Windows client?
- Just how effective is this, as compared to, say, Remote Desktop Connection on 

Windows?
- I've read that to encrypt my VNC session, I should run it through SSH, but if I were going in through the internet, wouldn't tunneling through VPN work just the same?


SSH:

- In Ubuntu, if I have the above setup, would I ever really need to SSH in?
- What about with other distros? Does it make a difference?


RAID:

- I have 2 300 gb harddrives and a 250 gb one -- I've been racking my brain trying to establish the best way to set it all up. I was thinking throwing the two 300 gb drives together in a RAID1, which should still leave me plenty of room for my file server volume on that drive array, but what do I do with the 250 gb drive? Would it be easy for me to put together a software RAID5? How much storage space could I get out of that? Wouldn't it just be 500 gb with one of the 300 gb drives as a backup? Or could I slap them all together for more room without a single drive crash trashing my data?
- Could I significantly improve my situation by getting another 250 gb and slapping it together with the first one in a RAID1, having the 300 gb drives in a RAID1, and stitching them together in a RAID0? That would give me 550 gb, but would I still be better off in a RAID5 situation? I suppose what I'm asking is -- I'm kind of stuck with awkward drive sizes -- I'm not worried about spending a little bit more money, but how can I get the most out of these drives without sacrificing performance or risking my data?
- Will I need seperate IDE controllers for them all? Or should I do a hardware array and get a controller? How does all of that typically work?


FS:

- Can I have different file systems on the different volumes?
- I've read that would ReiserFS is better for file servers, or would it just be easier to go with ext3? Does it really make a difference?
- With all of the virtualized Ubuntu installs running under Xen, how would the drives be utilized? 

volumes be accessible?
- Would they use NFS? If so, how does it work?
- I know it's a UNIX network file system, but could I easily mount an NFS volume in Windows over a VPN?
- What does all of that have to do with Samba? If I set them up as Samba shares, would I be able to mount the shared fileserver to my Windows XP laptop, or any other PC, over the VPN? Could I do that with NFS?


Backup:

- As I also have my laptop that I use every day which will be running a dual-boot Kubuntu/WinXP, I'd like to have something that would periodically roll up the contents of its 80 gb harddrive onto my server somewhere as a backup. How would I go about doing this automatically?



Sorry for the novellette of questions here -- I have a million others -- but these are the pressing ones I really can't seem to answer on my own, but I feel like I need to know before I embark on this project. I know some of these questions don't belong here -- it's more of a compilation of random thoughts and concerns -- I appreciate any help you can offer, even if it's just pointing me to a better place to find help on a certain topic. Thanks...

Dean

---

### Post by piedamaro on 2005-12-28
Hi and welcome aboard!! ;) 
I'll try to answer to few items without going too in depth:
- What exactly 'is' a swap volume and what would I use it for?
- Why should it be a seperate volume?
*It's used to "swap" memory on physical disk when your ram is full, if you have ~1GB of ram you'll going to see minimal if any swap usage. 
It should be on a separate partition for performance, linux has a sofisticated swap managment which allows varoius swap volumes to run together with priorities. You can use a swap file too instead of a partition.

XEN:
*I have no direct experience, but I have it with uml linux, take a look at it too.

VNC:

- If I'm VPN'd in, can I just run VNC strait through and get the monitor/keyboard/mouse and whatnot of the machine I'm attached to?
*with vpn you become part of the net you're conneting to, right? So it will be possible to connect direclty with the server ip address.

-If I'm attaching to an Ubuntu machine, would it function relatively smoothly, with all the pretty graphics and whatnots?
*It would run relatively smooth but from what I seen remote desktop is smoother (and has better mouse pointer). It has his drawbacks too (msn invite etc)

- Could I connect from a Windows client?
Yes, with vnc client.

- Just how effective is this, as compared to, say, Remote Desktop Connection on
*Don't know every feature of remote desktop, but with I experienced dropped connections with vnc over the internet.

SSH:

- In Ubuntu, if I have the above setup, would I ever really need to SSH in?
- What about with other distros? Does it make a difference?
*ssh is much more reliable, every sysadmin in the world use ssh to manage his unix/linux server. (at least as the most important tool),

RAID:

- I have 2 300 gb harddrives and a 250 gb one -- I've been racking my brain trying to establish the best way to set it all up. I was thinking throwing the two 300 gb drives together in a RAID1, which should still leave me plenty of room for my file server volume on that drive array, but what do I do with the 250 gb drive? Would it be easy for me to put together a software RAID5? How much storage space could I get out of that? Wouldn't it just be 500 gb with one of the 300 gb drives as a backup?
*RAID5 doesn't fly like this: you have parity informations distrubited accross the 3 drives. If not the parity drive will cause a bottleneck like in raid3 adn 4 which in facts are rarely used. (if ever)

-Or could I slap them all together for more room without a single drive crash trashing my data?
*A single drive crash will not thrash your data in a raid5 setup. If you use raid0 (striping) it will.(did you mean that with "slap them together" ?)

- Could I significantly improve my situation by getting another 250 gb and slapping it together with the first one in a RAID1, having the 300 gb drives in a RAID1, and stitching them together in a RAID0? That would give me 550 gb, but would I still be better off in a RAID5 situation? I suppose what I'm asking is -- I'm kind of stuck with awkward drive sizes -- I'm not worried about spending a little bit more money, but how can I get the most out of these drives without sacrificing performance or risking my data?
*I'd do a RAID5 with spare disk, 4 drives total.

- Will I need seperate IDE controllers for them all? Or should I do a hardware array and get a controller? How does all of that typically work?
*I think software raid is better with each drive on a separate controller, as in a sata drives setup. Hardware raid will cost you a lot and I'd say it's more fitted for an enterprise enviroment.

FS:

- Can I have different file systems on the different volumes?
*sure :)

- I've read that would ReiserFS is better for file servers, or would it just be easier to go with ext3? Does it really make a difference?
*I use xfs for servers, it depends on the feature you are interested in: xfs is multiplatform, very fast, journaled, supports the largest partition and file size, and can grow the fs on a mounted volume! (think LVM)

- I know it's a UNIX network file system, but could I easily mount an NFS volume in Windows over a VPN?
*for windows file sharing you need samba, nfs is for unix machines. However there is a xfs client for windows, iirc.

- What does all of that have to do with Samba? If I set them up as Samba shares, would I be able to mount the shared fileserver to my Windows XP laptop, or any other PC, over the VPN? Could I do that with NFS?
*see above

Backup:

- As I also have my laptop that I use every day which will be running a dual-boot Kubuntu/WinXP, I'd like to have something that would periodically roll up the contents of its 80 gb harddrive onto my server somewhere as a backup. How would I go about doing this automatically?
*you need to write a little shell script and launch it periodically with cron.
There are tons of them on the net, and a lot of specifically designed apps such as amanda, if you managed to learn to use it!
Make a google search, you'll find much much more about every topic you asked here! Take a look also at tldp.org and everywhere in the forums howtos and on the ubuntu wiki.

Hope this helps :)

---

### Post by Bailx on 2006-01-04
some good questions, and i'm not the expert to answer them (ubuntu seems to lack the multitude of guru's you find on other distros.... or at least they don't come around here much).

anyways... i just wanted to complement you on your post, you pose some interesting questions about xen stuff, that i also am curious about.  

if i can add one thing to your list, it would be about xen and the art of how much hard drive space each virtual server takes. (at the bare minimum), and seperate files... updating packages, updating the kernel etc.  is the kernel simply mirrored, and do you upgrade packages on the "physical" machine or do you do a massive virtual package upgrade over all the machines.  also the xen kernel, i'm guessing it has smp support built in?  (i can't test cuz on every distro i've installed it on, it locks up during boot.... that includes distro's where it comes as an optional rpm package...this could perhaps be my 64-bit os environment)....

well.... not expecting to get an answer to any of these, not from here anyway, but i would prefer to use ubuntu... since it kicks ass.... and hope someone answers your questions for you..... some day :)

---

### Post by piedamaro on 2006-01-09
I hate people asking looong technical question yet not even reading the answers , it takes time to read and to answer.


Edit: removed personal insults / abusive language - manicka

---

### Post by zvodd on 2006-10-05
Aww, hey Dont feel bad. I found this page on google and it helped me.

Cheers piedamaro.

---

