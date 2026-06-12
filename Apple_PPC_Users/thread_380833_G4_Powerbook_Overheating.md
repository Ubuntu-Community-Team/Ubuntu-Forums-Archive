---
title: "G4 Powerbook Overheating"
date: 2007-03-10
forum: Apple PPC Users
---

### Post by Speedious on 2007-03-10
I went ahead and installed Ubuntu 6.10 on my 1st Gen 17" G4 Powerbook Alu after feeling I wanted a change. I went through the insanity to get the Airport Extreme (Broadcom) setup and working. I am working on PBButonsd but was stopped dead in my tracks by some system crashes. I found the system to be really hot. I did some forum searching and Google hammering and was able to find lots of references to thermal heating with Powerbooks. 

Before coming in here to the forum and crying like a little girl I have tried to get a solution. After going a blistering 10hour hash session with my poor abused lappy and a friend who has Linux knowledge I am confident I can't make this work. We found that I do not have therm_atd746x running and I am pretty sure my system cooling fan is not on or atleast I know it is not revving up to any speed that would make it audible.

Please keep in mind I have been using Linux now for about 5 days, all GUI. I am a long time Windoze user and a light OSX abuser. If you just throw terminal commands at me it wont help much.

Its 3am. I'm going to bed. Tell me if you need more information.

---

### Post by Speedious on 2007-03-10
Not remembering that when I close the lid the system dosen't sleep I closed the lid and went to bed. Coming back to the system this afternoon I could hear the main cooling fan humming along and the system very hot. 

So, there is something controlling the fan but I don't know what or how to adjust it.
There is a therm_adt746x.ko file in /lib/modules/2.6.17-11-powerpc/kernel/drivers/macintosh.
There are also 4 folders under /lib/modules that look like kernel somethings and all of them have a therm_adt746x.ko. 
2.6.17-10-powerpc
2.6.17-10-powerpc64-smp
2.6.17-11-powerpc
2.6.17-11-powerpc64-smp

Help?

---

### Post by agds on 2007-10-15
Were you able to get this resolved?  Inquiring minds want to know.

---

### Post by Win2Mac2Linux on 2007-10-28
> **agds said:**
> Were you able to get this resolved?  Inquiring minds want to know.

Ditto...  My powerbook always ran hot, but it seems a little hotter than normal and I don't ever hear the fan coming on...

---

### Post by stmiller on 2007-10-28
> sudo apt-get install powernowd

Might need to remove cpufreqd if it is installed.

---

### Post by fredix on 2007-11-17
> 
[QUOTE]
sudo apt-get install powernowd

Might need to remove cpufreqd if it is installed.
[/QUOTE]

hi I was wondering if i could get some help here, as i have 7.10 install on my G4 PowerPC and it just runs flatout until it overheats:(

stmiller, could you tell me how to remove cpufreqd? thanks..../f

or if there is any other fix for this overheating? thanks also..:guitar:

---

### Post by stmiller on 2007-11-17
Hey in the Ubuntu menu go to Settings>Synaptic package manager* Then in Synaptic search for cpufreqd and uninstall it. And then make sure powernowd is installed. You can search for 'powernowd' in Synaptic likewise.

There was some recent chatter on the Debian ppc list about problems with cpufreqd and powerpc, though I'm not sure of any current status on that.

*(I use KDE so I'm not sure where exactly Synaptic is in the Gnome menu if you use Gnome. :( )

---

### Post by fredix on 2007-11-20
thanks stmiller for your help. 

the changes did not seem to adjust the level of heat that the hard drive was making? If anyone has found out any other thing to try would be greatful for some tips.. thanks..../f

---

### Post by maku-d on 2008-02-24
Hey, just thought I'd add a me too to the list. Can have my g4 powerbook on for around twenty minutes before it is insanely hot and has the fan up to full spin. I've tried ubuntu dapper, edgy, and fiesty, fedora 7 and 8 and debian etch. Any new developments? have spent a couple of hours googling but haven't found anything that works yet.

---

### Post by stream303 on 2008-02-24
Have you checked for any runaway processes with top in a terminal?

Or better yet, download and install HTOP and run that from a terminal.

I found that Network Manager was hogging my cpu on my iBook, so I had to disable it.  NM only did this on my iBook, and not on any other machines.  Maybe something else is hogging your cpu?

---

