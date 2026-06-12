---
title: "internet access works. updating doesn't."
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by justinol on 2006-10-16
Hello.
I have two ubuntu machines at home. one for my daughter and one for me.

she uses instant messagng and the internet a lot and loves ubuntu far more than windows (which used to keep crashing). She doesn't really have any need to update ubuntu so she's fine.

I enjoy ubuntu but am finding it less stable than windows when it comes to updating. which is very frustrating to me.

We use a wireless home network. A netgear wgl624 router if memory serves me and one netgear311 wireless adapter and an intel wireless adapter.

now any time i try and update ubuntu (on either of the two machines) it downloads the list of packages and soemtimes one or two of those packages but then stops downloading and actually crashes my LAN and i have to reboot the router to get internet access again. Every time.

I find this a great impediment to my complete adoption of ubuntu. I wonder how can it compete if updating (which IMHO should be one of the easiest and most attractive features of ubuntu) is so flaky? I have searched the forum and found lots of people with the same problem but no solutions, well there were a few solutions but not written in a way i can understand becasue i am new to ubuntu.

so to sum up a rambling post. why does general internet access (email, online browsing, instant messaging) all work fine but  updates don't?

---

### Post by dbott67 on 2006-10-16
It could be your sources.list file.  Could you please post the output of the following command **cat /etc/apt/sources.list**:
```
dbott@dapper:~$ cat /etc/apt/sources.list

deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

dbott@dapper:~$

```

Most countries have mirrored the repositories.  You'll notice that most of my repos start with 'ca'.  Yours will start with your country code (us, uk, ca, au, etc.).  You can use any mirrored repos you want (you're not obligated to use your own country).  You could safely copy my sources.list file and use it if you like (or use the main repos below):

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

1. Backup your current sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2. Edit your existing sources.list:
```
sudo gedit /etc/apt/sources.list 
```

3. Copy either of the sources.list from above and paste it into your sources.list.

4. Update your package manager by opening Synaptic & clicking RELOAD or typing the following:
```
sudo apt-get update
```

5. Try running the update again.

Keep us posted.


-Dave

---

### Post by dbott67 on 2006-10-16
It might also be some corrupted packages in the cache.  Try clearing it out (see attached image).

Select SETTINGS | PREFERENCES and then click on the FILES tab.  Click the "Delete cached package files" button.

-Dave

---

### Post by justinol on 2006-10-17
cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


thanks for the taking the time.

---

### Post by dbott67 on 2006-10-17
I take it you're running Edgy on both computers.  I don't see any issues with your sources.list file, but here is someone else's Edgy repos for comparison:
```
# Edgy Final Release Repository
deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse 

# Edgy Security Updates
deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse 

# Edgy Bugfix Updates
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse 

# Edgy Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

#Ubuntu Commercial
deb http://archive.canonical.com/ubuntu edgy-commercial main 
# deb http://archive.canonical.com/ubuntu edgy-commercial main
```

What happens when you clear the cache (post #3), click reload (to update Synaptic repos) and try to update from within Synaptic?

If that fails, we need to isolate where the problem is: (Edgy, wireless nic, router, Edgy repos, etc.)

**1. Isolating the OS:** Do you have a Windows-based (or multi-boot) system to check to see if it's only an "edgy-dependent" problem?

**2. Isolating the wireless component:** Can you try connecting via LAN cable (as opposed to wireless)?

**3. Isolating the router:** Can you connect your DSL modem directly to your computer (don't use the router)?  You'll need the PPPoE client, I think.   As an aside, you may want to update the firmware in your Netgear router.  On more than one occasion, I have had problems with various brands of routers.  Simply updating the firmware can fix many issues.

I couldn't find a WGL624, but I did find a WGU624 here: [http://kbserver.netgear.com/products/WGU624.asp](http://kbserver.netgear.com/products/WGU624.asp)

**4. Edgy repos:** Can you download files from other sources (music, videos, data files, etc.)?  If so, it may just be an issue with the Edgy repos.

Anyhow, before you fiddle around too much with your system, you may want to check the firmware on the router.

-Dave

---

### Post by mips on 2006-10-17
Try reducing the MTU value for tcp/ip.

---

### Post by justinol on 2006-10-18
thanks. i copied and pasted and now it works. of course being inexpereinced i used the dapper list you had with edgy. but then repasted my roginal list and it worked ok. the one difference (other than my dozy dapper/edgy) i noticed was my list had **#Added by software-properties** so i deleted that and things worked ok. 

this didnt make any real difference but was only thing i could see. unless it was an update from the dapper that got edgy wroking?

---

### Post by justinol on 2006-10-18
nope my mistake. i dont know what the problem was or is. it was working then i ruined ubuntu by trying to install video drivers. it wouldn;t start. so i reinstalled ubuntu and now the same damn problem.

---

### Post by justinol on 2006-10-19
ok. last reply. i have found a solution to this problem so hopefully this helps other new comers to linux like myself who find their internet updates broken.

i have tested this as a solution and it worked twice. basically it is a work around that somehow fixes the problem (which affected both my and my daughters ubuntu machines).

the solution is to install automatix and then when it asks if you want to restore your  server/ repository list (not the exact wording but you should get the idea) answer to keep the new updated list from automatix. 

why this fixes things is beyond me, but it worked for me twice (once after reinstalling my ubuntu and on the other machine as well).

hope this helps others.and maybe it gives people who know more about ubuntu than me (and thats most of you) a clue into the cause of the probelm and that clue might lead to the eradication of the problem itself in a far more technically sophiticated way.

---

