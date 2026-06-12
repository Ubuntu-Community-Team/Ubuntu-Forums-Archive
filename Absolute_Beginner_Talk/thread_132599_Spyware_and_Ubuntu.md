---
title: "Spyware and Ubuntu"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-18
So I've heard a lot about how Ubuntu (and linux in general) doesn't get virues. Now, being a paranoid Windows user, I use the Aegis-Virus Scanner anyway. But I was just wondering if Linux is vounerable to Spyware? And if so, where can I get a good anti-Spyware program?

---

### Post by nalmeth on 2006-02-18
I have never heard of spyware affecting anyone here. These problems can't really take root for a couple reasons, without going into detail. There aren't yet a lot of people targeting linux, and the typical  malware affecting a windows filesystem can't get the neccessary permissions to do the same for linux. I have a router, and feel safe to go anywhere without a firewall, or anytype of spyware/virus protection. If you really want to feel secure, download clamav antivirus, and firestarter or guarddog firewall.

In the end, its about how smart you are with what you execute or don't. You could theoretically be tricked into installing malware, but you would need to give up your root password somehow

---

### Post by Bartender on 2006-02-18
I'm pretty sure spyware just bounces off Linux, but if you download something that contains spyware and bring it over to a Windows partition it'll jump all over that.

---

### Post by darkbullet87 on 2006-02-18
Ok, thanks for the info :)

---

### Post by cilynx on 2006-02-18
Spyware requires three things to be successful:

1. A market
2. A way of getting installed
3. A system that can run it

So long as we have stupid people buying things from spam, #1 will be satisfied.  Not much we can do about that.  Fortunately, that market is using Windows.  Thus, they are the ones targeted.  Economically, there's no point in advertizing to a tiny market that is smart enough to not buy your product.

#2 is where the Internet comes in.  More specifically, it's where IE comes in.  IE has this great "feature" that allows it to run programs with full system-eating permissions.  It also doesn't have to ask if you want to run things or not.  All to protect you from yourself.  Great, eh?  Linux does not provide such "features".  We figure that you can handle deciding what you do and don't want to run yourself.  You can also decide for yourself what level of permission things run at.  By default, pretty much the worst thing you can do is pooch your home directory as your default user doesn't have write access to anything else.

#3 is the technical kicker.  All of the adware / spyware / crapware out there was written for Windows.  It would be a serious pain to rewrite it all to run on Linux.  Refer to point #1.

---

### Post by SMF on 2006-02-18
I was reading this earlier you might get some ideas of what other people are saying.

I personaly find it just crazy!
Imagine no firewall, no anti-virus, no anti trojan and no anti spyware protection on my pc Linux ubuntu as I surf the net. Un-Freakin believable.

Basicly discussion about Firestarter.
[http://ubuntuforums.org/archive/index.php/t-35083.html](http://ubuntuforums.org/archive/index.php/t-35083.html)

About Shorewall:
[http://ubuntuforums.org/archive/index.php/t-327.html](http://ubuntuforums.org/archive/index.php/t-327.html)

And GuardDog:
[http://ubuntuforums.org/archive/index.php/t-9865.html](http://ubuntuforums.org/archive/index.php/t-9865.html)

These discussion threads were found here:
[http://ubuntuforums.org/archive/index.php/f-7.html](http://ubuntuforums.org/archive/index.php/f-7.html)

You might skim through that real quick too.

I have been surfing for 3 days on ubuntu and I have been to sites that I know are very dangerous if you don't have a decent anti-virus program while running windows and nothing has happend to my linux system\\:D/ 

Hope this was of use since I too am a new born Linux user:mrgreen:

---

### Post by montablac on 2006-02-18
isent linux just so freekin cool?

i mean,VERY little  viruses and net to no spy ware

theres my two cents

---

### Post by aysiu on 2006-02-18
Only a small handful of people *claim* to have gotten spyware on Ubuntu; though, no one's come forward explaining what the spyware was, how they knew they had it, or how they got it.

For more info, see [this poll](http://www.ubuntuforums.org/showthread.php?t=109278)

---

### Post by Ghetto_Smurf on 2006-02-18
spyware and viruses need root permissions. keep that disabled and you will be safe. very little viruses can activate the root account

---

### Post by SMF on 2006-02-18
[QUOTE=Ghetto_Smurf]spyware and viruses need root permissions. keep that disabled and you will be safe. very little viruses can activate the root account[/QUOTE]

How can i tell who and what if any has the root permisions. Can you tell me what to look for in that area. I have done some reading on the matter but am not clear. I have been able to do many things on my pc. One thing I did was let my pc log in automaticly so I dont have to enter my user name in pass word at the gnome when starting my pc. Is that safe? and does that effect my root permissions any. Thank you.

---

### Post by Ghetto_Smurf on 2006-02-18
SMF, that would be safe in case of keyloggers, but anyone can give a look at your username and password. i've read somewere about a guy who went to a company running linux, and with the kubuntu liveCD he just wiped out the root account password and made a new one with passwd. someone having acess to this log is very dangerous, but also very unlikely

---

### Post by cilynx on 2006-02-18
Ubuntu is a little odd (IMO) when it comes to root permissions.  Basically, they did away with the root account.  The solution is the use of the 'sudo' program.  In order for sudo to gain the permissions it needs, it must 1) be set up to do so (handled for you by Ubuntu) and 2) ask you for your password.

Thus, when Ubuntu asks you for your password after you have logged in, it is upping the permission level for whatever program asked.  It also may pop up a window telling you that it would like to do something as root and has your password cached.  This is there just to make sure you know what's going on.  Do not disable this window or tell it to automatically do things as root without the popup.

That's about it.  Anything that doesn't ask you for your password is running at normal reduced user permissions.

---

### Post by aysiu on 2006-02-18
[QUOTE=Ghetto_Smurf]i've read somewere about a guy who went to a company running linux, and with the kubuntu liveCD he just wiped out the root account password and made a new one with passwd. someone having acess to this log is very dangerous, but also very unlikely[/QUOTE] If you allow others to have physical access to your computer, they can do pretty much anything they want.

---

### Post by cilynx on 2006-02-18
WRT Taking over a Linux system with a Live CD:

This isn't a hard thing to do assuming the target filesystem isn't encrypted.  In all actuality, it's trivial.  Physical access is the security professional's nightmare.

This is also why encrypted filesystems are good...

---

### Post by Ghetto_Smurf on 2006-02-18
he didnt knew what password was because the filesystem was encripted, but he knew what lines he should remove

---

### Post by darkbullet87 on 2006-02-18
Wow, this is great. I'm amazed at the ammount of info I'm getting :) :)

So basicly as long as I don't mess with the way sudo runs and/or give root premissions to unessecary programs it should be fine....thats awesome!

---

### Post by cilynx on 2006-02-18
You're talking "encrypted password file".  On a normal filesystem, you can see the password file.  You can open the password file.  You can see gibberish which is the encrypted password.  On an "encrypted filesystem", you can't even see that there are files, let alone edit them, without the encryption key.

---

### Post by nalmeth on 2006-02-18
> don't mess with the way sudo runs and/or give root premissions to unessecary programs it should be fine 
precisely

---

### Post by darkbullet87 on 2006-02-18
Ok, all this talk about encryption has peaked my interest. How would I go about obtaining a good encryption program for Ubuntu. And yes, I know...Google. But not all excryption software is the same, some are better than others...whats "good" encryption software for Linux.

---

### Post by aysiu on 2006-02-18
kgpg works for me, and it's in the repositories.

---

### Post by cilynx on 2006-02-18
The official way is documented here:

[http://www.linuxsecurity.com/docs/HOWTO/Encryption-HOWTO/Encryption-HOWTO.html](http://www.linuxsecurity.com/docs/HOWTO/Encryption-HOWTO/Encryption-HOWTO.html)

A nice Google Answer here:

[http://answers.google.com/answers/threadview?id=29290](http://answers.google.com/answers/threadview?id=29290)

---

### Post by darkbullet87 on 2006-02-18
hmmmm...I did sudo apt-get install kgpg and I got a strange error message I've never seen before.

```
dave@ubuntutucker:~$ apt-get install kgpg
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```

So I figured I'd try and open /var/lib/apt/lists/lock to see what he problem was so I typed 

```
sudo gedit /var/lib/apt/lists/lock
```

but it just gives me a blank text editor page. 

Whats up with that?!?!

---

### Post by cilynx on 2006-02-18
apt-get needs root permissions:

```

sudo apt-get install kjpj

```

All it was telling you is that you didn't have permission (as a non-root user) to write the lock file.
(The lock file makes sure that only one package manager is running at once)

---

### Post by darkbullet87 on 2006-02-18
Wow, so I installed KGPG and it's running great. I got my encryption key all set up and evertying. I managed to figure out how to great new files and encrypt them with the software, but I can't encrypt exsisting files. Is is possible to encrp an exsisting file?

---

### Post by SMF on 2006-02-18
[QUOTE=darkbullet87]Wow, so I installed KGPG and it's running great. I got my encryption key all set up and evertying. I managed to figure out how to great new files and encrypt them with the software, but I can't encrypt exsisting files. Is is possible to encrp an exsisting file?[/QUOTE]

Lol you went from Spyware to encryption.

You are crazier than me 
:mrgreen:

---

### Post by darkbullet87 on 2006-02-18
Well, I figured no sence in startinga new topic when encryption was already beinmg discussed here a lil :)

If you guys want me to make a new thread for it though I will :)

---

### Post by mwanafunzi on 2006-02-18
I remeber a while ago coming across some articles on windows security and specifically, how to crack the windows SAM files. I have not tried using the what I have read, so I still have no idea how easy it is to get user passwords (usable) on a windows system. 
What I am getting at is this (and this is more of a question), theoretically, would it not be possible to write some malware that would run on the system; such that it goes into the file that the pwd is decrypt and decrypt the pwd. Given that (in ubuntu) the user pwd is the same as the root. Although many are saying that sudo adds an extra layer of protection. Is this not a huge security hole?

---

### Post by ubuntu27 on 2006-02-18
darkbullet87: Did you created a new thread for "Encryption"?

Anyway, guys, what do you think of TrueCrypt: [http://www.truecrypt.org/](http://www.truecrypt.org/)

Is it good? What's your opinion?

---

### Post by nalmeth on 2006-02-18
> I remeber a while ago coming across some articles on windows security and specifically, how to crack the windows SAM files. I have not tried using the what I have read, so I still have no idea how easy it is to get user passwords (usable) on a windows system.
What I am getting at is this (and this is more of a question), theoretically, would it not be possible to write some malware that would run on the system; such that it goes into the file that the pwd is decrypt and decrypt the pwd. Given that (in ubuntu) the user pwd is the same as the root. Although many are saying that sudo adds an extra layer of protection. Is this not a huge security hole?

Windows viruses don't require your password to function. You give it to them as soon as you log in and start all the applications that require you to wander around as administrator, with full system priviledges. Also, there is no root password for ubuntu, because there is no root user. Sudo gives you system priviledges, but requires your authentication. Naturally, once this password is attained, someone smart and devious enough could do whatever they pleased. The other advantage with using ubuntu security-wise, and is often stated, that there are always just tons of eyes always watching the code, and ubuntu developers are constantly making security updates which you get with gnome-update-manager or a sudo apt-get upgrade. Less holes to watch, more eyes watching them, and dramatically less parasites to burrow into them.

Of course I have always doubts and suspicions. Anybody with enough ingenouity time effort and motive could gain access to your computer, eventually. With windows, it is much less complicated to attack many more computers.

---

### Post by darkbullet87 on 2006-02-19
[QUOTE=ubuntu27]darkbullet87: Did you created a new thread for "Encryption"?

Anyway, guys, what do you think of TrueCrypt: [http://www.truecrypt.org/](http://www.truecrypt.org/)

Is it good? What's your opinion?[/QUOTE]

Nope...Did not create a new thread for encryption. I figured unless somebody had a problem with this one going from spyware to encryption I'd just leave it as is.

---

