---
title: "Breezy, Dapper, Kubuntu, Hoobuntu?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by NT4usB on 2006-05-31
I've only been at this Linux thing for a week or so, still trying to get my box going.
I started with the wrong kernel (-386), upgraded to another (-686), only to find I should be using 686-smp. Not looking forward to upgrading again and fighting the @#^%$ nvidia driver all over...
Ok, they all will work but 686-smp should work best.
Now this Dapper is all the talk on the boards, should I blow off Breezy and get Dapper or just continue trying to get my box going as is?
At the end of the day, all I want is a working PVR I can stick under the TV and record programs...
*so many builds, so little time...*

---

### Post by catlett on 2006-05-31
If you're just starting then go with Dapper before you mess with breezy any more. Dapper will have better hardware detection and better "everything" as far as detection and compatability. If your system was all set and running fine I would say no, for what your doing.

---

### Post by nalmeth on 2006-05-31
You're right, they will all work, only you'll get better performance out of the correct kernel.

I would recommend a fresh install. After a lot of tinkering, an upgrade may bring around some problems.

You can download the current Release Candidate, or wait until tomorrow for the official release. Won't make much difference, as you'll get the update packages regardless.

Are you going to setup MythTV for the PVR business? I've heard it highly recommended.

EDIT: I guess so, just noticed your signature.

---

### Post by MetalMusicAddict on 2006-05-31
[QUOTE=NT4usB]Now this Dapper is all the talk on the boards, **should I blow off Breezy and get Dapper** or just continue trying to get my box going as is?[/QUOTE]
Sorry, I would say yes.
> At the end of the day, all I want is a working PVR I can stick under the TV and record programs...
Are you going to be using MythTV?

---

### Post by ProjectGod on 2006-05-31
personally i consider myself a luddite. so i say stick with breezy. however i'm assuming everything that needs to be functioning right now is functioning correctly. 

the old saying: why fix it if it ain't broken? (why upgrade if you've already got what you need?) :mrgreen:

---

### Post by gr0kzer0 on 2006-05-31
Dapper's the latest release, and when shipit send me my CDs I'll certainly be changing over.  But if you've only just got your Breezy install going, and you're still getting to grips with Ubuntu, it might be an idea to just carry on with that for a while.

I can't quite tell if you'ce actually got your Breezy going yet.  If you haven't got it working, then why not go for a fresh installation with Dapper?  It's the most up-to-date release, it's going to be supported the longest, so if Breezy isn't actually okay on your box, I'd say do the Dapper!

---

### Post by NT4usB on 2006-05-31
Well, as catlett noted, it's not a functioning system yet. Still struggling with cloning the display, and getting MythTV to play nice with the video card.
I've flatlined the box and started over once or twice already. Each time, I get a little better at it. I'm not too far along that changing over would set me that far back.
The current install is probably sufficiently jacked from all my messing around with it that a fresh install would probably be in order anyway...
I'm sort of a stick in the mud when it comes to upgrading though. (heck, I ran NT4 on my CAD box up until last year... If SolidWorks hadn't stopped supporting it, I'd still be running it.)

---

### Post by NT4usB on 2006-06-02
Well... I flatlined it last night and started over.
Already, I'm confused. I installed (I think?) the restricted modules for the 686-smp kernel and then used tseliot's fine skript to get my nvidia going. He warns that restricted modules will be removed using his skript.
How can I tell if it messed with the kernel? I'd hate to get deep into this and have to start over again...

---

### Post by skippy81 on 2006-06-02
OK heres the deal.

tseliot has written numerous excellent guides to installing nvidia drivers.  I will try and clarify the stuff you are confused about:

1) If you want maximum performance (hardware acceleration) you must use the 'nvidia' driver as opposed to the 'radeon', 'nv' and 'vesa' drivers.

2) The 'nvidia' driver is written by nvidia, it is therefore not open source like the rest of linux - for this reason it is included in Ubuntu's repositories, but is placed in a special 'resticted formats' package so that the end user knows that it is not open source like the other drivers.

3) There are 2 ways of getting the nvidia drivers working.  Tseliot calls these method 1 and method 2.  Method 1 basically uses the nvidia drivers which are stored in the ubuntu repositories, it is the simple and quick method - however it does not install the very latest copy of the drivers availiable. I assume this is the method the script you have run uses.  

4) Method 2 allows you to install the newest 'nvidia' drivers, which can be downloaded from nvidia's website.  This method is used by people who want maximum performance and are willing to spend a bit of extra time getting it.

Just stick to tseliots method one.  The only reason he warns you about removing restricted modules is because if you allready have your nvidia drivers installed using the method 1 approach, deleting these drivers will cause your system not to boot. Since you are using a script to sort things out for you, just stop worrying.  Once you have run the script, simply reboot.  IF your card PC is working fine, then be happy unless things arnt working.   Don't worry about messing with the kernel.

---

### Post by NT4usB on 2006-06-02
Thanks skippy81.
Pardon my noobidity...
I couldn't get my card to work with the repository drivers which is why I used method 2. It's worked flawlessly each time I used it to install/reinstall the drivers.
I wondered if tseliot was referring to the nvidia restricted drivers or **all** the restricted drivers you had on your machine. 
He makes reference to it affecting wireless cards which led me to believe it was nuking all the restricted drivers.
...just want to get the build right this time.
*Happy Linux user for going on four weeks now!*

---

### Post by uzi09 on 2006-06-02
personally, i'd recommend just trying a live cd of dapper.

if it works well, and automatically setups ur vid card so that you don't have to go through all that fighting again, y not switch?

---

