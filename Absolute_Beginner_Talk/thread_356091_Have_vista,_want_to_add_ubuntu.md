---
title: "Have vista, want to add ubuntu"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by havedampton on 2007-02-08
I am VERY new to the ubuntu world so I apologize in advance.

I was just given a laptop with vista and would like to add ubuntu as a second OS.  I've searched for instructions, but all I found are upgrading to vista and adding ubuntu at the same time.  I haven't been able to find anything that tells me (in my utter and complete ignorance) a step by step way to add ubuntu to a machine that ALREADY has vista.  I saw several things that led me to believe that re-partitioning after vista was installed would not be possible (or at least not easy)????

Any help would of course be greatly appreciated.

ANYONE STUCK LIKE ME BE SURE TO READ PAGE 2!!!!

---

### Post by cw1925 on 2007-02-08
> **havedampton said:**
> I am VERY new to the ubuntu world so I apologize in advance.

I was just given a laptop with vista and would like to add ubuntu as a second OS.  I've searched for instructions, but all I found are upgrading to vista and adding ubuntu at the same time.  I haven't been able to find anything that tells me (in my utter and complete ignorance) a step by step way to add ubuntu to a machine that ALREADY has vista.  I saw several things that led me to believe that re-partitioning after vista was installed would not be possible (or at least not easy)????

Any help would of course be greatly appreciated.I think it's that retarded "Protected Environment" DRM that they put on it that's disallowing you to partition.  I could be wrong though.  If that's the case, then somewhere in the EULA you agreed to, it's clearly stated there.  Bad move on Vista's front.  It's like "do you agree for Vista to have complete control over the your machine?"  I don't understand why they need complete control over a piece of machinery.

---

### Post by shoaibi on 2007-02-08
No no, i would suggest just creating a 5gb partitions, FAT or NTFS doesn't matter AFAIK, and install VMware on system i.e. on Vista, on C:\Program Files
and you can use VMware to install Ubuntu and use it.
I you need any more help please search using VMware on Google Videos, they have it all...... i learnt from there....

EDIT:
OR
empty a 5GB drive and do as suggested...

---

### Post by havedampton on 2007-02-08
I haven't actually tried anything yet (just to clarify), so I don't really know that I'll have a problem partitioning (other than the fact that I have no idea how to actually do that.)  I just saw something that mentioned vista not liking to be partitioned.  

As I said, I am very new to all of this.  I just really want to move toward not using anything produced by microsoft if I don't absolutely have to.

Thanks for your concern in my utterly pathetic state of ignorance.

---

### Post by hungrybuddha on 2007-02-08
i believe you must check for unused disk space.... new laptop, bet on it.

try this first:

[http://www.tweakvista.com/Article38991.aspx](http://www.tweakvista.com/Article38991.aspx)

let us know what ya got...

---

### Post by shoaibi on 2007-02-08
havedampton don't panic everybody is like that in start.
Listen now.
You can see partitions in your system, isn't it?
Try to free some space atleast 5gb AFAIK, or 8-10Gb in a partition.
Then go to [www.vmware.com](www.vmware.com)
from there in product>>Free Virtualtion Tools>>VMware Workstation.
Download that.
Good, now download Ubuntu/Kubuntu/Xubuntu/Edubuntu which ever iso you want.
done?
Hmmm start to install VMware Workstation, simply click next till it starts copy installation files, after that enter the key (that's free, you just need a free signup on there site for the key, i can provide you mine, if you need that is) now after clicking Finish, RESTART WINDOWS.
after restarting when its all loaded open VMware Icon on the desktop or in Quick Launch, read the tip, those are very handy ;)
Then click on Start/Create a new Virtual Machine (if you want a custom installation, else you gotta use appliances, and i am not gonna tell that now, if need, just ask) and use the typical option, in Guest Os, Select Linux and from the drop down select Ubuntu and press next and allocate the space that i asked you to make free in the drive in which you made it free, and give its size, Allocate Disk space now is a recommended option,
keep clicking next. till it starts allocating space.
Now when its doen, click EDIT Virtual Machine option and from there select CDROM and there select the radio button before ISO and give it the path to ISO where you download of Ubuntu.
Done?
Close that, and click start Virtual Machine, and there you go....

[TIPS]:
In the setup of Ubuntu choose either the "Use LArgest Free Space" if available or use Manually Edit Partitions and there create a 500-800MB swap by right click the grayed unallocated area and click "NEW" and then create a ext3 partition of remaining space. On the Mounting points screen simply click Forward.

When you are done with installation but wnat to use ubuntu to mount drives and access adata in other partitions, again go to EDIT option and there ADD a HARD DISK and select teh third Physical option and select Disk0 and either choose the partitions(Recommended) to allow or choose entire disk (Risky)

and now you can access other drives in Ubuntu. Using these won't damage you data AFAIK and As far as i have done.

Don't forget to check soundcard in the EDIT,

Still need help? may be going on IM will be better. can't type more longer posts :(

---

### Post by havedampton on 2007-02-08
much appreciate the help...must sleep now.

I'm sure I'll have something more I don't know soon.  Thanks again.

---

### Post by shoaibi on 2007-02-08
No problem, as long as it helps you, its great, i.e. the feeling of sharing....
Go to sleep, and wake up fresh and then read the post again.....
Sweet Dreams ;)

---

### Post by havedampton on 2007-02-08
One more thing, just to clarify.

It looks to me like the instructions above would allow me to run ubuntu on a virtual machine while I'm also running vista.  Is this correct?

I'd prefer to have a choice at startup of which OS to use.

I also need to partition without wiping out my current OS (Vista) and do not have any fancy program like partition magic to do it for me, so I could use any suggestions on how to accomplish this also.

Thanks loads!

---

### Post by hungrybuddha on 2007-02-08
[http://www.tweakvista.com/Article38991.aspx](http://www.tweakvista.com/Article38991.aspx)


i dont know why he's using VM...

---

### Post by havedampton on 2007-02-08
I can see how to resize the partitions, but is there a way to split a partition (because that's what I need to do)?

---

### Post by hungrybuddha on 2007-02-08
There's a program called GParted, 

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

How many partitions do you have currently?

---

### Post by shoaibi on 2007-02-09
Well i would suggest using VMware due to many reasons (if required, could be provided)
and then buddy hmm you wnat the choice at startup? yes for that you gotta install Ubuntu by itself without VM, for that you gotta burn a CD or order Pressed CDs, now it all depends on you.....

For somethings i would recommend toa very good website:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[Read Plan Partitions]

here you will find quite some stuff you need to know , later you can also check ubuntuguide.org for unofficial ubuntu guides....

Either way (i.e. with/without VMware) you gotta free some space and make partitions out of it, detail of that is covered in the first link, still if you need help, make another post...

---

### Post by havedampton on 2007-02-09
just to get back and tell some results

I have a HP Pavilion dv6253cl, AMD Turion 64, nVidia GeForce Go 6150 graphics card

Repartitioning my drive was extremely easy using the disk management tools in Vista.

then the live cd wouldn't boot, and I found out I needed the 64bit version for my AMD 64.
then the 64bit wouldn't boot, but....

I am currently writing this from my laptop running 6.06 (victory!!)

It was really late last night, but i think this is what finally let us install:
press f6 at first menu. delete the "quiet" and "splash" and add "noapic"

I think there may have been more, but that's a start, at least.

now I'm trying to get my screen resolution to the correct 1280 x 800 so everything doesn't look so squished.

thanks for the help

---

### Post by shoaibi on 2007-02-10
Nice going havedampton.
Keep the spirits high.

---

### Post by mr.v. on 2007-02-10
[quote=havedampton]then the live cd wouldn't boot, and I found out I needed the 64bit version for my AMD 64.
then the 64bit wouldn't boot, but....[/quote]
You don't need the 64 bit version to run on a 64 bit processor since your AMD is fully capable of running a 32-bit system. In fact, at this point in time, running a 32bit operating system is somewhat easier than setting up and using a 64-bit system.

While it's nice to fully use the capabilites of your 64-bit OS, there are many issues to deal with and many programs that whine, complain, or flat out refuse to work. Keeping the 32-bit version until you get more experienced with Linux may be the best way to go.

How's Vista by the way? It looks awesome...

---

