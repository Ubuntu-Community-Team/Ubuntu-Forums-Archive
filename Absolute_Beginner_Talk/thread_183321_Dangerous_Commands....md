---
title: "Dangerous Commands..."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-27
i was wondering if there are any commands you can type in (accidentally most likely), that would completely screw up your system.
Also, i thought i could type in ```
bin bash
``` and log in as root, but at first it just said "command not found" so i typed in ```
bash
``` but it didn't even say anything, it just went back to "user@ubuntu:~$"
also i typed in ```
yes
``` and a series of y's just went down the terminal, and it wouldnt stop, so i closed it. 
i'm not sure why i typed in these commands (experimentation i guess), but im wondering if they actually did anything?

---

### Post by ejos on 2006-05-27
Your system is fine.

---

### Post by voger on 2006-05-27
Well the "bin bash" command means "Run the command bin with "bash" as parameter". but there is no executable named bin as far as i know so the system replied "bash: bin: command not found" which means "I didn't find any executable file in your path named bin"

The "bash" command simply started another bash shell inside the currently running bash. bash is the command interpreter so you just started a command interpreter inside the command interpreter. I don't know if there is any practical use of this.

As for the yes command :confused: try man yes

Except for wrong usage of rm flags there are no dangerous commands for your system as long as you don't log in as root. 

BTW a good idea is to try man <command> before experimenting with new commands.

---

### Post by user1397 on 2006-05-27
Thank you guys for all the replies, they helped

---

### Post by nalmeth on 2006-05-27
**DON'T TRY THIS**

sudo rm -r /

I would believe this is one of the most fatal command's you could enter. Delete your root filesystem.

---

### Post by skippy81 on 2006-05-27
Beware of the deadly 

DON'T TYPE THIS - I REPEAT NOONE TYPE THIS:> sudo rm -r /

I may have the syntax slightly wrong (i dont use this command much :D but the gist of it is that it will recursively delete your root.  Even without the sudo its still very nasty since it will just avoid your linux system and take down all the media in your home directory instead.   Its actually a lot easier to do this than you think, since you could be deleting multiple directories recursively and accidently add " /" to the end and kill your system.   

After learning that it is impossible to undelete files on anything other than an EXT2 partion, rm has earnt a new found respect from me.

---

### Post by ComplexNumber on 2006-05-27
[quote=skippy81]Beware of the deadly 

DON'T TYPE THIS - I REPEAT NOONE TYPE THIS:
>  			 				sudo rm -r /

[/quote]
oops #-o

---

### Post by Randomskk on 2006-05-27
Eh, rm -rf / isn't as deadly as you'd think.
Sure, all mounted drives - USB, other hard disks, network mounted drives, your iPod, etc, etc get deleted, and don't forget the GRUB 17 error you'll see when you reboot, but the PC is still usable, just don't close any programs.

I know, I've done it :D

It also takes a heck of a long time, so you can usually cancel it quickly.


Another command not to type in would be:
:(){ :|:& };:

---

### Post by skippy81 on 2006-05-27
Sorry nalmeth I really should refresh my browser before I answer a post :)

---

### Post by skippy81 on 2006-05-27
[QUOTE=Randomskk]:(){ :|:& };:[/QUOTE]

Haha I just did it, I didn't think the fork thing would actually work :o  Surely bash should be able to filter it out?  As it was I had to perform my first 'reboot' in a couple of weeks :)

I really don't understand it, is it like a buffer overflow or something? Please enlighten me :)

---

### Post by voger on 2006-05-27
> **Randomskk]
Another command not to type in would be:
[HTML]:(){ :|:& } said:**
> 

Can you please explain what is that? My fingers are itching.

---

### Post by Randomskk on 2006-05-27
It's a forkbomb. I don't understand it much as it is, but the basis is it causes an infinite amount of forks of a program to spawn, thus consuming 100% CPU pretty much instantly, and the computer will lock up.

It's non fatal, you just need a hard reboot.

Perhaps someone who actually understands it could explain it better than me :P

---

### Post by dmizer on 2006-05-27
the "yes" command merely repeats a command until it is cancled.

could be useful ...

---

### Post by skippy81 on 2006-05-27
Wiki for the win it seems:-

[http://en.wikipedia.org/wiki/Fork_bomb]("http://en.wikipedia.org/wiki/Fork_bomb")

I found the MSDOS version particulary amusing :)

---

### Post by uzi09 on 2006-05-27
for those of you who wanted to see what
```
 rm -rf / 
```

does to a linux box, heres a vid:
[http://video.google.com/videoplay?docid=464540691509009245&q=linux](http://video.google.com/videoplay?docid=464540691509009245&q=linux)

ps: with the added 'f' switch it forces the remove so you can really kiss your linux good bye there :D

---

### Post by Randomskk on 2006-05-27
[QUOTE=skippy81]Wiki for the win it seems:-

[http://en.wikipedia.org/wiki/Fork_bomb]("http://en.wikipedia.org/wiki/Fork_bomb")

I found the MSDOS version particulary amusing :)[/QUOTE]


And from your link, here's a detailed explanation of the BASH one I posted:
[http://www.euglug.org/pipermail/euglug/2005-August/004338.html](http://www.euglug.org/pipermail/euglug/2005-August/004338.html)

---

### Post by skippy81 on 2006-05-27
I'm kinda worried now that I might sleepwalk to my computer, do a quick > sudo rm -rf / and then throw in a fork bomb for good measure :p 

Maybe I should change my password to something complicated so I have to actually be concious to use my PC :)

---

### Post by ronlybonly on 2006-05-27
This reminds me of the time that i typed: 

chmod 777 / -R

as root. That was a stupid idea. A VERY stupid idea.

---

### Post by user1397 on 2006-05-27
[quote=ronlybonly]This reminds me of the time that i typed: 

chmod 777 / -R

as root. That was a stupid idea. A VERY stupid idea.[/quote]
well couldnt you just later do "chmod 755 / -R"  i think -R means "and all subfolders" is that correct?

---

### Post by joshrobinson on 2006-05-27
are you TRYING to break your computer erik ;)

---

### Post by joshrobinson on 2006-05-27
[QUOTE=erik1397]well couldnt you just later do "chmod 755 / -R"  i think -R means "and all subfolders" is that correct?[/QUOTE]

yeah -r is for recursive.. it makes the command  you put in apply to the all subfolders like you said

---

### Post by user1397 on 2006-05-27
[quote=joshrobinson]are you TRYING to break your computer erik ;)[/quote]
just a lil bit :mrgreen:

---

### Post by joshrobinson on 2006-05-27
[QUOTE=erik1397]just a lil bit :mrgreen:[/QUOTE]

bad bad [-( i usually break it by accident haha..well not lately

---

### Post by ronlybonly on 2006-05-29
> well couldnt you just later do "chmod 755 / -R" i think -R means "and all subfolders" is that correct?

I guess I could have done something... that is, I could have if I didn't think "Hmm, I wonder if I could fix everything by typing: 'chmod a-rwx / -R'"
Now THAT was a really bad idea :D

---

### Post by IYY on 2006-05-29
The **yes **command is just like the drinking bird in the Simpsons.

---

### Post by Ben Sprinkle on 2006-05-30
lmao  i typed in sudo rm -r / and my coomp is screwed now thanks guys.

---

### Post by Klaidas on 2006-05-30
Well, they said not to type that :)
However, the deadliest command I can think of is like echoing some file to your /dev/hda ;)

---

### Post by vidak on 2006-05-30
what about 
```

cat /dev/urandom > /boot/grub/stage1
<Ctrl-C>
cat /dev/urandom > /boot/vmlinuz-2.6.12-10-686
<Ctrl-C>
cat /dev/urandom > /dev/hda1

```
and go for a coffee break?

---

### Post by Engnome on 2006-05-30
sudo apt-get moo completely destroys your system. :mrgreen:  Especially if you type yes afterwards.](*,)

---

### Post by vidak on 2006-05-30
sure. and so does 
aptitude moo
aptitude moo -v
aptitude moo -v -v
etc
:) don't be afraid, try it...
Check if your aptitude has the power of SuperCow with aptitude help...

---

### Post by mlind on 2006-05-30
I remember I once removed some pretty essential library using **--force** which
is my favourite parameter (reminds me of Start Wars), I think it was glibc or
something similar. After that neat command, nothing worked. Every command I
tried to execute threw out some sort of error.. Ah, memories.

I had to reinstall the whole system.

---

### Post by user1397 on 2006-05-30
[quote=vidak]sure. and so does 
aptitude moo
aptitude moo -v
aptitude moo -v -v
etc
:) don't be afraid, try it...
Check if your aptitude has the power of SuperCow with aptitude help...[/quote]
whoa that's awesome! after this many v's: aptitude moo -v -v -v -v -v -v, it's always the same :mrgreen:

---

### Post by Lord Illidan on 2006-05-30
You want to break your computer, Eric? Let me send you a windows cd!

lol..

I tried out the fork command. Nasty, but a quick, killall bash saved my system, hehe.. no need to do a reboot.

But everything got pretty slow while it was running....I had about 2k processes running on this 2Ghz celeron...poor thing!

---

### Post by Rinzwind on 2006-05-30
Regarding the rm -rf \ command

If you really want to make sure it can't be used make an alias and have the rm command replaced by "echo woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaen".

And have another alias where 
"woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaeng"  to do the rm  :+

The changes of accidently typing woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaen should be 0 :D :D

I really like the fork bomb :D :D Funny

---

### Post by Lord Illidan on 2006-05-30
[quote=Rinzwind]Regarding the rm -rf \ command

If you really want to make sure it can't be used make an alias and have the rm command replaced by "echo woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaen".

And have another alias where 
"woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaeng"  to do the rm  :+

The changes of accidently typing woiefhahewfvkwnsVKLnwaelkngvlwkjaerngljkwaen should be 0 :D :D

I really like the fork bomb :D :D Funny[/quote]

Nice solution for the rm, Rinzwind..

But what if you sleep on the keyboard? And wake up to find....disaster....

---

### Post by Rinzwind on 2006-05-30
Life sometimes sucks anyways so ...

But you could also add some alt-codes in that alias :D those require some fancy typing to do them by accident ;)

---

### Post by Randomskk on 2006-05-30
[QUOTE=Lord Illidan]You want to break your computer, Eric? Let me send you a windows cd!

lol..

I tried out the fork command. Nasty, but a quick, killall bash saved my system, hehe.. no need to do a reboot.

But everything got pretty slow while it was running....I had about 2k processes running on this 2Ghz celeron...poor thing![/QUOTE]

If you leave it for a few seconds more, the system usually gets so unresponsive you can't killall bash :P

---

### Post by Lord Illidan on 2006-05-30
[quote=Randomskk]If you leave it for a few seconds more, the system usually gets so unresponsive you can't killall bash :P[/quote]

I didn't dare:p

---

### Post by vidak on 2006-05-30
dangerous commands? tell your grandma/girlfriend/whatever to clean your machine :) she will surely do it with lots of water...

---

### Post by nocturn on 2006-05-31
[QUOTE=Randomskk]
Another command not to type in would be:
:(){ :|:& };:[/QUOTE]

I can and safely have done so.

I have the number of processes limited on all my machines though 8)

---

### Post by nocturn on 2006-05-31
[QUOTE=skippy81]Haha I just did it, I didn't think the fork thing would actually work :o  Surely bash should be able to filter it out?  As it was I had to perform my first 'reboot' in a couple of weeks :)

I really don't understand it, is it like a buffer overflow or something? Please enlighten me :)[/QUOTE]

This is a forkbomb.  It creates a dummy process which forks and tells each of its children to fork too.
The result is much like cancer, the number of process grows exponentially (not linear) and makes the machine stop responding to handle the forking (not actually crashing it).

You can protect against this though by setting limits on processes/user.

---

### Post by henriquemaia on 2006-05-31
[quote=nocturn]This is a forkbomb.  It creates a dummy process which forks and tells each of its children to fork too.
The result is much like cancer, the number of process grows exponentially (not linear) and makes the machine stop responding to handle the forking (not actually crashing it).

You can protect against this though by setting limits on processes/user.[/quote]

How do you do that limitation? Can be very handy.

---

### Post by nocturn on 2006-05-31
[QUOTE=henriquemaia]How do you do that limitation? Can be very handy.[/QUOTE]

Edit /etc/security/limits.conf

The nproc limits are what you want.  For normal users, a hard limit of 150 is more then enough.

---

### Post by henriquemaia on 2006-05-31
[quote=nocturn]Edit /etc/security/limits.conf

The nproc limits are what you want.  For normal users, a hard limit of 150 is more then enough.[/quote]

Thanks. But this has to be done app based? Or system wide? Can you post an example of a limits.conf?

(mine just has the default examples)

---

### Post by nocturn on 2006-05-31
[QUOTE=henriquemaia]Thanks. But this has to be done app based? Or system wide? Can you post an example of a limits.conf?

(mine just has the default examples)[/QUOTE]

It's user or group based (or it can be set for all users).

*          hard    nproc           1000 
would set it to 1000 processes for all users on a system

@users hard  nproc 150
would set it to 100 for all member of the users group

150 is safe for ordinary users, but root may require a higher number.

---

### Post by henriquemaia on 2006-05-31
[quote=nocturn]It's user or group based (or it can be set for all users).

*          hard    nproc           1000 
would set it to 1000 processes for all users on a system

@users hard  nproc 150
would set it to 100 for all member of the users group

150 is safe for ordinary users, but root may require a higher number.[/quote]

Thanks for providing the examples. Now I get it.

I'm going to test this with the bash fork bomb.

---

### Post by henriquemaia on 2006-05-31
[quote=nocturn]It's user or group based (or it can be set for all users).

*          hard    nproc           1000 
would set it to 1000 processes for all users on a system

@users hard  nproc 150
would set it to 100 for all member of the users group

150 is safe for ordinary users, but root may require a higher number.[/quote]

It worked. Thanks again. 

I had some unsuccessful experiences (2 lockups) before getting the proper configuration. 

Now I get a beautiful 

**bash: fork: Resource temporarily unavailable**

---

### Post by Dr. Nick on 2006-05-31
[quote=IYY]The **yes **command is just like the drinking bird in the Simpsons.[/quote] 
HAha Another Simsons watcher.

Wait, I know: vent gas.
 "Pressure too high?"
 "Tank must be shut down manually?"
Oh, stupid bird!  I never should have put
you in charge!


I need to try out the fork bomb soon

While not dangerous it can be comical.

Type **fortune** into a terminal

> Q:      Why does Washington have the most lawyers per capita and
        New Jersey the most toxic waste dumps?
A:      God gave New Jersey first choice.

---

### Post by Lord Illidan on 2006-05-31
[quote=vidak]dangerous commands? tell your grandma/girlfriend/whatever to clean your machine :) she will surely do it with lots of water...[/quote]

Or try and watercool your machine... put a hosepipe inside and fillerup!

---

### Post by user1397 on 2006-05-31
[quote=Dr. Nick]Type **fortune** into a terminal[/quote]Wow! there are so many fortune outcomes.  i didn't wanna keep on going, but i did like 20 and there were still new ones!  (Surprising isn't it how I'm so willing to try commands that I have no guarantee if they'll break my system or not :mrgreen:)

---

### Post by Klaidas on 2006-05-31
Ooh the fortune command, makes me addicted!
Didn't know about this one. Very cool ;)

---

### Post by user1397 on 2006-06-03
what would the command be (if any) to uninstall part of/all of the kernel itself?

would it be like ```
rm -R linux 2.16.12-i386
```???
lol im not actually gonna do it, and im not a linux kamikaze, im just curious:mrgreen:

---

### Post by Dr. Nick on 2006-06-03
similar to that, I removed some driver modules out of the kernel using this command

rm /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/prism2

so i guess 
rm -R /lib/modules/kernel-version would erase a big ol chunk of the kernel

SO DONT DO IT :) lol

---

### Post by user1397 on 2006-06-03
[quote=Dr. Nick]similar to that, I removed some driver modules out of the kernel using this command

rm /lib/modules/2.6.15-23-386/kernel/drivers/net/wireless/prism2

so i guess 
rm -R /lib/modules/kernel-version would erase a big ol chunk of the kernel

SO DONT DO IT :) lol[/quote] i'm so tempted!!! (not really :D)

---

### Post by u.b.u.n.t.u on 2006-06-03
Re: Dangerous Commands...

"EULA Windows. Tick to accept and install Windows"

That is pretty dangerous :rolleyes:

---

### Post by phoenixy on 2006-06-07
argg, can't believe this just happened to me. A moment of brain freeze and I ended up losing all my admin scripts...

Was setting up a script to copy some files to a user account...

cp files ~user/

ok, that didn't work as intended. I ended up creating a ~user dir at the current dir...

Without 2nd thought... rm ~user

??? ~user still exists on current dir? OH NO...:-? This ain't happening...

So, it did happen on the day when I'm moving my backup server to the new dapper machine, with admin scripts(one and only copy after backup server is down) temp copy over to ~user...

Still ](*,) ](*,) ](*,) ](*,) ](*,) 

And yes, I'm always root while making a million changes to the system. I'm still kicking myself for having such twitchy fingers...:-|

---

