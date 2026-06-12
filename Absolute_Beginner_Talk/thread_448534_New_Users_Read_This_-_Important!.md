---
title: "New Users Read This - Important!"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by LukeCarrier on 2007-05-19
If you haven't already chosen which version of Ubuntu to download, please use 6.06, as it is the only version of this crap operating system which actually works. I used to like Ubuntu until if ****** up my entire system, now I hope the project gets closed for being a complete waste of time and money.

---

### Post by BHelts on 2007-05-19
the juxtaposition of what you say here and your signature is very interesting.  what happened?

---

### Post by bchaffin72 on 2007-05-19
Did it really **** up your entire system, or did you? I use 6.10. Works like a charm. Be more specific.

---

### Post by chamberlain2006 on 2007-05-19
Excuse me?  If you need some help, we're happy to help you, but don't come on these forums to attack us.  Sure there are problems, but there are with any operating system or piece of software.  Ubuntu is a great project that helps a lot of people not have to pay for a proprietary operating system, and get rid of Windows.  If you don't like it, then install Windows.  DON'T yell and swear at us.  If you want some help, I'd be happy to help out.

---

### Post by LukeCarrier on 2007-05-19
I upgraded to the bloody 6.10 then to 7.04 and the thing refused to start. Ever since then Grub has been broke, and Ubuntu fails every install. It sucks. I'm going back to Windows, its way more reliable than this horrible loada junk.

---

### Post by taurus on 2007-05-19
I think this thread should be locked before it gets out of hand.

p.s.  Instead of upgrading from 6.06 to 6.10 to 7.04, what if you install 7.04 from fresh?

---

### Post by chamberlain2006 on 2007-05-19
Definately taurus.

---

### Post by heimo on 2007-05-19
> **LukeCarrier said:**
> I upgraded to the bloody 6.10 then to 7.04 and the thing refused to start. Ever since then Grub has been broke, and Ubuntu fails every install. It sucks. I'm going back to Windows, its way more reliable than this horrible loada junk.

Yes please. That's much better idea than trolling. And now - everyone, please ignore this troll until forum staff handles this. Criticism is ok, baseless junk with violations against forum policies isn't.

---

### Post by LukeCarrier on 2007-05-19
do what you like, i ent installing ubuntu again. windows might suck...a lot...but at least it works!

---

### Post by LukeCarrier on 2007-05-19
And taurus - i tried that and the system doesn't boot, i can't install any version of ubuntu now, and i don't want to anyway

sorry, but i'm sick of always fixing problems with ubuntu and never having time to actually use it

---

### Post by MetalMusicAddict on 2007-05-19
Yes! Another satisfied customer! :)

---

### Post by Najand on 2007-05-19
I think this thread is against the backyard rules: [http://ubuntuforums.org/rules.php](http://ubuntuforums.org/rules.php)
A lock is needed here. Tuarus, you have the power to do so, don't you?

---

### Post by taurus on 2007-05-19
If you need help to fix it, you should at least describe what the problem is.  Then, the spec of your machine would be nice too.

I am sure there is a way to get Feisty running on your machine if Dapper runs fine on it.  Otherwise, stay with Dapper since it's a long term support release.

---

### Post by spacegypsy on 2007-05-19
Before having 7.04 I had 6.06.

But I didn't upgrade.

Just did a fresh installation.

And everything is working properly even better then in 6.06.

---

### Post by enopepsoo on 2007-05-19
The only weird trouble I've ever had with installing is that I can't have my ide drive plugged in until the install is done, or else I will get GRUB errors.

You sounds pretty frustrated! :lolflag:

---

### Post by tchoklat on 2007-05-19
go away loser!

---

### Post by taurus on 2007-05-19
> **Najand said:**
> 
A lock is needed here. Tuarus, you have the power to do so, don't you?

Yes, I do but let's see if we can help him first.  Don't want to jump the gun here.

---

### Post by Najand on 2007-05-19
> **LukeCarrier said:**
> And taurus - i tried that and the system doesn't boot, i can't install any version of ubuntu now, and i don't want to anyway

sorry, but i'm sick of always fixing problems with ubuntu and never having time to actually use it

If you have problem with grub, it is not very difficult to fix it.

---

### Post by LukeCarrier on 2007-05-19
Right, heres the problem that I've been trying to fix for three weeks:

Every time i boot my system using ubuntu 7.04 i get the grub error 22 problem, and if i add the /boot partition during setup everything is slow. it doesn't work, i've spoken to everyone i know who uses grub / linux and none of them no. i even spoke to the tech staff at school, taking my pc there and it didn't work. i'm sick of it.

---

### Post by chamberlain2006 on 2007-05-19
Have you tried reinstalling it from the CD, and running the CD test?

---

### Post by Najand on 2007-05-19
As far as I know, Grub error 22 is "Must load Multiboot kernel before modules"
This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.

---

### Post by LukeCarrier on 2007-05-19
the cd test being the 'check cd for defects' or another one? i don't look at anything on the cd apart from the install icon on the desktop.

---

### Post by MetalMusicAddict on 2007-05-19
Have you created a existing thread about this? If not It should be done and this one closed.

---

### Post by LukeCarrier on 2007-05-19
Najand:

Can you explain this a little more simply? I'm new to linux and don't have the foggiest about what you're talking about, necause Windows does everything in the background.

---

### Post by Najand on 2007-05-19
Can you start inux by using live CD? If so, can you post the output of the following commands:
```

sudo fdisk -l
cat /boot/grub/menu.lst

```

---

### Post by bchaffin72 on 2007-05-19
It's also important to know if the system being upgraded has used only standard repositories and install methods. I have heard that using non-standrad repositories and installing software your own way has broken upgrades. I don't use non-standard repos, but have installed my own software from source, so I figure my upcoming move to 7.04 will take a little more planning than the norm.

---

### Post by taurus on 2007-05-19
> **Najand said:**
> Can you start inux by using live CD? If so, can you post the output of the following commands:
```

sudo fdisk -l
cat /boot/grub/menu.lst

```

I am not sure if the second command helps since it will look on the LiveCD instead of the harddrive.  You want to look at menu.lst on the harddrive, right?

---

### Post by Najand on 2007-05-19
> **taurus said:**
> I am not sure if the second command helps since it will look on the LiveCD instead of the harddrive.  You want to look at menu.lst on the harddrive, right?

That is right... He should mount his /boot partition before doing that.... Just post your "sudo fdisk -l" output.

---

### Post by LukeCarrier on 2007-05-19
I don't want to fuss any more. Thanks for trying to help, but I'm sick of all these problems now, and I think I'm going back to Windows because apart from being slow and ugly it does the job, and is easier to work with for me. Delete the thread, sorry for being rude to begin with but I'm really frustrated with all this, and want it to go away. I might try again another time, thanks for trying to help everyone.:(:confused:

---

### Post by bob74 on 2007-05-19
I  had numerous problems with my Feisty after the up-grade and spent countless hours
chasing one snag after another. I had been using Dapper for over six months daily without a glitch.
Having seen several postings I decided to bite on the bullet and wiped the partition and did a fresh install.
Result everything works great apart from fact that the system doesn't recognise my printer
(Epson Stylus Color 740)which was OK originally. If anyone out there can give me concise instructions on how to get it back I would appreciate it( I have tried the usual methods which don't seem to work on this system)
I am very impressed with Ubuntu and it is sad that an upgrade should seem to give so many problems-- perhaps it's me!

---

### Post by Najand on 2007-05-19
> **bob74 said:**
> I  had numerous problems with my Feisty after the up-grade and spent countless hours
chasing one snag after another. I had been using Dapper for over six months daily without a glitch.
Having seen several postings I decided to bite on the bullet and wiped the partition and did a fresh install.
Result everything works great apart from fact that the system doesn't recognise my printer
(Epson Stylus Color 740)which was OK originally. If anyone out there can give me concise instructions on how to get it back I would appreciate it( I have tried the usual methods which don't seem to work on this system)
I am very impressed with Ubuntu and it is sad that an upgrade should seem to give so many problems-- perhaps it's me!

Bob, can you make a separate thread for you problem?

---

### Post by taurus on 2007-05-19
Thread closed.

---

