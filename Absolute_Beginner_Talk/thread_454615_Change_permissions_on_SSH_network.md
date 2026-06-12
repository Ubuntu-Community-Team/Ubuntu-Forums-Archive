---
title: "Change permissions on SSH network"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-05-25
I have a basic and functional SSH network setup.  With a password and username, others on my LAN can connect to my computer, and the whole computer.  This is nice, but I want to know if there is any way to change what permissions people have to my files/folders when connected through the network without changing the "real" permissions (because I need access to my own computer of course ;))

Not to be rude, but I've looked into ftp, and formed my opinion, and if anyone has any advice on how to do this over ftp, I don't really care (unless you can make it real simple, and also tell me how to disable my current SSH network).

Any help (on ssh :p) appreciated!

---

### Post by Ek0nomik on 2007-05-25
You could create individual accounts.  For an example, create a Network account, than go into certain folders and allow only the "Network" username to use those files.

They would login like this:

```
ssh network@myip
```

---

### Post by ryanVickers on 2007-05-25
Interesting, I might do that, but wouldn't they still be able to access everything if they used my username and password (i'm not paranoid about the security, I just have a special need for this)

---

### Post by kevdog on 2007-05-25
Im not sure how many people have to access your computer, however I though ssh was meant to be set up so that everyone accessing the computer had their own account (or a shared account separate than yours).  

As far as permissions, again you could have one "common" ssh account and structure permissions for this user accordingly, or if each user has their own account, you could structure permissions individually.

If you are really paranoid about the users accessing any other part of the OS other then a select group of folders, you could setup an ssh jail.  Sorry I dont have a link, however there are various tutorials available.

---

### Post by ryanVickers on 2007-05-25
ooo, that sounds promising - I'll look into it

Yeah, I suppose your thinking for what I'm doing (sharing some folders with read-only) I should just use smb or something, but I want to be able to do this over the internet (with computers not on the LAN).
I've already got that method ready, I just need to setup permissions first.

---

### Post by Ek0nomik on 2007-05-25
> **ryanVickers said:**
> ooo, that sounds promising - I'll look into it

Yeah, I suppose your thinking for what I'm doing (sharing some folders with read-only) I should just use smb or something, but I want to be able to do this over the internet (with computers not on the LAN).
I've already got that method ready, I just need to setup permissions first.

Meh, I have my friends downloading from me using SSH (or WinSCP if they use Windows) if they want to get my *legal* content.  ;)

Basically you want to ask yourself:  What are these people doing on my computer?

Are they only downloading files?  If so, than just setup a group account.

Are they each sending you files and you **need** to know who sent you what?  Then you could setup individual account so they have unique passwords and they each get their own folder.

It just depends on what you want to do.  :)

---

### Post by ryanVickers on 2007-05-25
But wouldn't they, if they used my username and password, still be able to access everything, even though their accounts have only the desired permissions?!

---

### Post by ryanVickers on 2007-05-25
Ok, hold on to your comments everyone, I'm in the process of completing something useful I found.  I'll post the link later

---

### Post by qpieus on 2007-05-25
> **ryanVickers said:**
> But wouldn't they, if they used my username and password, still be able to access everything, even though their accounts have only the desired permissions?!
Yes, if they use your username and password they can access everything - that's because they are in your account, not theirs. That's the point the other replies here have been trying to make - there is no need to let other people use your username and password. Letting others use your account is not a good idea - they could delete your files, install programs, and cause general havoc!

Is there any reason why you want other people to use YOUR username and password? You don't need to do that. You can create a separate account (or several other accounts) that the other people, who you want to give access to, can use so they don't have to use your account.

You can then use permissions to give these other users access to whatever you want them to have access to on your pc, and deny access to stuff you don't want them messing with. Additionally, the other users would not have sudo privileges, which is the way you want it. You don't want other people being able to use your pc with superuser powers.

---

### Post by Dr Small on 2007-05-25
You could chmod your entire / so when people login at their ssh account, when they cd up to /, they get a forbidden erorr.

If you want to briefly connect to my sshd, pm me, and I'll send you some details.
You can then look around from there.

Dr Small

---

### Post by ryanVickers on 2007-05-25
Ok, yes, I get that, but...  It's complicated.

I'll just deny access to anyone trying to connect with that (my) usernamy I guess, and finish up my thing I'm doing now.  I think it will work pretty well.

---

### Post by Dr Small on 2007-05-25
Well, unless another user knows your username / password, it will deny them anyway.
I would just chmod your / directory, and some other sensitive places, and since most system directories are owned by root anyhow, it would be hard for a person to do much damage, unless they guessed sudo's password. ;)

Dr Small

---

### Post by ryanVickers on 2007-05-25
Yeah, I'll just lock up important things and change the root password.  That covers the problem of denying access completely to unauthorized users, but I'd still like to make everything else read-only to anyone remoteing in.

---

### Post by ryanVickers on 2007-05-26
Well, that went beautifully!  After a complete format and re-install, I'm ready to keep trying! :p
(don't worry, I didn't lose anything)

---

### Post by Ek0nomik on 2007-05-26
What problem are you currently having ryan?

---

### Post by eentonig on 2007-05-26
> **Dr Small said:**
> ...unless they guessed sudo's password. ;)

Dr Small

It's nit that hard to guess sudo password. It's your own (or better, their own). But they would have to be added to the sudo-users before they could use it.

That's one of the points of sudo security. You don't need to have one root password shared between several people (one person can keep a secret, as soon as two people know it. Word gets out) as everybody can have it's own (if entitled to)

---

### Post by qpieus on 2007-05-26
> **ryanVickers said:**
> Well, that went beautifully!  After a complete format and re-install, I'm ready to keep trying! :p
(don't worry, I didn't lose anything)

Yikes, what happened?

---

### Post by ryanVickers on 2007-05-26
Apperently, when the folder in question is "/", full read/write from anyone actually means no access, even from system apps. :p

---

### Post by ryanVickers on 2007-05-26
Ok, maybe is there a way to setup samba so that it can be accessed from anywhere (a computer cnnected to the internet, but not on the LAN) because that would work too.

---

### Post by seetho on 2007-05-26
Hi ryan,

I think what everyone here is trying to tell you is that you do not (and should not) give your login name and password to anyone else.  If you want other users to have access to your PC just go to System->Administration->Users and Groups and create some new users with their individual passwords.

Now they can individually access their home directories but they will never be able to touch your stuf of even each others stuff (unless you geive them your password).

If you want them to have access to a common directory just put all these users in a Group and then assign the correct permission for this group to the directory you want them to access.

It's that simple.... unless you have something else in mind?

---

### Post by hyper_ch on 2007-05-26
if the others are using WinSCP or something similiar and not true SSH then you could limit them to a common directory by editing /etc/passwd and set scponly.

---

### Post by ryanVickers on 2007-05-26
Ok, so how it's set up, is:
-me, read everywhere, write to home
-netusr (I called it), read everywhere (except my files - them: no access(well, a few, the ones I wanted(readonly though))) and write to home

I think that's good!  Now I just need to set up a port to forward to my ip, right?  I don't know if I'm saying this right, read [this]("http://ubuntuforums.org/showthread.php?t=448529").

---

### Post by seetho on 2007-05-26
> **ryanVickers said:**
> 
-me, read everywhere, write to home
-netusr (I called it), read everywhere (except my files - them: no access) and write to home


You (locally or remote) can read and write to your home (and elsewhere with sudo).
Other users (using their own login account) can read and write to their respective homes only - nowhere else; unless you assign them permission to do otherwise.

---

### Post by ryanVickers on 2007-05-26
But they don't know the sudo, just me, and I'd only use it if absolutely necessary, and the netusr I made can write to his home, but only read everywhere else (and some of my files gives it no access)

---

### Post by seetho on 2007-05-26
sudo will only work with your password, unless you assign them the right to run sudo (which is a bad idea).

---

### Post by ryanVickers on 2007-05-26
Ok, thats good.  My origonal point was though that:
-they have read/write to only thier home, and view to everywhere except a select few folders, the way I wanted it
-But using sudo or just me, I can read everywhere and write to my and thier home.
-Only I have sudo.

---

### Post by seetho on 2007-05-26
That would be correct.  Set up a few dummy accounts and experiment.  There are also lots of docs on the net that you can read about setting up users, groups, permissions, etc.  Any Linux distro doc would have the same info.  Same goes for BSD and other Unix flavours.

Good luck.

---

### Post by ryanVickers on 2007-05-26
I would say for now that this is done, and thanks to everyone who stuck with this through all that!  I might be back here soon though to discuss how to make it globaly available (to people off the LAN (but with an internet connection, obviously :)))

---

### Post by ryanVickers on 2007-05-26
One last question, I've noticed that (remotely signed on as netusr) I can open text files by right-clicking and choosing gedit from the list in the dialog, but just double-clicking the files normally doesn't work.  Something about netusr not being allowed to run this program.  I suppose that makes sense, but how would I give these permissions?

---

### Post by seetho on 2007-05-27
I'm not very sure as I use the cli when logging in via ssh.  In any case I guess that by chance you have double-clicked on as executable file and your Nautilus preference has been set to run the executable text file instead of opening it.  Since netusr does not have executable permission, Nautilus will give you and error message.

Like I say I not so sure about this.  If you find out, just put a post here so others will know.

---

### Post by ryanVickers on 2007-05-27
No, I checked, that's not the problem.  I don't know, it's not a big deal, just interesting.

---

### Post by ryanVickers on 2007-05-27
Ok, one more problem.  When a computer on the LAN using Kubuntu is trying to connect to my computer, it doesn't work.  It says that it's unable to connect.  On that computer, they are loged on as some user not on this computer, but that shouldn't matter if they use the username and password setup here, right?  What's wrong?  It doesn't even get to the point of network logon, just says "can't connect to *my computer name*".  Do I have to allow that coputer or something?

---

### Post by seetho on 2007-05-27
Have you read this?: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

There's a section with instructions on how to connect using Konqueror under KDE.

---

### Post by ryanVickers on 2007-05-27
Yes, that's exactly what I did from the remote computer after setting up the connection.

---

