---
title: "Why /home on a seperate partition?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Kyzon on 2006-05-31
I've got a 40 and 160 gig hard drive and i was wondering, what are the benefits of having the /home directory on another partition? Is it just that i'll be able to recover data if it is ever lost?

---

### Post by Master Shake on 2006-05-31
Pretty much.  That way if you have to reinstall your OS, your personal data is unscathed.

I didn't do this on my first few installs, but I swear by it now.

---

### Post by mostwanted on 2006-05-31
You should be able to reuse your settings (saved to your home dir) and keep your documents if you decide to repartition / and reinstall the OS.

---

### Post by Jagot on 2006-05-31
Primarily yes.  If you manage to kill your / partition then you can reinstall the operating system without losing the data.  Some people also share a /home partition between different distros also, but can cause problems with config files.

---

### Post by Sef on 2006-05-31
> I've got a 40 and 160 gig hard drive and i was wondering, what are the benefits of having the /home directory on another partition? Is it just that i'll be able to recover data if it is ever lost?


If you need to reinstall Ubuntu, you won't lose your data.  Ubuntu installs to root and your data is saved to home.

---

### Post by Gustav on 2006-05-31
I began my GNU/Linux experience with Mandrake 9.0. Then I got Mandrake 9.2, Mandrake 10, Debian, Ubuntu Warty, Hoary and then Breezy.

I still have the same /home partition that I had with the first Mandrake. I've never reformatted it.

---

### Post by Kyzon on 2006-05-31
Alright, thanks. But doesnt that mean i also wont be able to write to my 40gig? Or is there any reasoning behing that?

---

### Post by mostwanted on 2006-05-31
[QUOTE=Kyzon]Alright, thanks. But doesnt that mean i also wont be able to write to my 40gig? Or is there any reasoning behing that?[/QUOTE]

I'm not sure what you mean?

---

### Post by ComplexNumber on 2006-05-31
[quote=Kyzon]Alright, thanks. But doesnt that mean i also wont be able to write to my 40gig? Or is there any reasoning behing that?[/quote]
i don't quite understand what you mean.

---

### Post by hotbrainz on 2006-05-31
You cant directly write anything to the / partition  being in the normal user status ( if thats what u mean). You will have to become a root user. If am going in the rite direction tell me and i can provide further help :)

---

### Post by Kyzon on 2006-05-31
[QUOTE=hotbrainz]You cant directly write anything to the / partition  being in the normal user status ( if thats what u mean). You will have to become a root user. If am going in the rite direction tell me and i can provide further help :)[/QUOTE]

Yeah, thats what i mean. Is it recommended that I leave it as is and just use the 160gig for storing data? I just dont want 35 gigs of free space lying around knowing thas I can use it.

---

### Post by Pugaciov on 2006-05-31
I also have /home on a separate partition; what I would like to know is: when I'll format the / partition and install Linux again, for example the official Dapper instead of the Beta 2 I'm currently using, all the software automatically recognize my profiles (Firefox, Thunderbird ecc.)?

Cheers

---

### Post by Gustav on 2006-05-31
[QUOTE=Pugaciov]I also have /home on a separate partition; what I would like to know is: when I'll format the / partition and install Linux again, for example the official Dapper instead of the Beta 2 I'm currently using, all the software automatically recognize my profiles (Firefox, Thunderbird ecc.)?

Cheers[/QUOTE]
Yes, it will work.

---

### Post by ComplexNumber on 2006-05-31
[quote=Kyzon]Yeah, thats what i mean. Is it recommended that I leave it as is and just use the 160gig for storing data? I just dont want 35 gigs of free space lying around knowing thas I can use it.[/quote] you say you're going to leave it as it is. well, how is it at the moment? do you mean that you're not going to have a  seperate partition for /home. i seriously recommend that you have a separate /home partition.

---

### Post by Pugaciov on 2006-05-31
[QUOTE=Gustav]Yes, it will work.[/QUOTE]

Great! And thank you ;)

---

### Post by Gustav on 2006-05-31
[QUOTE=Kyzon]Yeah, thats what i mean. Is it recommended that I leave it as is and just use the 160gig for storing data? I just dont want 35 gigs of free space lying around knowing thas I can use it.[/QUOTE]
You can always partition your 40GB disc and mount the part you don't want as / somewhere else (like /home/kozon/media or something like that). It's not very pretty but at least the space won't be wasted.

---

### Post by ComplexNumber on 2006-05-31
[B]
kyzon[/B]
use the 160 for root aprtition and use your 40 as your /home. you don't have to use all of the 40 M for the /home aprtition. because the /home partition doesn't have to be permanantly mounted like the / partiton does, you can easily resize the /home partition as and when required. just remember that, before resizing, you MUST unmount that partition.

---

### Post by hotbrainz on 2006-05-31
Hey Kyzon,

35 meg is quite a lot. But no worries, You can install a lot of software :)
Now if you do want to put data there (not recommended), i think it is not easy through the command line. The easy way will be by getting to the root user status in graphical interface. If you are using gnome it is:

gksudo nautilus

if using kde, then it is :

kdesu Konqueror

But do remember, once you enter this mode. You can copy, cut delete anything anywhere. So beware. 
My advice - Create a folder in the ? partition and then move in stuff which you are not gonna edit ( like a safe storage box :) )

---

### Post by Gustav on 2006-05-31
[QUOTE=ComplexNumber][B]
kyzon[/B]
use the 160 for root aprtition and use your 40 as your /home. you don't have to use all of the 40 M for the /home aprtition. because the /home partition doesn't have to be permanantly mounted like the / partiton does, you can easily resize the /home partition as and when required. just remember that, before resizing, you MUST unmount that partition.[/QUOTE]
Why use the 160GB disc as / partition? You just need about 8GB for that.

I think the best way is to make a 10GB partition on the 40GB disc as / and use the whole 160GB disc as /home. Then you can mount the remaining 30GB of the first disc somewhere inside the /home.

There might be better ways to do it but to me (I might be wrong) that seems as the best way.

---

### Post by hotbrainz on 2006-05-31
The best thing you can do would be to format and then allocate 10 gig to root and then use the rest for data. 

I know this is a lot of work but saves u from later headaches innit!

---

### Post by ComplexNumber on 2006-05-31
[quote=Gustav]Why use the 160GB disc as / partition? You just need about 8GB for that.

I think the best way is to make a 10GB partition on the 40GB disc as / and use the whole 160GB disc as /home. Then you can mount the remaining 30GB of the first disc somewhere inside the /home.

There might be better ways to do it but to me (I might be wrong) that seems as the best way.[/quote]
i kinda wondered that. 40GB is more than ample for anyone's needs, i would have thought. everyone seems to have  4,890 zillion bytes on their hard drives these days but i can't see any reason why :confused:. there's 40GB in total on mine, and thats used for 1 very full linux distro(ie fedora), 1 windows isntallation which is just used for running VS, and about 15GB of free space. i can only assume that the OP wants to store masses and masses of mp3's and videos or something that potentially require lots of space.

---

### Post by Kyzon on 2006-05-31
Thanks for the help, i think i might try out a couple of the options that were reccomended and see which one will work best. Oh, and the 160 gig is basically going to be backups for family videos and images. I was planning on setting up my pc as a server where the whole family can give me their collection of their vids/pics and i can makie it accessible to them via web if they ever needed access to the material for one reason or another.

---

