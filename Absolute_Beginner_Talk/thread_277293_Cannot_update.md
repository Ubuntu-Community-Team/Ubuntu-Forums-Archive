---
title: "Cannot update"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by celim on 2006-10-14
I just installed Ubuntu 6.06 ytd
However I was unable to update using
sudo apt-get update

it will result in
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

I even had trouble in downloading the synaptic package which i wanted to install at 1st. The documentation for this version of Ubuntu is unclear. Is it I miss out some setting?

---

### Post by lreyes6 on 2006-10-14
r u behind a proxy???

---

### Post by taurus on 2006-10-14
Looks like those three sites in your /etc/apt/sources.list are offline right now!!!  You can try running it again later today or tomorrow...

---

### Post by celim on 2006-10-14
Nope
Using ADSL with a hub connecting few PC window based (home network)
Online is not a problem.
The problem only lies on connecting to Ubuntu via APT or update manager

---

### Post by Kateikyoushi on 2006-10-14
Isn't the problem the 1.0.0.0. ? Seems to me it can't resolve the address.

---

### Post by celim on 2006-10-14
Then how should i resolve the 1.0.0.0 since im a newbie here
Just solve my 1st problem
FF can't connect due to ipv6
Learning 1 step at a time
Havent gone through all the forum

---

### Post by Kateikyoushi on 2006-10-14
I wasn't aware you have connection problems with firefox.
That would explain it, seems you are trying to use ipv6.

Read[this thread]("http://ubuntuforums.org/showthread.php?t=225734") he had the same problems.

---

### Post by celim on 2006-10-14
I mean earlier on I fixed FF prob:
I cant surf due to ipv6
Has to disable it
Thn now I try to update but fail
So... is it 1.0.0.0 the prob? Or the server offline as what Taurus has spoken.

---

### Post by Kateikyoushi on 2006-10-14
The servers are online now. Just click those links and see for yourself.
I did not check them at the time taurus wrote that, but I am almost sure this is the ipv6 problem on your side.

---

### Post by taurus on 2006-10-14
Just got into the office to check with Ubuntu and those servers are online right now.  Run it again to see if you still experience the same problem!

---

### Post by celim on 2006-10-14
Still can't.
It is unreachable.
This goes same for synaptic too.
It will try to reach the host but fail.
Yet... if i plug the URL into FF, i can get response for instance...
do i wish to download? for *.deb file

I wonder is this a good news? As i can download a file and install each at a time. But this sound kinda crazy for >100 updates

---

### Post by Kateikyoushi on 2006-10-14
Well, it makes sure the problem is in your rig.
Let's see your resolv.conf

```
cat /etc/resolv.conf
```

---

### Post by celim on 2006-10-14
celim@celim-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.1.1

In order to update is it something i need to set which i miss? just like to surf, we need to configure network, FF and network proxy.

---

### Post by Kateikyoushi on 2006-10-14
That's the culprit but makes me wonder how did your FF work without dns.

You have to add your nameserver's ip there, can get it from another machine.

Then open that file for editing with the following command and add the dns ip and uncomment the current one.

```
sudo nano /etc/resolv.conf
```

---

### Post by celim on 2006-10-14
Wo wo wo... u are going to fast.
Can u pls attach your /etc/resolve.conf
so that i can know what outcome is expected
when you type this command

I do appreciate if you can provide me step by step assistance
Coz im too Window based
Still new too all those directories and command

By the way... its fun as Linux we can learn and share solutions
thx for ur guidance

---

### Post by celim on 2006-10-14
Can anyone pls help me? I still can't resolve my problem.
I can't connect to archieve of update
using Synaptic nor Update Manager
But my FF working just fine](*,)

---

