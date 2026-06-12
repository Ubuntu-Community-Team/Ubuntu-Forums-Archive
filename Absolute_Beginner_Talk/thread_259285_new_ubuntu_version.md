---
title: "new ubuntu version"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by cyrano_says on 2006-09-17
i hav been using ubuntu dapper drake for the past few months and absolutely luv it..

i hav a basic question... 

ubuntu comes out with a new version every 6 months..

>>so if we update the os.. dont we have to install all the programs
and configuratins all over again? do all the ppl who try the new os go thru this process of updating all their installations and preferences..

>>if not.. should we just stick with the old one ?? but the old one loses support in the discussion forums and the community in a few months time...after the release of the new version...

---

### Post by xyz on 2006-09-17
Updating does not erase anything.
Also you may want to back up your Ubuntu so as to ba able to restore in case something goes wrong.
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
Don't hesitate to ask question if unclear!

---

### Post by 3rdalbum on 2006-09-17
This is my understanding of it.

If you do a "dist-upgrade", then all updatable programs are updated.

If you use Synaptic to just update "ubuntu-desktop", then your existing programs are not updated unless they are referenced by ubuntu-desktop.

But somebody please correct me if I'm wrong about this.

---

### Post by xpod on 2006-09-17
I`d like to know for sure too.I asked back when i first arrived but still was`nt too much clearer i think.
 WILL i just be able to do the "dist-upgrade" thing when the next release comes out or whatever other commands it might take?
I dont have the separate home partition and aint got nothing im worried about but how exactly should i upgrade?...I thought merely by getting all the updates as they appear that i would have the latest???

---

### Post by Dinerty on 2006-09-17
Intresting question.

If one had xgl/compiz installed and did a dist-upgrade from dapper to edgy , would xgl/compiz be affected?

---

### Post by cyrano_says on 2006-09-17
so to do this dist-upgrade..
we insert the live cd .. and chose the upgrade option and 
ur current version gets updated to the new version but all ur programs 
and others configurations stay put..

do we hav to use apt-get or synaptic to do the upgrade or we have to use the live cd to do it ?

if so how do we go abt it ?

hmm tats cool..

---

### Post by bulldog on 2006-09-17
I think you need the Edgy repositories at least to upgrade.

Otherwise the upgrading will take a short time :p

---

### Post by xpod on 2006-09-17
SO i wont need to get any new iso?
I`t can all be done from here....
In fact THEN might be a good time for me to do it all again but with the separate "home" partition.

---

### Post by bulldog on 2006-09-17
> **xpod said:**
> SO i wont need to get any new iso?
I`t can all be done from here....
In fact THEN might be a good time for me to do it all again but with the separate "home" partition.

For a separate /home you need to make new partitions.

Updating to Edgy won't do that for you.](*,)

---

### Post by whizbaby on 2006-09-17
Hey, adventurers out there:
remember to do a backup of your (whole) existing installation before doing dist-upgrades so you don't screw your system by doing it (learned this behaviour doing years of debian work and I think it applies to any dist (just keep past xorg-xserver update in mind, anything can happen)).

---

### Post by bulldog on 2006-09-17
Thanks for the warning.

I myself have no planning to upgrade to Edgy or what ever.

Dapper is enough for the time being,and if Edgy comes stable,I'll try it in a virtual machine to take a look first.

---

### Post by deadgobby on 2006-09-17
When Edgy does come out, I hope i do not need to reload all the codecs again. Up grade from breezy to draper, it lost all the codecs.
Gobby

---

### Post by xpod on 2006-09-17
> 
For a separate /home you need to make new partitions.

Updating to Edgy won't do that for you.

I KNOW that mate...I just mean that when the new release is actually out on an iso THEN would be a good idea for me to start over...OBVIOUSLY by doing my partitions again...:biggrin: 

I might come across as a wee bit daft at times mate but im not THAT daft:-\"

---

### Post by bulldog on 2006-09-17
> **xpod said:**
> I KNOW that mate...I just mean that when the new release is actually out on an iso THEN would be a good idea for me to start over...OBVIOUSLY by doing my partitions again...:biggrin: 

I might come across as a wee bit daft at times mate but im not THAT daft:-\"

You could have fooled me.....:biggrin: :biggrin:

---

### Post by xpod on 2006-09-17
Right...wheres that m.e!!=D> :biggrin:

---

### Post by DOD1951 on 2006-09-17
Backing up the system is mentioned several times. Does anyone know how to backup Ubuntu? I have been trying to find a backup program utility but cannot find one that actualy works!

---

### Post by bulldog on 2006-09-17
In automatix is a backup utility what can be installed for you.

It makes a backup of my file every friday at six.

I never put one back however,I don't know if that works,but backup works exellent.

---

### Post by whizbaby on 2006-09-17
rsync does that job (and a couple of others) quite well. (man rsync)
If your backup HD is mounted on let's say /media/backup 
**rsync -azvx / /media/backup**
(the option x will prevent rsync from recursing into other HD's)

---

### Post by xyz on 2006-09-17
> **DOD1951 said:**
> Backing up the system is mentioned several times. Does anyone know how to backup Ubuntu? I have been trying to find a backup program utility but cannot find one that actualy works!
There are many ways to do it; here are a couple of them:

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive](http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
I used GParted Boot CD to back up Windows.
Hope it helps!

---

### Post by rhomp2002 on 2006-09-17
I would like to know how to do the upgrade also.  Now that there is a release Dapper 6.06.1 which is an upgrade of the original Dapper, how do we upgrade to that?  Has it been released for upgrade yet or do we have to download or get the CD's from Canonical?  It apparently has a lot of good stuff upgraded so I would like to apply it but also do not want to lose what I already have.](*,) ](*,)

---

### Post by cyrano_says on 2006-09-18
I would like to find out also...

ubuntu has great faqs on a lot of stuff 
and if someone could put a faq on how to backup/update ur distro.. that would be great..

i havnt seen one yet and it wud be very helpful...

few questions that need addressing would be :

> do we need to a new iso image or can we do it off the repos..
> how do we go abt making a partition... and what do we have to backup. 
> incase of crashes.. how do we restore to our old os ??

are there any other q's that ppl can think of ?

---

### Post by bulldog on 2006-09-18
> **cyrano_says said:**
> I would like to find out also...

ubuntu has great faqs on a lot of stuff 
and if someone could put a faq on how to backup/update ur distro.. that would be great..

i havnt seen one yet and it wud be very helpful...

few questions that need addressing would be :

> do we need to a new iso image or can we do it off the repos..
> how do we go abt making a partition... and what do we have to backup. 
> incase of crashes.. how do we restore to our old os ??

are there any other q's that ppl can think of ?

Well, I only can hope,might somebody takes the time and efford to write such a HowTo,he or she won't write like you.:lol: 

If possible,make whole words,it's far more easy to read and understand.

Words like  q's and ppl give me a head ache.

Thanks in advance :biggrin:

---

### Post by Odinist on 2006-09-18
HOWTO on upgrading from version to version:
[http://ubuntuguide.org/wiki/Dapper#Upgrading_Ubuntu]("http://ubuntuguide.org/wiki/Dapper#Upgrading_Ubuntu")

Oh, and as for Dapper support going away in a few months...

"Release 6.06 is labelled Long Term Support (LTS) to indicate that Canonical intend to support it with updates for longer than most Ubuntu releases. Package updates are planned for three years on the desktop and five years on the server, with paid technical support available from Canonical over the same period."

[http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Releases]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Releases")

---

### Post by ADH on 2006-09-18
How would I update to 6.06?  I have 5.10, which is what I installed that killed my master drive by placing Grub on it, rather than on the slave drive where I told Ubuntu to install everything (and everything but Grub is on the slave drive.)  Is updating simple, and done by the OS?

---

### Post by bulldog on 2006-09-18
If you want GRUB on your slave drive,that's not so hard to do.

I know that it's a bug that Ubuntu don't ask you where to put GRUB,but it's to fix. 
Just let me know.:)

---

### Post by Odinist on 2006-09-18
> **ADH said:**
> How would I update to 6.06?  I have 5.10, which is what I installed that killed my master drive by placing Grub on it, rather than on the slave drive where I told Ubuntu to install everything (and everything but Grub is on the slave drive.)  Is updating simple, and done by the OS?

Check that first link I posted above you...


Essentially, you change your sources.list to reflect the 6.06 repositories in lieu of the 5.10 repositories, then you run "sudo apt-get update" followed by "sudo apt-get upgrade" and finally "sudo apt-get dist-upgrade".

---

