---
title: "[SOLVED] The FUTURE Dual Booting Question"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by Spoken on 2008-04-15
So, as of right now i'm running Ubuntu 7.10 on my laptop, but in a few months ill be heading off to college to get my associate of applied science degree.  The classes i'm taking could potentionally require me to use some programs only found on windows.  

So, my desktops at my house have vista on them already.  my question is, can i use the vista cd that came with them to use for my future dual booting? or will i have to go buy a seperate cd cause the other ones are already registered?

or basically can i use a live cd more then once on more then one computer?

:confused:

EDIT:

ok, so here from my recent research i understand this.

vista home basic - $ 200

Vista Premium - $240

Vista Ultimate - $300

so much $$ for an operating system...i hate windows lol, but i need it for school.

can i still dual boot if my laptop came preloaded with ubuntu?

---

### Post by Spoken on 2008-04-15
.

---

### Post by neurostu on 2008-04-15
I don't think you should have a problem using the Vista install cd.  I would recommend just finding an XP cd. Software will run faster and better in XP then vista.

---

### Post by canadianwriterman on 2008-04-15
My understanding is that you cannot use your Vista CD for more than one installation. Worse, the new service pack for Vista will fail to install if you have a dual booting setup, which has overwritten the MBR.

---

### Post by Spoken on 2008-04-15
but can i use the vista install cd again if ive already used it to install on my other computer?  cause of the registry pin or whatever.

---

### Post by Spoken on 2008-04-15
ok, so, lets say i bought a new install cd, cant i overrigt the MBR with GRUB?

---

### Post by neurostu on 2008-04-15
Yes you can totally dual boot vista and ubuntu, and yes you will need to re-install with grub.  Check around on google for dual booting vista and ubuntu.

check this out:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Golem XIV on 2008-04-15
> **Spoken said:**
> but can i use the vista install cd again if ive already used it to install on my other computer?  cause of the registry pin or whatever.

From the legal standpoint, no you can't.  Your Vista CD was licensed to you for use only on the computer it came with.  (please note that IANAL)

---

### Post by canadianwriterman on 2008-04-15
If you install Vista on the drive first, and then Ubuntu, Ubuntu will overwriter MBR with GRUB and you should be fine. However, early reports indicate that you will not be able to install Vista SP1.

---

### Post by Spoken on 2008-04-15
ok, so here from my recent research i understand this.

vista home basic - $ 200

Vista Premium - $240

Vista Ultimate - $300

so much $$ for an operating system...i hate windows lol, but i need it for school.

can i still dual boot if my laptop came preloaded with ubuntu?

---

### Post by neurostu on 2008-04-15
Do you actually need vista or do you need windows? If you just need windows then get XP. Its cheaper and easier to use (IMHO).

If you need vista then contact the bookstore or IT department at your future school about purchasing an academic version of Vista. I know that my school provides Vista for free and my previous school offered it at a significant discount.

---

### Post by ssadhale on 2008-04-15
Technically speaking you can dual boot irrespective of whether your laptop came with windoze preloaded or ubuntu. I can simplify your thought process. Go through the following equation.

Cost of Ubuntu preloaded laptop (approx 780 $) + Windoze license cost (based on version u want)

Cost of Windoze preloaded laptop (approx 780$) + Ubuntu (free)

Which option sounds better? ;-)

I think you are better off buying a laptop with windows and then add ubuntu on top of that. If you are patient enough to wait for Hardy to be released, you can get something like Wubi - which makes installing ubuntu from within windows a child's play.

Cheers!

---

### Post by neurostu on 2008-04-15
Didn't you read the inital post? He already has ubuntu installed and wants to install windows onto his current machine.

---

### Post by Spoken on 2008-04-15
well your right, i just need windows in general, so that way when im in college any programs that i would need i could get (unless ubuntu becomes fully cross platform compatable) 

ill get ahold of my future school and ask them about it.  now did they actually provide you with a "free" install cd and or discounted?

and secondly, if i already have ubuntu on my laptop, its still possible to dual boot right? cause i keep hearing i need visat on my hard drive first in order for it to work right.

---

### Post by ssadhale on 2008-04-15
Well, if you are a student you might as well get discounted windows version for you. They have copies of windows selling for even 80$ for students.

---

### Post by neurostu on 2008-04-15
So I posted early a link about installing Vista ** AFTER ** Linux.  It really isn't that difficult, Here it is again:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)


My school provides a download link for the dvd; however, every school is different.  

Also I would hold off installing (buying) windows until you know exactly what programs you need and you are sure a linux (FREE) version doesn't already exist.  If you just need MS Office you can try Abiword, Google Documents, Open Office, Star Office, etc... Or even use MS Office in Crossover.

---

### Post by neurostu on 2008-04-15
Also contact your school's Computer Science department and see if they are a member of the MSDN (Microsoft Developer Network). Students of most CS departments can get software FREE through the MSDN.  Meaning if you take 1 CS class you can get a lot of MS software for free!

---

### Post by Spoken on 2008-04-15
Alright, like i said ill get ahold of my school and ask them about the install cd

but im still stuck at this, can i still dual boot my machine even though ubuntu came preloaded on it?

---

### Post by neurostu on 2008-04-15
Yes! Did you read this link: [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

---

### Post by Spoken on 2008-04-15
well, what im worried about is that during my course ill be taking classes that deal with networking and such, thats why i was looking at vista ultimate, cause not only does it have the "home basic" features, it has premium and busniess as well.  And the business version is the one that contains all of the networking and related programs.

---

### Post by neurostu on 2008-04-15
If you don't mind me asking, what are you going to study and where are you going to school?

---

### Post by Spoken on 2008-04-15
btw thanks for that link, it will be very helpful if i do decide to take this route.

---

### Post by Spoken on 2008-04-15
im going to South Plains Jr. College in Levelland TX for 2 years to get my Associates of Applied Science Degree.  Then im going to pursue my "dream job" of being a support administrator.

---

### Post by neurostu on 2008-04-15
If you are worried about having "Networking tools" it sounds like you will probably be studying something CS related.  In that case most of the programs I am aware of focus on the theory and the architecture of networks, and most of them use linux.  From the two schools I've attended both of them (in their CS departments) use Linux exclusively.  

The only things you will need Windows for will be running most 3d party software.  Not for the tools the OS provides. Linux provides tools that are lightyears ahead of those provided by windows

---

### Post by aysiu on 2008-04-15
How about using VirtualBox instead of dual-booting?

---

### Post by Spoken on 2008-04-15
i see, well thats always helpfull to know lol.

i must thank you much so far.  that link you gave me seems to be very helpful for the case that im in.  but likewise, i will call the IT department of south plains and talk to them about the courses that involve the 3rd party programs and tools etc.

---

### Post by Spoken on 2008-04-15
ive heard of virtual box but i have no recalection of what it is exactly, nor how to use it or anything.

what advantages does it have over dual booting?

disadvantages?

and what is your take on my situation on weather of not to have vista and linux on my computer in order to be secure on programs that i could potentially be using in college

---

### Post by neurostu on 2008-04-15
Awesome. Good luck with your studies!

---

### Post by aysiu on 2008-04-15
> **Spoken said:**
> ive heard of virtual box but i have no recalection of what it is exactly, nor how to use it or anything.

what advantages does it have over dual booting?

disadvantages? I've outlined in the link below the advantages and disadvantages as well as the procedures for installing and using it:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by Spoken on 2008-04-15
Edit

---

### Post by barney385 on 2008-04-15
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by tvtech on 2008-04-15
I'd say, drop some coin  buy a copy of XP pro and a liscence for parrallels from ubuntu.com  and do it that way.  whole lot cheeper and easier than dual booting.

---

### Post by Spoken on 2008-04-15
ok but here is the thing.  

Im running Ubuntu right now, it was preloaded on my laptop when i ordered it.  

according to that link, its talking about loading ubuntu inside windows (which i dont have running lol)

---

### Post by Spoken on 2008-04-15
virtual box requires you to have windows already though does it not?

I'm running Ubuntu 7.10 :l

---

### Post by barney385 on 2008-04-15
You install VirtualBox within Ubuntu, then install Winbloze&#8482;, preferably XP.

---

### Post by aysiu on 2008-04-15
> **Spoken said:**
> ok but here is the thing.  

Im running Ubuntu right now, it was preloaded on my laptop when i ordered it.  

according to that link, its talking about loading ubuntu inside windows (which i dont have running lol)
Either way.

You can use VirtualBox to install Ubuntu inside Windows or use it to install Windows inside Ubuntu.

Same principles apply.

---

### Post by Spoken on 2008-04-15
oh i see.  well thank you very much.

I'm going to look into both dual booting and virtual box, call some people, get ahold of my college, and see what would best fit my needs.

i appreciate everyones help.

---

