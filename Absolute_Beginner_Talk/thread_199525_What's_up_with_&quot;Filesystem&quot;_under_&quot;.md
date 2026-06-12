---
title: "What's up with &quot;Filesystem&quot; under &quot;Computer&quot;?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ZeusABJ on 2006-06-18
The Filesystem icon is proving to be a bit puzzling to me. When I first installed Ubuntu I took the defaults (erase entire disk) and when I went to "Places ---> Computer". Once there all I saw was my Optical drive, Floppy Drive and at third drive labeled "Filesystem". Naturally I just assumed it was an indicator of the hard drive that Root was installed on. Since I only had one hard drive I figured it listed the whole thing as "Filesystem". Well I decided to partition my drive (for the sake of efficiency) and I decided to mount my Home folder on a different partition than Root (again, which I am assuming to be the equivalent of "Filesystem"). Well when my desktop loads up after my reinstall I see my two partitions (Home and Root) but oddly enough Filesystem is still there? Clearly it must be something else entirely. So I'm a little confused...what exactly does this item represent? Also (its minor I know) but I’m not 100% thrilled with the way Gnome is naming my partitions. Is there any way to specify an Alias for them (like listing Root as “System Disk” and Home as “Files Disk”?

---

### Post by user1397 on 2006-06-18
"filesystem" is equivalent to **/**

i believe  you can rename them by simply right-clicking > rename

btw, is that muse's singer in your avatar?

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=erik1397]"filesystem" is equivalent to **/**

i believe  you can rename them by simply right-clicking > rename

btw, is that muse's singer in your avatar?[/QUOTE]

Well if its equivalent to / then why do I have it in addition to my Root partition. That&#8217;s why I'm confused. Right clicking and choosing "Rename" gives me the following error:

"The item could not be renamed"

That&#8217;s why I'm so confused. Why won't it work? My avatar is David Tennant, the current incarnation of Doctor Who, protagonist of the best Sci-Fi show ever!!!! Check it out:

[http://www.bbc.co.uk/doctorwho/gallery/doctor10_rose/index.shtml](http://www.bbc.co.uk/doctorwho/gallery/doctor10_rose/index.shtml)

Not quite as poetic as you implied, but it's still pretty cool (in my opinion)!

---

### Post by user1397 on 2006-06-18
[quote=ZeusABJ]Well if its equivalent to / then why do I have it in addition to my Root partition. That’s why I'm confused. Right clicking and choosing "Rename" gives me the following error:

"The item could not be renamed"

That’s why I'm so confused. Why won't it work? My avatar is David Tennant, the current incarnation of Doctor Who, protagonist of the best Sci-Fi show ever!!!! Check it out:

[http://www.bbc.co.uk/doctorwho/gallery/doctor10_rose/index.shtml]("http://www.bbc.co.uk/doctorwho/gallery/doctor10_rose/index.shtml")

Not quite as poetic as you implied, but istill pretty cool (in my opinion)![/quote]well, you may have two root partitons.  did you install a new linux os or something?  ah, it couldn't be renamed because it would need root privileges.  i wouln't mess much with it though, the "filesystem" should remain the way it is, i don't know what catastrophic effects might occur if you rename it otherwise.

and talking about "muse", i wasn't talking about the greek myths, i was talking about the band muse, from england.  no hard feelings.

---

### Post by ZeusABJ on 2006-06-18
Okay I'm completely confused (and concerted) now. I have my HOME directory on a completely different partition than ROOT, yet when I browse my ROOT partition I see HOME there and any changes I make on my HOME partition are reflected in ROOT. What's the deal there? Are they "linked" somehow or is it actually making a copy of the items in HOME onto my ROOT partition?! Also the same thing is true of "Filesystem". Can anyone explain how the icons listed under "Computer" actually interact with each other? Because I am totally lost here and would really like to know what&#8217;s going on.

Oh and good one Erik1397!!! Here I was thinking you were getting all philosophical on me and you were just talking about a rock band. That&#8217;s too much!

---

### Post by user1397 on 2006-06-18
actually, if you go to system > administration > disks, what does it look like?  an attachment of a screenshot would be best?

---

### Post by user1397 on 2006-06-18
[quote=ZeusABJ]Okay I'm completely confused (and concerted) now. I have my HOME directory on a completely different partition than ROOT, yet when I browse my ROOT partition I see HOME there and any changes I make on my HOME partition are reflected in ROOT. What's the deal there? Are they "linked" somehow or is it actually making a copy of the items in HOME onto my ROOT partition?! Also the same thing is true of "Filesystem". Can anyone explain how the icons listed under "Computer" actually interact with each other? Because I am totally lost here and would really like to know what’s going on.

Oh and good one Erik1397!!! Here I was thinking you were getting all philosophical on me and you were just talking about a rock band. That’s too much![/quote]im pretty sure that the reason you have 2 "root" icons is that you partitioned your hard drive to have a separate /home.  "Filesystem" always has to be there, but since you separated /home from /, a different icon was set for both root ( / )and home ( /home ).  So basically, your 2 root icons are the exact same thing, /home is a seperate icon, but it is the same as going to filesystem > home or root > home.

---

### Post by ZeusABJ on 2006-06-18
Well all that view shows is my partitions. All I did was follow this guide to the letter:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

The only change I made was selecting "/home" as my mount point instead of his custom option of "/documents". Any ideas?

---

### Post by user1397 on 2006-06-18
[quote=ZeusABJ]Well all that view shows is my partitions. All I did was follow this guide to the letter:

[http://www.psychocats.net/ubuntu/installing.html]("http://www.psychocats.net/ubuntu/installing.html")

The only change I made was selecting "/home" as my mount point instead of his custom option of "/documents". Any ideas?[/quote]so you reinstalled ubuntu but this time with dapper?

---

### Post by aysiu on 2006-06-18
If you have a separate /home partition, it is "mounted" as the home folder within the / partition (the "root" partition).

So when you're at the top level of the folder hierarchy, you'll see a folder called /home. Once you click on that, instead of actually being taken to a folder called /home within the hierarchy, you'll be taken to your home partition.

It's a bit like a Windows shortcut or Mac alias. If you create a Windows shortcut to D: on your desktop, it appears to be an icon on your desktop, but it's not really on your desktop--it's on a separate drive. Same thing here. /home appears to be a folder within another folder. When you click on it, it goes to another partition.

It's a bit like the wardrobe in *The Lion, the Witch, and the Wardrobe* or the telephone booth in *The Matrix*.

Does that make sense or confuse you more?

---

### Post by user1397 on 2006-06-18
thanks aysiu, that was clearer and more concise than anything i could come up with.

btw, you'll find a picture of matthew bellamy, lead singer of muse, down in my attachment.  notice any similarities?

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=aysiu]If you have a separate /home partition, it is "mounted" as the home folder within the / partition (the "root" partition).

So when you're at the top level of the folder hierarchy, you'll see a folder called /home. Once you click on that, instead of actually being taken to a folder called /home within the hierarchy, you'll be taken to your home partition.

It's a bit like a Windows shortcut or Mac alias. If you create a Windows shortcut to D: on your desktop, it appears to be an icon on your desktop, but it's not really on your desktop--it's on a separate drive. Same thing here. /home appears to be a folder within another folder. When you click on it, it goes to another partition.

It's a bit like the wardrobe in *The Lion, the Witch, and the Wardrobe* or the telephone booth in *The Matrix*.

Does that make sense or confuse you more?[/QUOTE]

**"It's a bit like the wardrobe in *The Lion, the Witch, and the Wardrobe* or the telephone booth in *The Matrix*." **

Those have to be two of the coolest metaphors ever!!! Yeah I'm seeing that regardless of how I get to HOME (Filesystem or ROOT) when I right-click on it and choose "Properties" it lists the volume as "HOME". It&#8217;s just a little annoying (and a bit counter-intuitive in my opinion) to have two icons located in the same window that basically serve the same function and take me to the same place. I assume anyone else that is running several partitions has this as well? Is it a good idea to drop Home on a separate partition like this? My plan was to make that HOME partition my all-purpose files directory. Should I maybe put that stuff on a different partition?

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=erik1397]thanks aysiu, that was clearer and more concise than anything i could come up with.

btw, you'll find a picture of matthew bellamy, lead singer of muse, down in my attachment.  notice any similarities?[/QUOTE]

Yeah but he's no David Tennant!!!

:mrgreen: 

but I'm biased!

---

### Post by user1397 on 2006-06-18
[quote=ZeusABJ]**"It's a bit like the wardrobe in *The Lion, the Witch, and the Wardrobe* or the telephone booth in *The Matrix*." **

Those have to be two of the coolest metaphors ever!!! Yeah I'm seeing that regardless of how I get to HOME (Filesystem or ROOT) when I right-click on it and choose "Properties" it lists the volume as "HOME". It’s just a little annoying (and a bit counter-intuitive in my opinion) to have two icons located in the same window that basically serve the same function and take me to the same place. I assume anyone else that is running several partitions has this as well? Is it a good idea to drop Home on a separate partition like this? My plan was to make that HOME partition my all-purpose files directory. Should I maybe put that stuff on a different partition?[/quote]well the irony in all this, is that i do have seperate / and /home partitions, but there's only the "filesystem" icon in places > computer!!!

---

### Post by aysiu on 2006-06-18
[QUOTE=ZeusABJ]Is it a good idea to drop Home on a separate partition like this? My plan was to make that HOME partition my all-purpose files directory. Should I maybe put that stuff on a different partition?[/QUOTE] The answer is that it is a good idea to have home on a separate partition. It makes doing a clean reinstall easier (either because you messed up your system and want to reinstall or because you want an easy way to upgrade your system to Edgy or later Ubuntu releases).

The second part of the answer is that the home partition should contain not only your settings and preferences but *also* your files (so, yes, it is the "all-purpose files directory").

---

### Post by ZeusABJ on 2006-06-18
Well, surprise surprise! I just updated my system, rebooted and *BAM* one single "Filesystem" icon. So looks like that was a bug or something. I’ll bet there’s some option to “View Partitions in Computer” and an update killed it. Very interesting. So Filesystem is basically the top of the folder hierarchy. Okay, cool. I like it much better this way anyway (single icon and my partitions hidden)

SWEET! So if someone else complains, tell ‘Em “Update and reboot”!

---

### Post by ZeusABJ on 2006-06-18
[QUOTE=aysiu]The answer is that it is a good idea to have home on a separate partition. It makes doing a clean reinstall easier (either because you messed up your system and want to reinstall or because you want an easy way to upgrade your system to Edgy or later Ubuntu releases).

The second part of the answer is that the home partition should contain not only your settings and preferences but *also* your files (so, yes, it is the "all-purpose files directory").[/QUOTE]

EXCELLENT! That was EXACTLY what my line of reasoning was Aysiu. When Edgy drops this Winter I want to do a clean install, so looks like I'm right on track. Now if I can just figure out an easy way to create all my directories under HOME and assign permissions. So far it looks like "sudo" under command line is my only route since "Create New Folder" is greyed out under right-click. Man Windows does spoil you with that ease of use in creating directories, but its like my Gentoo buddy says, “That’s the price of having a truly secure OS”.

Thanks for all the help guys!

---

### Post by user1397 on 2006-06-18
[quote=ZeusABJ]Now if I can just figure out an easy way to create all my directories under HOME and assign permissions.[/quote]why would you want to do that?  do you mean all your personal files under /home?  they should already be there.  or do you mean all files (root) to be under home?  now THAT would be pointless.

---

### Post by aysiu on 2006-06-19
Anything within /home/zeusabj should allow you to right-click to make a new folder.

If you wanted something like /home/randomfiles accessible to all users, what you would do is ```
sudo mkdir /home/randomfiles
sudo chown -R zeusabj:zeusabj /home/randomfiles
sudo chmod -R 777 /home/randomfiles
sudo ln -s /home/randomfiles /home/zeusabj/randomfiles
``` By the way, if you create a launcher for the command ```
gksudo nautilus
``` you can temporarily browse as root.

---

### Post by user1397 on 2006-06-19
or you can also press ALT+F2 and type 'gksudo nautilus'

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=aysiu]Anything within /home/zeusabj should allow you to right-click to make a new folder.

If you wanted something like /home/randomfiles accessible to all users, what you would do is ```
sudo mkdir /home/randomfiles
sudo chown -R zeusabj:zeusabj /home/randomfiles
sudo chmod -R 777 /home/randomfiles
sudo ln -s /home/randomfiles /home/zeusabj/randomfiles
``` By the way, if you create a launcher for the command ```
gksudo nautilus
``` you can temporarily browse as root.[/QUOTE]

To answer your question Erik1397 Aysiu has hit my idea right on the head. Besides hosting my user-specific files I was also planning to use HOME to host some directories that could apply to multiple users. I have some very large directories on my machine that are used by both me and my wife. A few examples would be:

Music - My MP3 collection (40GB).
Pictures - Where we drop the digital photos (4GB).
Images - General Disc Images (like Ubuntu LIVE)

These are things multiple users might need access too. So rather than drop them all in my personal user directory under HOME, I planned to go the route Aysiu talked about and just drop them in the HOME folder OUTSIDE of any specific user folder. Then I was just going to create a group with the appropriate permission set to use those folders and assign the users that need access to that group (which means I&#8217;ll be asking question son permissions soon, lol). 

Does that seem like a good/bad idea to you guys?

---

### Post by user1397 on 2006-06-19
[quote=ZeusABJ]Does that seem like a good/bad idea to you guys?[/quote]it seems like a great idea, but i would follow exactly what aysiu said.

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=erik1397]it seems like a great idea, but i would follow exactly what aysiu said.[/QUOTE]

Of course! Aysiu is like.... my own private little Linux Yoda! I currently worship at Aysiu's alter of Linuxdom

[-o<

---

### Post by aysiu on 2006-06-19
Well, there is a little snafu to this, which is that files created by anyone default to a 600 permission--meaning that the owner can read/write, but the group and the other users can't do anything.

This is stupid, I know, but it's supposed to be for security reasons. If you ask me, any user in the same group as another user should at least be able to read the other user's file, if not write to it.

So one way to deal with it is to change the permissions on every file you create. Kind of a pain. Unfortunately, I don't know how to change the *umask* option for a folder.

Read [this thread](http://ubuntuforums.org/showthread.php?t=145741) for more details.

**Whoops**: I take it back, there was [a solution](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9) in that thread--I even bookmarked it.

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=aysiu]Well, there is a little snafu to this, which is that files created by anyone default to a 600 permission--meaning that the owner can read/write, but the group and the other users can't do anything.

This is stupid, I know, but it's supposed to be for security reasons. If you ask me, any user in the same group as another user should at least be able to read the other user's file, if not write to it.

So one way to deal with it is to change the permissions on every file you create. Kind of a pain. Unfortunately, I don't know how to change the *umask* option for a folder.[/QUOTE]

Well is it necessary to change permissions on EVERY file? Won't permissions on the directories inherit down to their contents?

---

### Post by aysiu on 2006-06-19
[QUOTE=ZeusABJ]Well is it necessary to change permissions on EVERY file? Won't permissions on the directories inherit down to their contents?[/QUOTE]
Read the thread I linked to.

---

### Post by user1397 on 2006-06-19
aysiu i have a question while you're here: i know this is a little off-topic, but how do you rename files with the terminal?

---

### Post by aysiu on 2006-06-19
I just used the *mv* command.

```
mv ~/oldfilename ~/newfilename
```

---

### Post by user1397 on 2006-06-19
[quote=aysiu]I just used the *mv* command.

```
mv ~/oldfilename ~/newfilename
```[/quote]oh duh! yea that works, thanks

---

### Post by ZeusABJ on 2006-06-19
[QUOTE=erik1397]so you reinstalled ubuntu but this time with dapper?[/QUOTE]

No, Dapper is my first attempt to go full blown with Linux. I'm sure you are familiar with the constant threat of spyware and viruses under windows. Plus it can be a pain to update software. Well, being the OCD person I am I adopted a "spring cleaning" plan a several years ago shortly before XP hit the scene. I split my hard disk into two partitions. On one I put the OS, on the other all my important data. I even hacked my registry so I could put some system folders on my data drive and have the OS point to them (Tweak UI made that a whole lot easier when XP hit). Anyway, what I wound up with was a machine where my data was completely independent from my OS (and programs). So if my machine ever got really sluggish, a service pack got released or if I needed to update 6 or more programs on my machine, rather than waste time uninstalling everything or running cleanup tools I'd just reformat my OS partition to ensure a squeaky clean OS with he latest software.

So basically I was able to reinstall my OS whenever I wanted without harming any of my data or folder structures. Later on I learned to use programs like Norton Ghost and Acronis True Image to build an image of my clean install which even further reduced my downtime. Since (like Aysiu said) Ubuntu releases come on a fairly regular basis (I think Edgy is due this October) I figured it would be smart to adopt a similar strategy on my Linux box. Form what I understand many of the perks of a new Ubuntu release can only be seen during a clean install, and I don’t want to miss out on anything!

I hope that answers your question.

---

### Post by user1397 on 2006-06-19
[quote=ZeusABJ]I hope that answers your question.[/quote]it certainly does.

---

### Post by jason.b.c on 2006-06-19
> My avatar is David Tennant, the current incarnation of Doctor Who, protagonist of the best Sci-Fi show ever!!!! Check it out:

I'll bet that the next season of that show is going to suck, They got rid of the first guy and now this whole new guy to play the part of the doctor..

I dunno..I think it's a real cool show too , I just have a bad feeling about it now..#-o

---

### Post by ZeusABJ on 2006-06-20
[QUOTE=jason.b.c]I'll bet that the next season of that show is going to suck, They got rid of the first guy and now this whole new guy to play the part of the doctor..

I dunno..I think it's a real cool show too , I just have a bad feeling about it now..#-o[/QUOTE]

HAHAHAHA, sorry to laugh but there have been a total of **10** actors to play the Doctor throughout the show's history. You see whenever a Timelord is severely injured he "regenerates" into a new body. That way when an actor decides to move on its easy to replace him on the show. In fact it may surprise you to know that many people consider the FOURTH actor to play the Doctor to be the absolute best portrayal of the character. So don't be too upset that the lead was recast. In the case of Doctor Who it can often be an improvement! I have seen eight episodes from the new season and I can assure you the "new guy" does an excellent job. In my opinion he's much better than the previous actor (Christopher Eccleston) but thats like comparing apples and oranges. It is still a cool show my friend!

---

