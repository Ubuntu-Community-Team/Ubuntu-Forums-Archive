---
title: "[SOLVED] newbie user account trouble"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2007-07-22
I've been a windows user for many years and I've only just switched to ubuntu feisty. Please help me clarify some stuff about how user accounts work in ubuntu.
Normally, 2 people will use my computer - both need to be able to do administrative stuff, and keep some amount of data to themselves. 
Here are my questions:
1) I think I know the basics of how to set user privileges and stuff (System-->Administration-->Users and Groups and so on). So if there are 2 administrator accounts, each will use her/his own password to do administrative tasks, right?
2) It seems that administrators can see all data on the computer. Is that right? If yes, what can users do to keep some of their data (like pictures and spreadsheets - private stuff) to themselves and share some of it (like music) with other users?
Thanks.
P.S.: Simple solutions please!

---

### Post by Daveth on 2007-07-22
there will be 3 "users" on your pc, you, the other person, and root. Each person will have their own /home/user folder to store letters, pictures, music etc, and they can control the permissions to folders and files as much as they want. Only root is all seeing. I must admit I do not know if you can shut root out of a folder. You can also use groups to control who of the 2 of you can have permissions to admin some things, if you need that degree of separation.

---

### Post by ddrichardson on 2007-07-22
Whoa steady there. Don't think of root users under Linux like Administrator under Windows.

The root user can see and modify everything - but then again so can a Windows Administrator. There is no way for a user to lock out root - by design.

UNIX in general was designed as a multi-user OS long before MS-DOS/Windows started bolting bits on to introduce that functionality.

If you need to do administrative stuff, then please use sudo - or create a group that gives permission to carry out that specific administration task, i.e. installing software.

---

### Post by kleo skywalker on 2007-07-22
To all of you who've done this for a bit (or longer) the following is going to sound stupid, but here it is: what exactly is a root user? I know that when I go to "users and groups" I can  see the accounts I created, and then one called root (but I can't login to that account, right?)
What else do I need to know?

---

### Post by ddrichardson on 2007-07-22
The root user is basically the main system administrator account. All system files are owned by this account hence only the root user can alter them.

Everytime you use sudo you are executing a program as if you were root.

---

### Post by bodhi.zazen on 2007-07-22
To give your second user admin access, via sudo, addhim/her to the admin group.

To configure sudo use visudo. You can restrict the root powers of the second user if he/she does not need full root access.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)

If you need to have privacy you can encrypt your files.

You can use gpg :

To encrypt : gpg <file>

it will ask you for a password and make a new file, file.gpg (it will not delete the original file, you need to do that manually).

To extract the file : gpg file.gpg <enter PW>

You will get an error message, 

you can ignore that.

---

### Post by kleo skywalker on 2007-07-22
Yes I looked it up and get the basics, I think.
So back to my main problem:
How does a user (an administrator) make her/his data inaccessible to other administrators?
What about users of the type "desktop user"? It seems that by default they can do everything but administer the system. So that means they can never even get into a situation that prompts them to give the sudo password, right? And they can access everyone's data too - how can I stop that?!
Another request, whatever you suggest - password protection for folders or whatever works - please give the step-by-step procedure from start to end.
Thanks.

---

### Post by bodhi.zazen on 2007-07-22
> **kleo skywalker said:**
> Yes I looked it up and get the basics, I think.
So back to my main problem:
How does a user (an administrator) make her/his data inaccessible to other administrators?

Start by reading permissions

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

On Linux the administrative account is called root. You can restrict root access to files by either restricting root (sudo) powers (more difficult) or encryption.

I gave you a simple encryption command already.

If you want more see here : [http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

> What about users of the type "desktop user"? It seems that by default they can do everything but administer the system.

Not at all. It only seems so because you do not yet have much experience ...

> So that means they can never even get into a situation that prompts them to give the sudo password, right?

If they attempt to use sudo, gksu, su, su -, gksu, or access admin stuff (add/remove software) they will be prompted for a password. If they do not know the password they will get no further.

> And they can access everyone's data too - how can I stop that?!

See permissions. Linux/Unix has been multi user for much longer then Windows and is much better at it then windows.

> Another request, whatever you suggest - password protection for folders or whatever works - please give the step-by-step procedure from start to end.
Thanks.

Linux does not do this. The closest is permissions and encryption. Permissions is fine if your users do not have root access.

Try google or the (ubuntu) search function. It is unlikely anyone will type such detailed lengthy descriptions.

---

### Post by kleo skywalker on 2007-07-22
> **bodhi.zazen said:**
> To give your second user admin access, via sudo, addhim/her to the admin group.

To configure sudo use visudo. You can restrict the root powers of the second user if he/she does not need full root access.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)

If you need to have privacy you can encrypt your files.

You can use gpg :

To encrypt : gpg <file>

it will ask you for a password and make a new file, file.gpg (it will not delete the original file, you need to do that manually).

To extract the file : gpg file.gpg <enter PW>

You will get an error message, 

you can ignore that.

Despite your good and helpful intentions, the above solutions are wayyy to complicated for me - this is the first time I'm using anything other than Windows.
As far as encrypting files is concerned - between the 2 of us (the other user and me) we have thousands of files and encrypting each one individually will take up the rest of our lives!
Isn't there a simple way to just protect certain folders with a password? Because if there isn't, then that means ubuntu users have no way to make their data private - a single consideration important enough to put off many potential average users. In any case, different users' home folders should be accessible **only** to them by default.

---

### Post by ddrichardson on 2007-07-22
Their data is protected by default! Users have no need for root access, and permissions for each folder can be set (right click in nautilus) to prevent them even reading the contents of a folder.

This is the whole purpose of groups - if you need a user to have the ability to install software, then that permission can be granted - it doesn't mean they can override your permissions on folders.

Each file on a UNIX system is encoded with permissions, something not even supported by Windows until NTFS came along, in the format RWX-RWX-RWX where each group of three letters  corresponds to user, group and the world.

If you set a folder as RWX------ then only you can access it.

This is one of the hardest concepts for new users to grasp, not your fault obviously, because Windows was not designed this way ehereas UNIX was. Try to forget the Windows XP concept of users with administrative rights and restricted users, it's much more akin to the Administrator account.

---

### Post by kleo skywalker on 2007-07-22
I think that when you're trying to get your computer to work according to your preferences after installing a different OS for the very first time in your life, you may not necessarily approach things in the order that more experienced users do. And I can see that Ubuntu and Windows don't work the same way, and I'm not saying anything about who developed what first and what's works better where etc. All I want to know is how to make a particular thing work without breaking anything.
What I can see is a large part of what I know, so here it is:
I logged in as an administrator, as well as as a desktop user, and I can see every user's all data, so could you please explain what you mean by it being protected by default?
Also, how do user groups and permissions work? For example, there are 2 users on my computer, one administrator and one desktop user. There is a folder in the desktop user's home folder that I want to make private - that is, only the desktop user should be able to access it. How do I do that?

---

### Post by meierfra on 2007-07-22
I don't think you solved kleo skywalker problem yet. This is how I see the situation:

There will be only two people accessing the computer.
Obviously one of them will have to have sudo right (otherwise the system can not be administered)
Is there any way  to prevent this person to read/change the other persons files?

---

### Post by kleo skywalker on 2007-07-22
> **meierfra said:**
> I don't think you solved kleo skywalker problem yet. This is how I see the situation:

There will be only two people accessing the computer.
Obviously one of them will have to have sudo right (otherwise the system can not be administered)
Is there any way  to prevent this person to read/change the other persons files?

Thanks.
In addition to what you've said, all I need is know how to configure permissions for individual folders.

---

### Post by ddrichardson on 2007-07-22
> **kleo skywalker said:**
> I think that when you're trying to get your computer to work according to your preferences after installing a different OS for the very first time in your life, you may not necessarily approach things in the order that more experienced users do. And I can see that Ubuntu and Windows don't work the same way, and I'm not saying anything about who developed what first and what's works better where etc. All I want to know is how to make a particular thing work without breaking anything.

Neither am I, I'm trying (obviously badly) to explain the UNIX permission system in terms familiar to a Windows user ;-)

> 
What I can see is a large part of what I know, so here it is:
I logged in as an administrator, as well as as a desktop user, and I can see every user's all data, so could you please explain what you mean by it being protected by default?
Also, how do user groups and permissions work? For example, there are 2 users on my computer, one administrator and one desktop user.

User is a username, group is a group of people. User permissions stipulate what that user can do to the file. Group permissions stipulate what members of that group can do to the file. The last part of the permission system stipulates what anyone who is not the user or a member of that group can do.

> There is a folder in the desktop user's home folder that I want to make private - that is, only the desktop user should be able to access it. How do I do that?

Set it's group as say, RESTRICTED_ME and then change its access to RW-RW---- then add the users who can access it to that group. If you and your other user are in the same group (desktop administrators) then you will both see it, if your other user isn't then they can't.

Think of groups like policies in Windows. A user can be a member of many groups, for example most users will be a member of dhcp as they need to be able to access the internet.

In fact if you set it to RW- --- --- only you the username can access it.

---

### Post by meierfra on 2007-07-22
ddrichardson:  Tell me if I'm wrong. As far  as I  know   you can set the permission of a file  any way you want to, but  a person with sudo rights will still be able to read and write to the file  via " sudo gedit filename"

---

### Post by ddrichardson on 2007-07-22
> **meierfra said:**
> ddrichardson:  Tell me if I'm wrong. As far  as I  know   you can set the permission of a file  any way you want to, but  a person with sudo rights will still be able to read and write to the file  via " sudo gedit filename"

It depends on how you specify /etc/sudoers. What I'm saying is that there should only be one person administering one machine.

---

### Post by meierfra on 2007-07-22
> IWhat I'm saying is that there should only be one person administering one machine.

Yes, but we are trying to prevent this one person from accessing  the other peoples files. Is there a way to do that by editing "/etc/sudoers"?

---

### Post by ddrichardson on 2007-07-22
Are you saying that regardless of who is administering the computer, that admin shouldn't be able to access the other users files?

---

### Post by meierfra on 2007-07-22
Yes, that's what  Skywalker wants. More precisely he wants to be able to shield  particular files from the administrator.

---

### Post by ddrichardson on 2007-07-22
The only way to do that (to some degree) is, in the case of two users, to have three accounts - one for each user and one to carry out major administrative tasks, hence why many distros use the root account.

That way the sudoers file can be used to configure exactly what access and programs each user can run.

However if the data is that in need of security it would be considerably easier to either use something like GPG to encrypt them or to use a removable device.

---

### Post by bodhi.zazen on 2007-07-22
:lolflag: ~ And so this thread goes full circle ~ Permissions + Encryption :twisted: ~ :lolflag:

---

### Post by kleo skywalker on 2007-07-22
Once again, here's what I want: I want 2 user accounts with administrative privileges and I want both to be able to keep some of their stuff inaccessible to the other. In fact, the main reason I want 2 separate user accounts is for the 2 users to have privacy, and be able to customize their PC experience.
If you must know, I share the computer with my teenaged brother, and he will absolutely not accept a situation where his stuff isn't private or where he can't install stuff by himself.
Also, if there isn't a solution to my problem, I'm in a huge fix, because I was the one rooting (pun unintended) for Ubuntu and if stuff doesn't work out I'll have to go buy Windows Vista (which is not something I want to have to do!)
So please help, thanks.

---

### Post by ddrichardson on 2007-07-22
Steady on fella we're all trying to help here!

As I have said, it is perfectly possible to create folders others have no access to. You need to work out exactly what you mean by "customizeable", then use groups and sudoers to define what can and cannot be accessed. If you want everyone to be able to do anything to the computer from one installation then you simply cannot keep anything completely private.

You have alternatives - To create seperate home partitions for each user and prevent access to these partitions for the other users.

Or if you want anyone to do anything to any part of thier installation, to create multiple partitions with a seperate install for each user.

In any case, if you wish to buy Vista then you wont be able to completely protect any folder while having complete control over installation/administration either.

---

### Post by ddrichardson on 2007-07-22
Further to what bodhi.zazen said earlier (lol - full circle again), have you considered encrypting the whole folder rather than individual files? It would entail either changing to multiple home partitions or creating a large empty file but it is possible.

I can talk you through this if you like, it is however fairly involved and time consuming.

---

### Post by davidjmayo on 2007-07-22
> ddrichardson

In any case, if you wish to buy Vista then you wont be able to completely protect any folder while having complete control over installation/administration either.

+1 
Exactly. If you have admin rights

---

### Post by AKA3Toes on 2007-07-22
> **kleo skywalker said:**
> [I][SIZE="1"]I've been a windows user for many years and I've only just switched to ubuntu feisty. Please help me clarify some stuff about how user accounts work in ubuntu.
Normally, 2 people will use my computer - both need to be able to do administrative stuff, and keep some amount of data to themselves. 
Here are my questions:
1) I think I know the basics of how to set user privileges and stuff (System-->Administration-->Users and Groups and so on). So if there are 2 administrator accounts, each will use her/his own password to do administrative tasks, right?
2) It seems that administrators can see all data on the computer. Is that right? If yes, what can users do to keep some of their data (like pictures and spreadsheets - private stuff) to themselves and share some of it (like music) with other users?
Thanks.
P.S.: Simple solutions please![/SIZE][/I][FONT="Times New Roman"][COLOR="DarkRed"][I][SIZE="3"]---Good day kleo. I myself am a new user and can offer a little advice. Too busy right now to go through all the posts, I am working on setting up RAID and was on my way to post my query.

---Now first off, I was not simply an user of my old Wondows OS, I was the owner/operator/technician. I turned my back about a week ago and haven't looked back. 

---I'll say this straight out before I tell you what I have done and if you're going to play with settings, make sure you know what your playing with before you change the owner/group/etc. So far I have set up everything 3 times and started from the beginning cause well... I am taking a crash course.

---Changing ownerships in Users and Groups to give myself access to files is what caused me to just wipe everything. Errors telling me that my user did not have a home left me without a desktop and too new to know how to perform maintenance and change back what I did so I could again access my desktop. Others stating in various posts that you must set up RAID during installation, made me give less about wiping the new distro and starting from scratch. If you're in this position, IMHO, it's a good time to play, but again... know what your handling.

---I used nautilus to change ownership on files gone and well, that's probably why it's there on the disk. So you don't kick yourself out of your home trying to gain writing privileges to "certain" files.

---FWIU, placing a period in front of the name of the folder ".receipts" will hide the folder. I haven't looked to see if the files in the folder are automatically tagged with the prefix "." also or if a period as a prefix in front of the file even hides the file (surely it does), right now I am too concerned with the files that I am trying to share through wired connection to my router, with XP that is on wireless to that router. Privileges may have been why XP was having problems, Ubuntu (SAMBA) found XP immediately.

---Hope that helps and again, be careful and if you do something, make sure you really want to do it. With full administrative privileges, I haven't seen a box in the desktop environment yet that says "Are you sure you want to do this?" That's what seems the coolest about the OS so far, I can do a lot of things and then at the end say "Yes" This gives me plenty of time to change my mind about one... LOL, not sit there and stare at the 7th box wondering if it's necessary or worth it.[/SIZE][/I][/COLOR][/FONT]

---

### Post by AKA3Toes on 2007-07-22
[FONT="Times New Roman"][SIZE="3"][COLOR="DarkRed"]*---Wow, [[color=red]_bodhi.zazen_[/color]]("http://ubuntuforums.org/member.php?u=89054") got some good info running in this thread and from the way he posted his last statement, I had to go back and take a peek. It looks like he's very pleased with the way the "demonstration" went, so I'll have to come back later to read through the thread.*[/COLOR][/SIZE][/FONT]

---

### Post by kleo skywalker on 2007-07-22
Separate partitions for individual home folders is an idea, but I don't think that'll work for me. Again, let me state the facts instead of asking for a solution to a theoretical problem:
I share a computer with my brother. Roughly, both of us have the following kinds of files: music, pictures, videos, and others (like documents & spreadsheets etc). We want access to each other's music, but not the other stuff. 
This is why putting our home folders on separate partitions and making the whole partition inaccessible is not such a great idea because how do we share music then?
(If this helps, what we did on Windows was keep music in a shared folder or non-primary drive - D:, and the rest in our respective "my documents" folders - C: -  where it was inaccessible to others.)
And in response to what I mean by customizable, I mean both users should be able to install and remove applications, customize their desktop etc - in a nutshell, have a private space for themselves on the computer.
So what happens next?
Thanks.
P.S.: I've just started, but so far I like Ubuntu, I like its philosophy, I don't mind figuring stuff out, and  I'm ok with making adjustments. The trouble is, none of this applies to the person who shares this computer with me - my teenaged brother - he is almost technologically challenged (I'm not so much better, but I don't mind learning as long as I don't risk ruining stuff), he isn't interested in the philosophy part, he likes his fancy-schmancy Windows Live Messenger (inexplicably, all his contacts are on it), and he's willing to throw out an entire OS just because GAIM doesn't give those tiny pop-up alerts when contacts on your list come online. 
So in asking all these questions, I'm trying to get stuff to work the way he wants, so that I don't have to give up Ubuntu.
Please help.

---

### Post by davidjmayo on 2007-07-22
To go back to your original question which was "simple solutions please." and your last post 
> P.S.: I've just started, but so far I like Ubuntu, I like its philosophy, I don't mind figuring stuff out, and I'm ok with making adjustments. The trouble is, none of this applies to the person who shares this computer with me - my teenaged brother - he is almost technologically challenged (I'm not so much better, but I don't mind learning as long as I don't risk ruining stuff), he isn't interested in the philosophy part,** he likes his fancy-schmancy Windows Live Messenger (inexplicably, all his contacts are on it), and he's willing to throw out an entire OS just because GAIM doesn't give those tiny pop-up alerts when contacts on your list come online.**
So in asking all these questions, I'm trying to get stuff to work the way he wants, so that I don't have to give up Ubuntu.


My suggestion to you is a dual boot that way you both seem happy. You have your win solution already and the ubuntu is yours to do what you want with it. You want the simple solution. Reading this thread I think that is the simplest solution. You can share stuff between windows and ubuntu but you will need to add some apps for write acces but read is there already for ubuntu. I don't think windows will recognise the ubuntu partitions but there is an app you can add.

EDIT: Not sure if the permissions will be recognised by the different OSes?? Would need further info on your windows partitioning

---

### Post by ddrichardson on 2007-07-22
> **kleo skywalker said:**
> 
(If this helps, what we did on Windows was keep music in a shared folder or non-primary drive - D:, and the rest in our respective "my documents" folders - C: -  where it was inaccessible to others.)
And in response to what I mean by customizable, I mean both users should be able to install and remove applications, customize their desktop etc - in a nutshell, have a private space for themselves on the computer.
So what happens next?

A shared folder in home, set with a group called shared_data with read, write and execute permission. Add the three users to this group and hey presto - a shared folder.

The private space can be defined as standard on any new account. You need to limit their sudo access to apt-get/synaptic so they can install progams, but not access your data. If your brother is as technophobic as you state then he isn't going to know you can sudo into his files (not being unethical here - I assume you wouldn't actually do this).

> GAIM doesn't give those tiny pop-up alerts when contacts on your list come online.

I haven't used gaim in a while but pidgin (its succesor) can do this with the guifications plugin if that helps.

_In anycase davidjmayo hits the nail on the head - dual boot, then your everyone is happy._

---

### Post by kleo skywalker on 2007-07-22
Dual-booting with Windows is my last resort - I'll have to go buy something that keeps crashing and getting bombarded with rubbish!
It's been just a day since I installed Ubuntu, so I want to try to make it work the way my brother wants - of course if that doesn't work, I will have to buy Windows.
Fact is, my brother's demands are pretty basic. Keeping some of your data private while sharing your music, having a decent IM client (the version of Gaim installed on Feisty by default is really lame, even for me who's happy chatting from inside Gmail), and being able to enqueue songs into your media player from the folder itself - that's not too much to ask for, is it?



> **ddrichardson said:**
> A shared folder in home, set with a group called shared_data with read, write and execute permission. Add the three users to this group and hey presto - a shared folder.

The private space can be defined as standard on any new account. You need to limit their sudo access to apt-get/synaptic so they can install progams, but not access your data. 

_In anycase davidjmayo hits the nail on the head - dual boot, then your everyone is happy._

Thanks, how do I do this?

P.S.:Solutions to any of the above problems will be very welcome! I asked about the IM client [here]("http://ubuntuforums.org/showthread.php?t=506791"), and about the media player thing [here]("http://ubuntuforums.org/showthread.php?t=506947"), so you can post there as well.

---

### Post by ddrichardson on 2007-07-22
> **kleo skywalker said:**
> Dual-booting with Windows is my last resort - I'll have to go buy something that keeps crashing and getting bombarded with rubbish!
It's been just a day since I installed Ubuntu, so I want to try to make it work the way my brother wants - of course if that doesn't work, I will have to buy Windows.

Tell *him* to buy windows :-)

> **kleo skywalker said:**
> Fact is, my brother's demands are pretty basic. Keeping some of your data private while sharing your music, having a decent IM client (the version of Gaim installed on Feisty by default is really lame, even for me who's happy chatting from inside Gmail), and being able to enqueue songs into your media player from the folder itself - that's not too much to ask for, is it?

No its not too much to ask. 

Create a group called shared and a group called installers (System/Administration/Users & Groups/Manage Groups/Add Groups, ticking the users you want to allow access. Then from a terminal:

```
sudo nautilus
```

Navigate to /home, right click and create a directory called shared. Right click again, click Properties/Permissions. Set the permissions to look like the attached picture.

That's your shared folder set up.

Now onto sudoers. 

Right, first things first backup:

```
sudo cp /etc/sudoers /etc/sudoers.bak
```

Next:

```
sudo visudo
```

The file looks like this:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Add a new line at the end that reads as follows:
```
%installers ALL=(root) /usr/bin/aptitude, /usr/bin/apt-get
```

The programs stated are the only ones that the installers group can execute with root permission. 

This will mean that members of shared and installers - your brother for example can access a shared folder and can install software.

---

### Post by bodhi.zazen on 2007-07-22
Well, young skywalker, you will have to do some reading. I understand the frustration of a new OS.

The problem is you are asking us to type long how-to's to accomplish your goals. If I wrote them they would appear very similar to the links I gave you ...

So, please read and ask for clarification where needed, at lease that is how, IMO, we can help you best.

1. Read permissions for privacy. My home folder has permissions of 700.

2. If you have either physical access or root (admin) access the *only* way t have privacy, beyond permissions, is with encryption. Administrators (root) has access to everything.

3. Yes, you can each have your own desktop customizations, very easily.

4. He he he ... If you brother does not like Ubuntu. let him buy Windows.

5. You can have a shared data partition with Ubuntu just like windows. You then make a likn in your home directory. A link is a short cut. So if, for example, you have a shared partition mounted at /media/data with music (/media/data/music) you then link with ```
ln -s /media/data/music /home/<user_name>/music
```This creates a directory (folder) in your home directory "music" which is a direct link to the shared music directory on the shared partition. You ser access with permissions.

Experienced users can do all you are asking with Ubuntu. You (and your brother) need to be willing to read and learn a new OS which may take 3-6 months.

---

### Post by bodhi.zazen on 2007-07-22
> **ddrichardson said:**
> 

```
sudo nautilus
```

Now, now ddrichardson, teach 'em right :twisted:

For graphical apps you should use gksudo (aka gksu).

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by ddrichardson on 2007-07-22
> **bodhi.zazen said:**
> Now, now ddrichardson, teach 'em right :twisted:

For graphical apps you should use gksudo (aka gksu).

My mistake ;-) - still not bad for someone typing left handed with a cat on their keyboard...

---

### Post by bodhi.zazen on 2007-07-22
LOL

I have a baby :)

---

### Post by ddrichardson on 2007-07-22
Been there (three times) at least they don't chase the pointer on screen and scratch your arms when they're happy.

---

### Post by AKA3Toes on 2007-07-22
[SIZE="3"][FONT="Times New Roman"][COLOR="DarkRed"][I]---Mine just lays across my wrist or forearm and she's not partial to left or right. Whether I need the mouse or the keyboard, she's there... [indent]... but I really miss my Siamese, lost her to that dang clumping litter last year[/indent]

---And (Misplaced), how did I spill the beans? by admitting I've reinstalled three times or by hinting toward nautilus... lol. I was afeared to say "sudo nautilus" and more devoted to saying "be careful".

---Like I had said, make sure you don't play with anything in nautilus unless you really* want to change it. Keep an eye on which window is your file browser and which one is your Nautilus. One oops with the wrong file and I'm sure it'll be irreversible... going by Murphy's law.[/I][/COLOR][/FONT][/SIZE]

---

### Post by meierfra on 2007-07-22
I'm not  sure whether this is practical, but I suggest it anyway:

Set up  three accounts, one administrator and one each for you and  your brother.

The accounts for you and your brother have   sudo rights   restricted to installing programs.

For the administrator account choose a password whose first half is only known to you and the second half is only known to your brother.

---

### Post by meierfra on 2007-07-23
Well I  tried out ddrichardsons method to create a user account which can install programs but has no other sudo right.  It actually wasn't all that difficult  and worked perfectly.

Then I thought the user should be able to use the Synaptic Package Manager. So I added "/usr/sbin/synaptic" to the list of allowed sudo commands.  But it didn't worked, in fact it failed for any program with a graphical interface.  Googleing the error messages I found the following fix:

The line 
```
Defaults !lecture,tty_tickets,!fqdn
```
in /etc/sudoers  must be appended as follows:
```
Defaults	!lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME XAUTHORIZATION"
```

I don't really know what this extra command does or whether it has  negative  side effects , but it seems to do the job.

---

### Post by ddrichardson on 2007-07-23
> **meierfra said:**
> Well I  tried out ddrichardsons method to create a user account which can install programs but has no other sudo right.  It actually wasn't all that difficult  and worked perfectly.

Then I thought the user should be able to use the Synaptic Package Manager. So I added "/usr/sbin/synaptic" to the list of allowed sudo commands.  But it didn't worked, in fact it failed for any program with a graphical interface.  Googleing the error messages I found the following fix:

The line 
```
Defaults !lecture,tty_tickets,!fqdn
```
in /etc/sudoers  must be appended as follows:
```
Defaults	!lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME XAUTHORIZATION"
```

I don't really know what this extra command does or whether it has  negative  side effects , but it seems to do the job.

In the thread that wont die today ;-)

[LIST]
[*]enc_keep is just a variable that holds anything to be presevered in the user's account in this case being used to access the X display.
[*]tty_tickets makes you login again for every tty you open. 
[*]fqdn is a good idea to avoid because although it allows the use of fully qualified domain names, it slows things down by doing DNS searches, especially if your DNS drops out.
[/LIST]

lecture is my favourite - something only UNIX coders would ever consider. It prints the contents of lecture_file telling the user the reasons not to do what they are doing.

> Googleing the error messages I found the following fix

This is an excellent point that I sometimes wonder how many (even experienced users) know - before googling, try using man from the command line. I know the command line seems a little out of vogue these days but man is the primary documentation system on all UNIX type systems. It also has entries on files - so if you do a man sudoers: ta da every possible variable is there.

man can be a little impenatrable but is an excellent place to start.

---

### Post by kleo skywalker on 2007-07-24
The way to do what I wanted was very very simple.  So for the next clueless newbie, here it is:
Go to **System**-->**Administration**-->**Users and Groups**. 
On **Manage groups**, there's a group for each username (that is, if there's a username *blah*, there's a group called *blah*). 
Select the one you want to configure, and click on **Properties**. Check the member names you want in that group.
Once that's done, go the folder (or file) you want to keep to yourself. Right-click to go to **Properties**-->**Permissions**. For **Others** select the access permission as **None**. **Apply permissions to enclosed files** and **Close**.
Now only you and other members of that group (in my case none) can access that folder.

---

### Post by bodhi.zazen on 2007-07-24
> **kleo skywalker said:**
> The way to do what I wanted was very very simple.  So for the next clueless newbie, here it is:
Go to **System**-->**Administration**-->**Users and Groups**. 
On **Manage groups**, there's a group for each username (that is, if there's a username *blah*, there's a group called *blah*). 
Select the one you want to configure, and click on **Properties**. Check the member names you want in that group.
Once that's done, go the folder (or file) you want to keep to yourself. Right-click to go to **Properties**-->**Permissions**. For **Others** select the access permission as **None**. **Apply permissions to enclosed files** and **Close**.
Now only you and other members of that group (in my case none) can access that folder.

\o/

See, permissions, permissions, permissions ...

While I am sorry it was a struggle for you I am also glad :

1. You were able to problem solve for yourself.

2. You took the time to post your solution.

3. You marked the thread as solved \o/

In a few short weeks/months it will all become much easier for you.

Now, don't go changing the permissions on system files ...

Welcome to Ubuntu.

---

