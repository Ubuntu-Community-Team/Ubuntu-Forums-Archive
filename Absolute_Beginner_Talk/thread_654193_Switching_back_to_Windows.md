---
title: "Switching back to Windows"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by ma_prism on 2007-12-30
I'm having way too many problems with Ubuntu, so I would like to switch back to windows.

So I insert the cd, format, and everything, and now when it has to restart to continue installing it stays at the boot screen and doesn't go anywhere.

How do I fix this?

Ubuntu messed up my computer plenty.

And please, no trying to keep me on Ubuntu, it's just really not compatible with my computer and me.

---

### Post by JoshuaRL on 2007-12-30
You have angered the Linux gods and must pay the price.

Nah, just kidding.  I think everyone understands that some things just aren't for some people.

Try going into the BIOS setup and change boot order to CD first.

But we'd love to have you back . . .

---

### Post by ma_prism on 2007-12-30
> **JoshuaRL said:**
> You have angered the Linux gods and must pay the price.

Nah, just kidding.  I think everyone understands that some things just aren't for some people.
[B]
Try going into the BIOS setup and change boot order to CD first.[/B]

But we'd love to have you back . . .

Way ahead of you, it's always been CD first... Doesn't change anything.

---

### Post by oldb0y on 2007-12-30
Hmm... I had a bit of trouble understanding your post. 
Is it the Windows-cd that won't boot?

---

### Post by r4ik on 2007-12-30
Did you try Mint ? Linux is always the better alternative.

---

### Post by ma_prism on 2007-12-30
> **oldb0y said:**
> Hmm... I had a bit of trouble understanding your post. 
Is it the Windows-cd that won't boot?

No it boots and installs, and then when the computer restarts to finish installing, it doesnt finish and just stays at the boot screen without continuing.

---

### Post by r4ik on 2007-12-30
-

---

### Post by JoshuaRL on 2007-12-30
Well then I think it may either be the Windows CD or your HD.  Can you try a memory check from the BIOS?

I hate to say this, but you may be barking up the wrong tree.  I'm sure we'll help all you can, but our expertise come in Linux shades.  You might try either Microsoft themself or the original equipment manufacturer.

---

### Post by louieb on 2007-12-30
If your dual booting now, or did until you deleted Linux  You got to replace Grub with the winddows boot loader -  heres how. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by bwtranch on 2007-12-30
I don't understand your question, either. You just put in the WIN CD and if your BIOS is set to boot CD first, then it wipes out everything and starts over. You don't have to format anything. You'll have to give it the 16 digit key stamped on the CD so it makes sure you're not a pirate and the software is recognized by MS as being authentic. Should be no prob, unless it was pirated software in the first place.

---

### Post by ma_prism on 2007-12-30
My CD is genuine.
My HD is perfectly fine.
Memory is perfectly fine.


I deleted the partitions with ubuntu on them, and installed Vista (only temporary untill I buy a new XP CD) and vista installs, then restarts the computer to start up, and it just freezes at the boot screen.

Man this is crazy.

---

### Post by JoshuaRL on 2007-12-30
Ooooh.  May be Vista.  I tried that on a laptop that should have run it and it stalled every time with no error message.

---

### Post by jken146 on 2007-12-30
If you have formatted your hard disk then this cannot be an Ubuntu problem.  It is either a hardware or a Windows problem.

---

### Post by ma_prism on 2007-12-30
> **JoshuaRL said:**
> Ooooh.  May be Vista.  I tried that on a laptop that should have run it and it stalled every time with no error message.

I doubt it's vista, it does the same thing when I try to instal XP

---

### Post by ma_prism on 2007-12-30
> **jken146 said:**
> If you have formatted your hard disk then this cannot be an Ubuntu problem.  It is either a hardware or a Windows problem.

I haven't formated the whole disk. I have 50gigs of music and photography that I can't delete... Because as you can imagine,that's a lot of music.

But I never changed that music partition, nor did I assosiate it with Ubuntu...

I deleted the partitions that were associated with Ubuntu, reformated, instaled, and now I get this problem.

I never had these problems before.

---

### Post by jken146 on 2007-12-30
Well, that's effectively the same thing.  No trace of Ubuntu left.

If it were me I would check the disk itself for defects.

---

### Post by ma_prism on 2007-12-30
> **jken146 said:**
> Well, that's effectively the same thing.  No trace of Ubuntu left.

If it were me I would check the disk itself for defects.


It's a new disk.


Ugh I think this would be easier to get it professionally fixed.

---

### Post by JoshuaRL on 2007-12-30
I know this is gonna sound like someone getting last digs in, but I agree with jken146 that this probably isn't an issue caused by Ubuntu.

But I am sorry nonetheless.

---

### Post by Moop on 2007-12-30
Try using a bootable Super Grub cd to fix your windows mbr. You could also try using the XP cd and entering the recovery console and run fixmbr. I don't know about vista.

Not sure if that will work but it's worth a shot.

---

### Post by jken146 on 2007-12-30
> **JoshuaRL said:**
> I know this is gonna sound like someone getting last digs in, but I agree with jken146 that this probably isn't an issue caused by Ubuntu.

But I am sorry nonetheless.

Yeah, I'm sorry too that Ubuntu didn't work out for you.

It's just occurred to me that Moop may be onto something -- I'm not entirely sure what Windows does to the MBR during install... it did some funny things to me quite recently.

---

### Post by eolson on 2007-12-30
Something isn't right (something you didn't know).   I've installed and uninstalled XP and Ubuntu numerous times on my test machine (I like playing around with different stuff)  and it has never given me a problem either way.  Even removing one from a dual boot has not caused problems.

---

### Post by PilotJLR on 2007-12-30
I have seen this with XP and Vista before.

Once in a while (ie I can't reliably reproduce it) XP and Vista get confused as partitions and MBR's come and go. Wiping the drive fixes the problem, in this event.

By wipe, I mean wipe every bit, not just delete the partition table.
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

DBAN can sanitize the drive. Be advised, this is a slow process... I usually start a three-pass sanitization in the evening, then come back in the morning.


Of course, this may not be related to your problem. But I can say I've experienced your symptoms, and this sometimes solves it.

---

### Post by ^rooker on 2007-12-30
I can confirm PilotJLR's experiences.
Every now and then Windows installation pukes on the MBR of the disk - Back in Win98 times one could simply boot from a Win98 floppy and do a:

"fdisk /mbr"

...but unfortunately, I have no clue how to do that with XP/Vista.

---

### Post by Saint Angeles on 2007-12-30
installing windows is more dificult than installing ubuntu.

ubuntu CANT screw up your hardware. ubuntu is what we humans call "software"

YOU screwed it up.

why dont you take your whining *** over to a windows support site for your retarded question?

oh wait i forgot, windows support is crap.

---

### Post by JoshuaRL on 2007-12-30
I apologise on behalf of the entire Linux community.  Most of us try to be accepting.

Please, less religion and more maturity.

---

### Post by nonewmsgs on 2007-12-30
> **Saint Angeles said:**
> installing windows is more dificult than installing ubuntu.

ubuntu CANT screw up your hardware. ubuntu is what we humans call "software"

YOU screwed it up.

why dont you take your whining *** over to a windows support site for your retarded question?

oh wait i forgot, windows support is crap.

saint it isn't that i don't agree with you, but some people have to learn things like that on their own.  i know that you are defending the OS we all love, but the back to windows posts are so common that you just have to shrug your shoulders and wave goodbye.  many new users are coming but for some there is simply too much to learn and that grass sure was greener on the other side.

---

### Post by Saint Angeles on 2007-12-30
> **JoshuaRL said:**
> I apologise on behalf of the entire Linux community.  Most of us try to be accepting.

Please, less religion and more maturity.
don't you dare apologize on my behalf. worry about yourself. you consider yourself to be some kind of linux ambassador to the nations?

wow you are very full of yourself. less religion? HAH. more maturity? HAH.

what you are saying is that you consider yourself an extremely important source of knowledge on the subject and its your burden to make sure we all know.

why don't you grow up?

---

### Post by Saint Angeles on 2007-12-30
> **nonewmsgs said:**
> saint it isn't that i don't agree with you, but some people have to learn things like that on their own.  i know that you are defending the OS we all love, but the back to windows posts are so common that you just have to shrug your shoulders and wave goodbye.  many new users are coming but for some there is simply too much to learn and that grass sure was greener on the other side.
i understand...

what i meant is he needs to stop asking linux users how to install his windows.

he should ask windows users.

---

### Post by ckr on 2007-12-30
You will need to boot again from the XP disc.  During the first few screens prior to installation, choose the repair option to get to the recovery console.  Then, I think the commands you would need to run are fixboot and fixmbr.  (Type "help" at the prompt to see your options, and I think typing a "/?" after each command will explain it somewhat.  After that, see if the installation will continue by letting the computer boot from the hard drive.  Chances are it will, but you may need to start the installation over from the beginning.

Good luck.


And ignore the rude post earlier.  Linux and Windows differ in how they see drive geometries at times, though it's gotten much better the last few years.    I've run into your issue myself in the past.  Grub sometimes doesn't like to let itself get removed by the Windows installer.  Go figure!:)

---

### Post by nonewmsgs on 2007-12-30
if someone has the guts to try it, shouldn't we at least put them back on the right track even if he wants it back the old way?  he may be back, and i appriciate him giving it a shot.

---

### Post by JoshuaRL on 2007-12-30
First of all, let's not degenerate into a flame war.

Look dude, I don't set myself up as any kind of expert or ambassador.  But I know how to talk to people in a respectful way.  No matter what you or I or anyone else wants to believe, Ubuntu isn't the only choice.  I feel it's the best by far, but that's just my opinion.  And to be fair, I agree with everything you said.  And yet, there are some people who know and understand windows and just would straight up faint if forced to switch.  So letting people follow their own path is the best choice.

I don't like preachy posts, so I'll leave it at this:

**SHE SAID IN THE FIRST POST TO NOT TRY TO MAKE HER CHANGE HER MIND**.  So if you're not willing or capable of doing that, please just leave it alone.  Because you're not winning any fans.

---

### Post by Saint Angeles on 2007-12-30
> **JoshuaRL said:**
> 
**SHE SAID IN THE FIRST POST TO NOT TRY TO MAKE HER CHANGE HER MIND**.  So if you're not willing or capable of doing that, please just leave it alone.  Because you're not winning any fans.
like i said earlier... 
ask ubuntu users how to install ubuntu...
ask windows users how to install windows

and when people blast ubuntu for "breaking their computer" i have to make sure that know that THEY broke their computer (with a little help from the windows virus).

"not winning any fans"? - look at my thanks and compare to yours

you're terrible at debating

---

### Post by eolson on 2007-12-30
A very wise old Master Chief once told me that some things are best left alone.

---

### Post by JoshuaRL on 2007-12-30
I know eolson.  I'm done.  I've got enough stress in RL.

---

### Post by bwtranch on 2008-01-01
I consider this thread closed and solved.

---

