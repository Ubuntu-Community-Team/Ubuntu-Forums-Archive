---
title: "Am sure this is probably a simple problem"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Superdelphinus on 2007-11-07
but please be gentle i'm totally new to this!

I installed Ubuntu 7.04 last night using Wubi (a long story concerning the breakdown of my dvd writer!) and the installation itself worked perfectly. On reboot it logged in to Ubuntu through the Grub system perfectly and i was able to log in and the desktop came up correctly.

However, the problem i'm having is that everything works perfectly for about 30 seconds - 1 minute then gradually gets slower and slower until i have to wait 30 seconds for it to even register that i have moved the mouse cursor!

I'm not sure what details about my system/ install are useful to anyone who might be able to help so ask and i will tell.

Please help, you're my only hope...

(Acer Aspire 1670 laptop:
Pentium 4 3.2ghz
512mb DDR Ram
64mb ATI Mobility Radeon 9700
Installed using 10gb of second hard disk via Wubi)

---

### Post by Superdelphinus on 2007-11-07
Would it be solved by installing the ATI propriety linux driver (which supports the mobility 9700)?
If so, how can i install this into Ubuntu when i can't really use the desktop?

---

### Post by sn0wflake on 2007-11-07
Maybe this will help you solve the problem: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Superdelphinus on 2007-11-07
Thanks, i've just been reading that. Don't i need to be able to actually use the GUI for that though? Unless i can install the driver in the 30 seconds or so that i can actually use the desktop before it freezes i'm stuck!

---

### Post by bumanie on 2007-11-07
Not sure if this will be helpful, but you could try booting in via the live cd and using terminal from there.

---

### Post by mivo on 2007-11-07
Right after logging in, open a terminal window and type **sudo top** and watch what happens. Is there a process that uses all of the CPU when your system starts slowing down? Also, does it get better after a while? Tracker and Scrollkeeper tend to be really demanding for some time (this stops when they have done the initial work, usually).

---

### Post by Superdelphinus on 2007-11-07
I can't use a live cd because the dvd writer is knackered :o(
I can't work out whether this is a problem because of Wubi and it's massively running out of cache very quickly or if it's a video problem

---

### Post by Superdelphinus on 2007-11-07
Thanks Mivo - i'll give that a try.
To be fair i haven't left it for a few minutes after it starts to slow down to see if it sorts itself out yet, i'll try tonight.
I feel lost at the moment!

---

### Post by bumanie on 2007-11-07
Sorry. I forgot about that part ie the optical drive issue.

---

### Post by mivo on 2007-11-07
It is possible that you never let it run long enough to finish the initial indexing of your files, so it started fresh every time you tried another time. :) It shouldn't freeze up your system like this, but if I had to bet, I'd put a cookie on Tracker or Scrollkeeper. If it does get better after a while (on a slower system this may take some time), see if it happens again after the next restart. If it does, you can just disable the offender. (*System -> Preferences -> Sessions -> Startup Programs*)

---

### Post by Superdelphinus on 2007-11-07
great thanks, that sounds promising. I think i'll leave it running for a while before swearing at it tonight.

Just quickly - i have the wubi installed on a second hard disk. how easy is it to convert it to a 'proper' install on the same disk without destroying xp (which is on the first HDD)?

---

### Post by mivo on 2007-11-07
> **Superdelphinus said:**
> great thanks, that sounds promising. I think i'll leave it running for a while before swearing at it tonight.

Let us know how it went, please. :)

> ... how easy is it to convert it to a 'proper' install on the same disk without destroying xp (which is on the first HDD)?

Is Ubuntu on its own disk? Regardless, though, since it now has its own partition, you could easily install it again from a CD, but I am not sure if there anything improper about your Wubi installation. But anyway, I only have "pure" Ubuntu boxes, so I can't help with dual-boot questions. (But there should be no troubles as long as you make sure you don't select the Windows disk/partition by accident.)

---

### Post by Superdelphinus on 2007-11-07
At the moment Ubuntu/ Wubi is completely on its own on the second disk. I suppose all i want to do is to extract the Ubuntu bit on to that disk and get rid of the Wubi bit so that the install is 'real' as opposed to 'virtual'. Then i can upgrade to 7.10 from inside Ubuntu because i can't via a disk annoyingly

---

### Post by Superdelphinus on 2007-11-07
Hello - i've just tried it again and left it for a bit. The first boot it just gradually ground to a halt. Second time it worked a bit better in that it didn't totally freeze just got extremely slow. Not sure if it's important but the icon of the battery  and of the two little monitors in the top right kept dissapearing and then reappearing again (usually accompanied by a performance increase) and the clock froze

---

### Post by mivo on 2007-11-07
What did **sudo top** say when your system was slowing down? Any hint what might be causing it? For testing purposes, go into *System -> Preferences -> Sessions -> Startup Programs* and uncheck "Tracker", then reboot.

---

### Post by Superdelphinus on 2007-11-08
I just uninstalled it then reinstalled it giving it 20gb of space rather than 10gb and it's working fine now! Only problems now are getting the wireless card to work and also i don't seem to be able to enable the ATI driver in the restricted drivers option. It enables then immediately blanks out again and says 'not in use'

---

### Post by TeaSwigger on 2007-11-08
Hm have you ever had the hard drive that ubuntu was/is installed on checked in case it's going out (developing bad sectors etc)? Hope you get your dvd drive repaired / replaced (is it really gone, that is have you tried it in ubuntu?) and fix the other niggles, good luck :)

---

### Post by Superdelphinus on 2007-11-08
No not had it checked. Do you not think increasing the size that it installed into was the thing that fixed it?
I don't think it's likely that i'll get the dvd fixed - i googled the drive model number and there were 1200 hits of people with exactly the same problem! I've flashed a firmware upgrade to it and it's still not working. Think i will have to get an external usb drive instead.

---

