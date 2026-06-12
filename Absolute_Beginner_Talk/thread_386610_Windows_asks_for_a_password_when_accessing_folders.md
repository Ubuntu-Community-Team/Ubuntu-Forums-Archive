---
title: "Windows asks for a password when accessing folders shared from Ubuntu"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by garton on 2007-03-17
I've enabled samba file sharing from my Ubuntu box, and shared a folder with it. Then I walk over to my Windows computer and try to see what folders are shared from Ubuntu, I'm asked for a username and a password??

I've tried with my regular Ubuntu user/pass, but that doesn't work. What's the problem here?

---

### Post by shingalated on 2007-03-17
To add a samba user use the command:
sudo smbpasswd -a

---

### Post by garton on 2007-03-17
> **shingalated said:**
> To add a samba user use the command:
sudo smbpasswd -a

I left Gentoo for Ubuntu so that I wouldn't *have* to do things like this... 

Ok, I guess I'll have to do it the difficult way. *sigh* This really sucks. Ubuntu should have seamless file sharing with Windows out-of-the-box, in my opinion! This is a shame for an otherwise very nice distro!

---

### Post by Zzl1xndd on 2007-03-17
That would be awesome but this is a samba issue not an Ubuntu one, and thats just the way samba works. Although I agree with you its not really Ubuntu that is the cause of this problem.

---

### Post by garton on 2007-03-17
> **tweakedenigma said:**
> That would be awesome but this is a samba issue not an Ubuntu one, and thats just the way samba works. Although I agree with you its not really Ubuntu that is the cause of this problem.

Oooooh no!!!!

It is VERY possible to pre-configure samba in such a way so that it allows for out-of-the-box seamless Windows file sharing. And it IS an Ubuntu issue!

For really, how can it not be? Should Ubuntu shrug its shoulders over every weird thing that happens in it and point to the original supplier of the software and say: "It's their fault! Not our issue!"?

I think not.

---

### Post by Zzl1xndd on 2007-03-17
> **garton said:**
> Oooooh no!!!!

It is VERY possible to pre-configure samba in such a way so that it allows for out-of-the-box seamless Windows file sharing. And it IS an Ubuntu issue!

For really, how can it not be? Should Ubuntu shrug its shoulders over every weird thing that happens in it and point to the original supplier of the software and say: "It's their fault! Not our issue!"?

I think not.

No doubt it could be but I guess ill rephrase I am rather happy with the way it works and hope they don't change it. Also it is normally the way Samba comes pre-config on most systems somewhat of a standard if you will. I mean they could also pre-configure it to do a lot of things that end users would find easier but its not always best to do that.

---

### Post by garton on 2007-03-17
> **tweakedenigma said:**
> No doubt it could be but I guess ill rephrase I am rather happy with the way it works and hope they don't change it. Also it is normally the way Samba comes pre-config on most systems somewhat of a standard if you will. I mean they could also pre-configure it to do a lot of things that end users would find easier but its not always best to do that.

It is not always best to do what users find easier, granted, but in this case it absolutely is. 

It doesn't matter if the original samba software comes pre-configured in this or that way, bad default configs are meant to be improved by the distro maintainers, in this case Ubuntu.

---

### Post by thelinuxguy on 2007-03-17
> **garton said:**
> I've enabled samba file sharing from my Ubuntu box, and shared a folder with it. Then I walk over to my Windows computer and try to see what folders are shared from Ubuntu, I'm asked for a username and a password??

I've tried with my regular Ubuntu user/pass, but that doesn't work. What's the problem here?

You have to add samba users to the system. But its not necessary to do that on the terminal. Install GSambaD from the repos. Its a GUI app meant for such tasks. Using it you can set up your Ubuntu system users as Samba users, share folders and printers and quite a lot of other things. Give it a try.

---

### Post by Zzl1xndd on 2007-03-17
> **garton said:**
> It is not always best to do what users find easier, granted, but in this case it absolutely is. 

It doesn't matter if the original samba software comes pre-configured in this or that way, bad default configs are meant to be improved by the distro maintainers, in this case Ubuntu.

I'm gonna disagree on this cause it doesn't suit my needs I prefer having the password but I have people travel in and out of my network a lot, Granted that it would more likely be better for many other users if I was the one that needed to configure it to work the way I wanted.

---

### Post by islander_810 on 2007-03-17
I guess this should ans all ques

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add.2Fedit.2Fdelete_network_users)

---

### Post by guyraz on 2007-05-14
I've tried both ways using the terminal I've added the command, and still it won't accept the password
using the gsambad I got the massage Failed to execute child process "su-to-root" (No such file or directory) (child is the name of computer I guess)
any help?? please.

---

### Post by stealhrt on 2007-05-14
I'm in the same boat with the same error message too .. Sigh I feel so stupid with all these Linux errors every time I try to do something I can do in my sleep in XP :/
:mad:

---

### Post by Dr Small on 2007-05-14
Make sure firestarter isn't blocking the network IP's of which you are trying to access your ubuntu system with.

Dr Small

---

### Post by Nythain on 2007-05-14
so if you dont want them to have to have a user and password at all, why dont you change security from user to share... in fact you can do it in a nice gui way inside Kubuntu (i think its a kde thing)... it defaults to user for security reasons, and doesnt just go creating random accounts pre-configured for security reasons too...
Though ubuntu is a great desktop linux distro, its still a linux distro, and that means security out of the box... both on samba's part and ubuntu's part.
its really not difficult to create a user in ubuntu, and make them a member of whatever effen group they need to be... and its even easier to open one file and change a few words (mainly security = user to security = share)
I will admit that things could be much easier for you but you did not create ubuntu, and you are not the thousands if not millions running ubuntu, you are one user, with one users needs wich are easily enough obtained that the creators of samba and ubuntu feel they should have to jeopardize thier secure and working default configs for
Sorry but thats just how it is

---

### Post by thelinuxguy on 2007-05-15
> **guyraz said:**
> I've tried both ways using the terminal I've added the command, and still it won't accept the password
using the gsambad I got the massage Failed to execute child process "su-to-root" (No such file or directory) (child is the name of computer I guess)
any help?? please.

Start gsambad as root: sudo gsambad
In the gsambad window:
1. Server settings >> Workgroup or domain name >> Put the same workgroup as that of your Windows box ( I am not sure if this is required but I have a working system with this setting)
2. Shares >> Import users and groups >> forward >> select the users and import
3. After this the users should be listed in the Users tab. If not, add them manually there.

[B]Select Apply on each tab you have changed.
Click on Activate.[/B]

Your shares should be available now. Let me know if it works.

[COLOR="Red"]Do not delete any users from the Users tab. I had done this thinking only the samba users will be deleted. But it deleted the users from the system altogether. 
I had to spend some time getting things back to normal again.[/COLOR]

---

### Post by thompa on 2007-05-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/32067) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a bug report about Samba and the need to create a GUI friendly iinterface to allow networking and possibly even printing to be configured.

Have a look and lend your support to get this thing moving... Linux and Ubuntu is suffering from and easy and effect network set-up solution!

---

### Post by BLTicklemonster on 2007-05-16
I find it hard to believe that when I choose to share a folder in ubuntu, I don't have an option to click that states that the folder is shared openly and freely without regards to any username and password. Sure, there's a good reason for usernames and passwords, but come on, how many people have home networks and share stuff around the house, and aren't worried about anything because they use a router with a hardware firewall in it? 

*bip bip bip* hello? 

Come on, whomever, get with the program already. It should be standard, and it should be staring you in your face when you share a folder: do you want this to be private? y/n if yes, then you can enter users and password. If no, then the danged thing should be able to be opened by anyone who wants to open it. I can't share any stuff from my computer because I refuse to mess with editing danged files just to have a convenience that the meglomaniacs at Redwood give me automatically when I use their product.

---

### Post by [h2o] on 2007-05-16
Changing 
security = user
to
security = share
in /etc/samba/smb.conf made sharing work for me. I have no clue whether this is good for security or not, but I don't really care since my network is closed.

---

### Post by BLTicklemonster on 2007-05-16
Thanks Water dude!!! I'll try that at the house tonight.

---

### Post by BLTicklemonster on 2007-05-20
Shoot, I can't share any folders now. lol

---

### Post by II_V_I on 2007-05-24
Greetings to all.

I've tried all the steps that I can find outlined on this forum for accessing shared folders and shared volumes on my Ubuntu machine, but I still get asked for a user name and password when trying to access those folders from my Windows machine. 

Perhaps it is because the Windows machine is running Win2K instead of WinXP. I don't know. I have absolutely no trouble whatsoever accessing shared folders on the Win2K machine from the Ubuntu machine. But like so many others here, the simple steps which seem to work for others are not working for me either.

Yeah, yeah, I've changed the security from {user} to {share}, gone to the end of the file and added the lines:

force user = nobody
force group = nobody

and when that didn't work went back and changed them to:

force user = my_username
force group = my_username

And of course, liberal restarts of both machines haven't helped either...

Ain't none of it done no good.

---

### Post by BLTicklemonster on 2007-05-25
Okay, upon restart, I can share a folder as windows network smb.

Big deal, I still can't access it from another computer because access is denied because it's passworded. Yet I was never, at any point, asked to provide a password for any folder I have shared. This may make sense to some people, but it is absolutely retarded beyond reckoning in my book. This is like having a lock installed on a door, yet not being given a key. "Oh, but in order to get the key, you must fart the national anthem in F sharp while standing on your head!!!" 

Now I ask you, why is networking not straight-forward in linux?

How hard could it possibly be to allow me to, upon clicking on a folder and clicking on share folder to decide yes or no if I want it password protected or not? Without having to perform some mysterious task that is not mentioned at the time I share the folder, btw.

AAAARRRGGGG!!!!! I"m surrounded by idiots, and I married their Queen!!!!

:)

I've got pictures of my daughter getting honors at her school this morning that I want to share with the machine upstairs. Were it not for Window's simple networking, and sharing a folder with full access, so that I can just open it here and drop the pictures in the folder, I'd be totally stumped in my effort to get the images shared to that machine.

Simplicity. That is the one thing that is keeping Linux as an oddity stared at with derision.

I have to edit a file to share without a password, right? I did, yet I still can't do that. In that I have to edit a file in the first place just shows how far Linux has to go to be "useful" to me and others like me. Or is there some other secret? 

Rather than rant on and on about this, I'll leave it be for now, but I am totally livid at this lack of fore sight on the part of "the powers that be" in the Linux universe.

---

### Post by lazyart on 2007-05-25
The step I think that is missing here is to enable said user in samba.  Yes, they were added with -a, but need to be enabled:```
sudo smbpasswd -e *username*
```

If the user has been added and enabled, AND if they have permissions to the folder, only then will their password be accepted.  If it is your folder, use your ubuntu name and pass to get in... assuming you have added and enabled yourself using the smbpasswd commands.

Linux is secure.  And secure doesn't always equal convenient. :(

---

