---
title: "Questions about Root account"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by cobrn1 on 2007-06-14
I have a few questions about the root account in ubuntu:

1) Does the root account actually exist. Let me clarify: what does the 'password is locked' mean? Does it mean that it is a valid account with a password that was chosen by the computer, but you don't know it; or does it have different connotations?

2) The RootSudo article ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)) talked about hackers knowing there is a root account. This coincides with point one above - is it actually hackable (it has a password that you don't know, but could be brute-forced/guessed) or is it actually immune to being hacked - basically, is it essentially hackable like all other accounts except for it's greater permissions over the pc (making it a better target) and you know the login name (root always exists, but you'd have to guess other users logins)?

3) Are there any ill effects from enabling root login and then disabling it - does the root login revert to the 'locked' state that it was in originally, or does this change the state that it was in / the setup in ubuntu. Also, is the password 'forgotten' when you disable root, so next time you decide to unlock root you don't need to remember the password you used last time?

4) Are there any problems with enabling a root account and not actually using it - I ask because I'm concerned about the ability to loging into recovery mode - as ubuntu is patched to be happy with no root password in recovery mode, instant root access - at least in my windows XP installation when I enter recovery mode I'm asked for an admin password (that was set at installation).

5) I'm aware that even with a root password, BIOS, etc you can only slow down people with physical access to the pc. If I was to encrypt the harddrive / partitions, would this fix the problem, ie, you could enter a root account, but then be faced with a prompt for the decryption code? Lastly, if you did have a root password, you'd be asked for that, and _then_ the decryption code, yes? Or would you be asked the passwords in the other way round. Main point - encryption is the ultimate ploy that actually works?


I hope I've been clear with the questions - sorry there's quite a few but I'm really interested in this. Many thanks in advance for your help.

PS: Before I get flamed or have upset sudo lovers banging on my door, I actually quite like sudo and don't intend to unlock the root account (esp if encryption makes it unnecessary). Admitedly, sudo was a bit of a culture shock coming from windows (and DOS beforehand) but I got used to it and it actually makes sense. The real shock was permissions :-( Still, I'm relatively happy with them too now.

PPS: About the recovery mode login - I'm aware that you could count physical access as a system already compromised - please put that thinking to one side for just a moment...


Anyways, back to the questions ^

---

### Post by ruy_lopez on 2007-06-14
Root is disabled to stop users using it as their default login. There's not many situations which require root enabled. Sudo handles 90%  of situations requiring elevated permissions. The remaining 10% of the time, you can use single-user at the boot prompt.

As I understand it, if you enable root, then disable it, it won't be usable. But this doesn't matter. If you are concerned about security, other steps are required.

If someone has access to your machine, to the extent that they can perform a brute-force attack on your password, it doesn't matter if you have root enable or not, you have problems.

The best way to secure your system is to choose a good password, limit physical access to the machine itself, and disable any unnecessary running services. Keep the software up to date by regularly running the update manager.

Seriously, I wouldn't worry about brute force attacks on your password. Basically, people need access to the system to perform these attacks. Preventing access to your system on all fronts is the best way of preventing security lapses.

There no way anyone can remotely access your password without some kind of remote login server running. You can routinely check which services are running by typing "netstat -at"

---

### Post by cobrn1 on 2007-06-14
Actually, I'm not terribly worried about security, there will always be ways and means, but I was more interested from a curiosity point of view (if that makes sense!?).

Does root count and _could_ it be hacked, or is it intrinsically different.

Enabling and disabling root may cause problems - I remember reading a warning somwhere on another forum but have forgotten what they said... does anybody know what they are or if that was a load of rubbish?

And also the recovery mode thing is slightly disconcerting - maybe be I have prying room-mates/siblings/insert-favourite-pest-here, etc? Like I sadi, atleast XP needs a disc and a admin password - both can be circumvented but as they say, security is a process, not a product...

---

### Post by dreadlord_chris on 2007-06-14
> **cobrn1 said:**
> Actually, I'm not terribly worried about security, there will always be ways and means, but I was more interested from a curiosity point of view (if that makes sense!?).

Does root count and _could_ it be hacked, or is it intrinsically different.

Enabling and disabling root may cause problems - I remember reading a warning somwhere on another forum but have forgotten what they said... does anybody know what they are or if that was a load of rubbish?

And also the recovery mode thing is slightly disconcerting - maybe be I have prying room-mates/siblings/insert-favourite-pest-here, etc? Like I sadi, atleast XP needs a disc and a admin password - both can be circumvented but as they say, security is a process, not a product...

Just a couple comments here. 

In XP if you have the Recovery Console installed, anyone who has physical access to your box can boot into it (RC) - no password required. Same as Recovery Mode in Ubuntu.

In Ubuntu, when they say that the root is disabled - what is really meant is that the account is *locked*
An account is locked by changing the password to a value which matches no possible encrypted value. This effectivly prevents **anybody** from being able to log into root - since there would be no possible way they could enter the password. Since there are still times when root access is necessary - the Ubuntu kernel has been modified to allow root local login only in *single-user mode*.

If you are worried about unauthorized access to Recovery Mode, you can remove the option from your GRUB menu.

---

### Post by cobrn1 on 2007-06-14
On XP when I go into recovery mode I am prompted for a admin password. This however, is by-the-by.

Once you have enabled the root account, how do you lock it again so that it is *locked* , ie, unencyptable password, essentially as it was before unlocked.

How would one disable the recovery option option in GRUB (guessing put hashes infront of that stanza in the boot file)?

If I then find I've buggered the system up and actually need the recovery option/ single-user mode, how would I get into it (seing as it's disabled) - (again, guessing, use a live CD, boot up, mount partition and then edit the boot file. Incidentally, if the partition is encrypted is this now impossible, or will you be asked to put the decryption password when you try to mount it {as opposed to getting an ugly error message})?

PS: thanks for the swift replies - I really appreciate it guys =)

EDIT: by boot file I mean menu.lst

EDIT2: by hashes I mean comment out the stanza with # infront of each of its lines

---

### Post by dreadlord_chris on 2007-06-14
> **cobrn1 said:**
> On XP when I go into recovery mode I am prompted for a admin password. This however, is by-the-by.

Once you have enabled the root account, how do you lock it again so that it is *locked* , ie, unencyptable password, essentially as it was before unlocked.

How would one disable the recovery option option in GRUB (guessing put hashes infront of that stanza in the boot file)?

If I then find I've buggered the system up and actually need the recovery option/ single-user mode, how would I get into it (seing as it's disabled) - (again, guessing, use a live CD, boot up, mount partition and then edit the boot file. Incidentally, if the partition is encrypted is this now impossible, or will you be asked to put the decryption password when you try to mount it {as opposed to getting an ugly error message})?

PS: thanks for the swift replies - I really appreciate it guys =)

EDIT: by boot file I mean menu.lst

EDIT2: by hashes I mean comment out the stanza with # infront of each of its lines

To disable the root account:
```

sudo passwd --lock root

```

You are correct about how to disable the Recovery Mode option

As for getting into Recovery Mode after you've disabled the option from the GRUB menu: 
hmmm..... it's been so long since I've done this - let me reboot and check the steps....

back in a sec...

Ok, I'm back....
After the GRUB menu comes up press [ESC] then press '**e**' to go into edit mode, move the cursor down to to the kernel line and press '**e**' again to edit that line. What you want to do is add the word **single** to the line. If the word **splash** is there just replace it with **single** - hit [ENTER] then '**b**' to boot. This change will only be temporary for this boot - no need to change anything back.

---

### Post by cobrn1 on 2007-06-15
Thanks - I think I understand what you mean ;-)

Remove all the comments/# i had put before the lines and have single:

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro **single**
initrd        /boot/initrd.img-2.6.20-15-generic

Correct?

Also, (1) if you had enabled the root account again (by giving it a proper password) would you now be prompted to type that in, or does the patch in ubuntu mean that regardless of root account's status, you are not asked for a password for recovery mode/single user mode.

(2) Is it possible to password protect GRUB so that you can't edit it like this - I seem to remeber reading that GRUB only allows you the password protect booting and editing as one thing, where as LILO you can specify a password for each or mix n match as you see fit.

(3)If you had encryped the hard drive would you be asked for the decryption password when logging into single-user mode - i guess you must be otherwise you couldn't mount the partition - but that's just my guess - could you confirm?

(4) Finally, if you were to get around BIOS password and use a live CD, when attempting to mount the harddrive would you then be asked for the password to decrypt it (again, I'd guess so otherwise you can't read anything). If so then encryption is the best way to go as you'll always be asked for the password for it, and should you bugger up GRUB, etc, you can use a live CD and mount the partition, giving the password then. Am I right in this thinking or have I overlooked something major?

Thanks again for your help :-)

---

### Post by Tomosaur on 2007-06-15
Root account is disabled by default - meaning that it exists but its not usable (except in recovery mode). This means that an attacker is aware of your root account, but couldn't use it even if he/she had the root password. Thus, an attacker has to guess both a user-name which has administrator priveleges, AND that user's password (which is far more difficult than just trying to work out the root password).

Your concerns about recovery mode are justified, but I think it's just a compromise for the sake of user-friendliness. The developers are probably of the opinion that a machine which is physically available to a malicious user is effectively compromised already, thus precautions with recovery mode are fairly pointless. However, there's nothing stopping you from taking extra precautions, if you so desire. You could try the following:

1) Remove the recovery mode option from the boot up list, then put a password on Grub to stop malicious users fiddling with the boot-loader to re-enable it. This is probably the 'best' idea, because it gives at least some protection against a malicious user with physical access to the machine, but it does throw up another inconvenience to you if you ever want to use recovery mode, because you will need to manually add the recovery mode option back into grub from the grub command line.

2) Enable the root account and set up your system to require the root password when you use recovery mode.


Easiest, method? Put a lock on the door of the computer room and lock it when you're not on the machine :P

---

### Post by antoz on 2007-06-15
Woudn't anyone with a rescue disk like Knoppix be able to boot up, mount the partitions and access everything on the computer?

---

### Post by eentonig on 2007-06-15
If someone has physical access to a machine, security is ALWAYS compromised. That's also the reason why most  linux distributions have no root password requirement for the recovery console. It is only available if you got hands-on to the box. And if you got hands-on, the box is insecure. Period.

---

### Post by anaconda on 2007-06-15
> **antoz said:**
> Woudn't anyone with a rescue disk like Knoppix be able to boot up, mount the partitions and access everything on the computer?

Yes they would, unles the filesystem is encrypted..

And  if you give root a password (eg. enable root account) then when you boot to recovery mode you will be asked the root password!.

So one way to protect your maxhine is to give root a password, and set a password for BIOS too and disable booting from CD:s and USB:s from BIOS

And giving root a password doesn't really matter. you can still do all your maintaining with sudo.. Just make the password difficult enough so that brute force attacks wont succeed..

---

### Post by cobrn1 on 2007-06-15
> **Tomosaur said:**
> 
2) Enable the root account and set up your system to require the root password when you use recovery mode.

So enabling the root account would then make ubuntu ask for a root password when going inot recovery mode? Or is there another step to amking that occur (i'm not sure as the ubuntu kernel is patched to accept locked root account as default.

> **eentonig said:**
> If someone has physical access to a machine, security is ALWAYS compromised ... if you got hands-on, the box is insecure. Period.

While I can see this point of view - i even mentioned it in my first post - disallowing access to the box is sometimes not an option, ie, roommates, siblings etc could have access to it which couldn't be helped (lock the door is not a valid option here so please don't say that :rolleyes: ) It's not like I'm running a server that I can just lock under the stairs (in which case, btw, I would start to share your view point more whole-heartedly.

> **anaconda said:**
> Yes they would, unles the filesystem is encrypted...

And giving root a password doesn't really matter. you can still do all your maintaining with sudo.. Just make the password difficult enough so that brute force attacks wont succeed..

This is one of the points I was also trying to raise, while enabling the root account does have a disadvantage that it is not open to brute force when it wasn't before, if you use a good enough password this shouldn't matter. Not using sudo isn't the problem here - it's fine - security is the problem.

However, if you encrypt the hard disc this solves all problems - recovery still askes for decryption password, and if you use a live CD (after circumventing and BIOS passwords) you are assked for the password when trying to mount the harddrive (otherwise it is useless).

---

### Post by bodhi.zazen on 2007-06-15
Security is always an interesting topic.

encrypting your filesystem is the way to go.

If you are interested I found this book to be outstanding (it was at the local library) :

[http://www.amazon.com/Hardening-Linux-James-Turnbull/dp/1590594444](http://www.amazon.com/Hardening-Linux-James-Turnbull/dp/1590594444)

---

### Post by cobrn1 on 2007-06-15
ooh - looks very interesting. Thanks for the recommendation - I'll see if they have it in any of my local libraries...

And to sum-up, encryption is the best idea (and not to go buggering about with the root account). Cool, but the hard disk will be mountable from a live CD as long as you can still remember the decryption password, right? Otherwise if anything goes wrong one could be in for a world of pain...

---

### Post by bodhi.zazen on 2007-06-15
> **cobrn1 said:**
> ooh - looks very interesting. Thanks for the recommendation - I'll see if they have it in any of my local libraries...

And to sum-up, encryption is the best idea (and not to go buggering about with the root account). Cool, but the hard disk will be mountable from a live CD as long as you can still remember the decryption password, right? Otherwise if anything goes wrong one could be in for a world of pain...

LOL ~ Security is a balance between pain and pleasure.

---

### Post by cobrn1 on 2007-06-15
> **bodhi.zazen said:**
> Security is a balance between pain and pleasure.

lol - so true... But getting back (to my last question), if you loaded up a live CD you would be able to mount the partition as long as you remembered what the decryption password is, right?

Please confirm this and then I can sleep better...:D

---

### Post by cobrn1 on 2007-06-15
Actually, i have two questions left:

(1) if you loaded up a live CD, you would be able to mount an encrypted harddrive/partition as long as you remembered what the decryption password is;

(2) will you be asked for a root password when entering single-user mode / recovery mode from the GRUB menu if you have enabled a root password, OR, does it still not ask for a password. (NOTE: If not then is not asking for a password unique to ubuntu, or is it a universal feature of the linux kernel).

Thanks.

---

### Post by cobrn1 on 2007-06-15
Did a bit more research - from what I've been able to gather, it's only when sulogin detects a locked, no-passworded root acount will it let you it without password. If you enable root (and set a password) and then disable it again, this isn't counted as the same and can lock you out of the recovery mode (unless you remember the password you used when root was enlocked). This can be fixed by manualling editing the file involved, but i'm not sure if this does buggerup sulogin anymore (may have been fixed).

so, only question (1) remaining (if you loaded up a live CD, you would be able to mount an encrypted harddrive/partition as long as you remembered what the decryption password is) - I'm relatively sure that you would still be able to mount it, but I'd really appreciate some confirmation on this.

Thanks to everyone else for helping to nswer my q's.

---

