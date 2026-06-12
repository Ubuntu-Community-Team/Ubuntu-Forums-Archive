---
title: "how do i secure my ubuntu box ?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by imT on 2008-01-28
my concern are my personal files from /home basicly and not even, i have a bios pass and an account pass but the home files are still accessible. ex.: i dual boot ubuntu with xp, and in xp i mounted my ext3 partitions and i can easily access my files from /home even i set my permissions only 2 me. not to mention when i installed freespire i was able to access my files as easy as i did from xp.
what should i do ? i wanna be the only person that has access to my set of files, not even the root :)
any suggestions ?

---

### Post by LaRoza on 2008-01-28
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

Perhaps you can look into less than full system encryption.

---

### Post by (((X))) on 2008-01-28
root more or less has access to everything on your system

---

### Post by imT on 2008-01-29
> **LaRoza said:**
> [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

Perhaps you can look into less than full system encryption.

i'll give that a look....

---

### Post by Seisen on 2008-01-29
> **(((X))) said:**
> root more or less has access to everything on your system

By default in Ubuntu the root account is disabled hence why we tell you guys to run commands with sudo if you need super user privileges.

---

### Post by amo-ej1 on 2008-01-29
You can only do this by relying on encryption of the data itself.

---

### Post by imT on 2008-01-29
> **amo-ej1 said:**
> You can only do this by relying on encryption of the data itself.

:confused: what that suppose to mean ????

---

### Post by p_quarles on 2008-01-29
> **imT said:**
> :confused: what that suppose to mean ????
It means that the only way to secure data against any possible intruder is to encrypt it. Any other method of securing it is vulnerable to, if nothing else, anyone with physical access to the computer.

---

### Post by asmiller-ke6seh on 2008-01-29
> **imT said:**
> :confused: what that suppose to mean ????

iT MEANS: *Perhaps you can look into less than full system encryption.*

---

### Post by amo-ej1 on 2008-01-29
Check this fresh thread for example: [http://ubuntuforums.org/showthread.php?t=680292&highlight=gnupg](http://ubuntuforums.org/showthread.php?t=680292&highlight=gnupg) it illustrates you how to encrypt/decrypt files using gnupg.

_do keep in mind_ that if you loose the key, you data will be lost !

---

### Post by Luggy on 2008-01-29
> **Seisen said:**
> By default in Ubuntu the root account is disabled hence why we tell you guys to run commands with sudo if you need super user privileges.

Yes but Windows lets you play in root all you want, hence you can access anything in Linux when running Windows.

---

### Post by Seisen on 2008-01-29
There is this guide too, [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Seisen on 2008-01-29
> **Luggy said:**
> Yes but Windows lets you play in root all you want, hence you can access anything in Linux when running Windows.

Provide with a link on how to do this so I can test, I have never heard of that before.

---

### Post by amo-ej1 on 2008-01-29
and vice versa offcourse. (unless you're using some encryption features of ntfs).

but nothing forbids you to take out a disk and put it in another computer and mount it these. Or boot it into single user mode from grub etc etc 

As previously said, everyone with physical access to the machine can do anything he/she wants.

---

### Post by chewearn on 2008-01-29
You can encrypt an entire partition using truecrypt, but only if you are truly paranoid: 
[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by Seisen on 2008-01-29
The problem with truecrypt is that you have to do a fresh install for it to work otherwise it will completely overwrites the data that is on that particular partition. Gnupg is probably the OP's best bet.

---

### Post by imT on 2008-01-29
i don't wanna encrypt files, i know that  is the best way ....
i was looking for something for a partition, not exactly encryption but to "remove" the access from windows or from other distro to "a bunch" of files that i, as owner of them i would have full and easy access with out some time wasted in decryption....something similar with permissions within ubuntu....??
i'll give a try to those anyway ...
thanks :)

---

### Post by (((X))) on 2008-01-29
> **Seisen said:**
> Provide with a link on how to do this so I can test, I have never heard of that before.

[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by steveneddy on 2008-01-29
Turn off the PC, unplug it from the internet and hide it in the closet.

---

### Post by lespaul_rentals on 2008-01-29
> **imT said:**
> i don't wanna encrypt files, i know that  is the best way ....
i was looking for something for a partition, not exactly encryption but to "remove" the access from windows or from other distro to "a bunch" of files that i, as owner of them i would have full and easy access with out some time wasted in decryption....something similar with permissions within ubuntu....??
i'll give a try to those anyway ...
thanks :)

That's pretty much impossible without encryption; if you have physical access to a computer you will be able to access the files.  It doesn't matter how much you chmod, chown, password protect...it's always crackable.  The only way you can really guarantee an intruder will not (easily) get access to your files is through encryption, as has already been stated.  If your encryption is strong enough, it will take weeks to crack the encryption.  That's the only way to be safe.

---

### Post by (((X))) on 2008-01-29
Don´t give administrative rights to users on you computer, best way imho.
I will never encrypt again, if something goes wrong..last  time I did that, I lost all my work :(

---

### Post by imT on 2008-01-29
............you all get me wrong.
i don't want advanced security...i want just a little "wall" between my ubuntu account and my windows partition, or other distro.
as Luggy said earlyer, linux is too easily accessible from windows cuz when you log in windows the permissions don't mean squat.... the same thing with other distro's installed.
i was asking about that kind of stuff if there is... i knew about encryptioning before but from my experience that seems to much time wasteing.

> **(((X))) said:**
> Don´t give administrative rights to users on you computer, best way imho.
I will never encrypt again, if something goes wrong..last  time I did that, I lost all my work :(
yeah, but from windows my /home permissions don't mean anything, i can access files as easy as being on my desktop...that was my start point for may concern, and this happend  to me in freespire :( the /home password seems to be aplying only on the installation that is mounted ...........

---

### Post by (((X))) on 2008-01-29
When a system has shadow passwords enabled, the password field in /etc/passwd is replaced by an "x" and the user's real encrypted password is stored in /etc/shadow. Because /etc/shadow is only readable by the root user, 
malicious users cannot crack their fellow users' passwords. Each entry in /etc/shadow contains the user's login, their encrypted password, 
and a number of fields relating to password expiration. A typical entry looks like this:     pete:/3GJllg1o4152:11009:0:99999:7:::
[http://tldp.org/HOWTO/User-Authentication-HOWTO/x71.html](http://tldp.org/HOWTO/User-Authentication-HOWTO/x71.html)

so, I wonder, is etc/shadow readable from Windows partition?
If it is, Windows user is able to crack it with md5 utilities and login as root.

---

### Post by The Cog on 2008-01-29
Maybe you should look at encfs, which allows you to keep just one encrypted directory:
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by imT on 2008-01-29
> **The Cog said:**
> Maybe you should look at encfs, which allows you to keep just one encrypted directory:
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)
:)    thanks, it dose the trick....:KS

---

### Post by Seisen on 2008-01-29
> **(((X))) said:**
> [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Ok that is all fine and dandy but you still need physical access to install those programs, they are not installed in Windows by default.

---

### Post by chewearn on 2008-01-30
> **Seisen said:**
> The problem with truecrypt is that you have to do a fresh install for it to work otherwise it will completely overwrites the data that is on that particular partition. Gnupg is probably the OP's best bet.

That is untrue.  You don't need fresh install for it to work at all.  It is moderately easy to create a new partition and format it as a truecrypt container.  Else, it is also easy to create file-based container, if repartitioning is not an option.

---

