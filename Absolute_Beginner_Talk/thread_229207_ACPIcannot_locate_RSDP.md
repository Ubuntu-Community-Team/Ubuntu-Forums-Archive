---
title: "ACPI:cannot locate RSDP"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-04
Upon installing unbunto in this pc i then attempted to do the same in an older pc and got the above message before it proceed to try and set up.It just eventually kept freezing

So discovering that "unbunto" was mabey needing more memory than the old pc had i then downloaded "xubunto"...Which again ,works great on this pc BUT still proceeds to display the "ACPI:cannot locate RSDP" message on other pc

I have googled it and there is some advice for changing boot options but im not to sure how i`d be going about that

Could anybody mabey spell it out for me if it`s possible

The pc in question is a compaq presario 5130 with 128mb ram and 6g drive

Strangely the pc has had xp pro installed on to it somehow(a friend who never knew any better)but dosent have a proper product key(maddness!) 

So it`s formatted to ntfs if that has any bearing on the matter but ive tried and tried just getting the cd up and running ALL to no avail.

ANY IDEAS

edit:Sorry i forgot to mention that after displaying the message it then still try`s to install, freezing just prior to the desktop coming up.

---

### Post by xpod on 2006-08-04
Anyone?????????????????????????

---

### Post by xpod on 2006-08-05
Not sure if this problem was just missed OR mabey im just being a pest with TOO many querys????????????(i always had my hand up in class as a kid too)

I read the "no reply thread" and i hope im understandable?/:confused: ...

I have read,googled and scoured what few articles there are about this but nothing seems to specifically help.

Please could "somebody"...............ANYBODY:(   tell me if im on a "no hoper" here or if there`s something i can do to change whatever is causing that message i get as noted in initial post.

GO ON.......i promise ,i`ll give you`se peace for at least a month:rolleyes: 

:confused: ](*,) :( :-k

PS......The pc in question now has 192mb of ram

---

### Post by tudedude on 2006-08-05
Just a beginner with linux, but actually I get that same message when the box I have Ubuntu on boots. But it boots up and no problems. I know ACPI is a power management specification. Just go into the "Setup" when booting up and disable any power management and see if that make a difference. Good Luck.:)

---

### Post by sdebo on 2006-08-17
I am trying to sort out the RSDP message too.
I am running Ubuntu 6.06 on a PII with 256Mb RAM.  I get that message but again boots up and works perfectly well after that. 
The problem arises when shutting down in that it does not turn off the PC on its own.
My old BIOS is to blame.

As regards it freezing when starting the desktop I would think it is a video card/driver issue.  Try looking up the forums to perform a safe boot.  If that works, it must be the video card drivers.

BTW, does the live CD work for you?  In my case it does, woth no ACPI problems.  It shutsdown well too.  I will try copying settings from the live cd to the install version and see what happens.

---

### Post by samuel_oc on 2007-06-09
I´m also having that kind of problem.
I´ll detail it for the best:
I just got the ubuntu 7.04 CD from the mail, and I was already running the 6.06 LTS version just fine in my PC.
* By the way. It´s a real thrill receiving a free OS CD just by putting your address on a site. Especially becouse I leave in Brazil (it took a long journey from Netherlands to my house). The ubuntu community rocks!!!*
The thing is that when I tried to run the new CD version I got the message:
"[     0.000000] ACPI: unable to locate RSDP"
after that, he goes like "loading..." and then the monitor loses its signal, showing, in the case of my monitor, this message: "Attention! Mode not supported". Like if the monitor data cable was off.

And, yes, when I try to shut down my current ubuntu installation (6.06) it doesn´t shuts by itself. It stops on the message "will now halt...". By the way, this start happening before I got the new CD version. So I guess it has nothing to do with the new version. Except that the old CD version does still work in the LIVE mode. I just tested it.

NOTE: My PC is an AMD Duron-850Mhz, 320MB RAM (AMIBIOS 07/12/2000).

---

### Post by jamesisaacjames on 2007-07-15
Hello to xpod, tudedude, sdebo, and my compliments to samuel_oc.

I also received the "[ 0.000000] ACPI: unable to locate RSDP" when installing on an old computer.
The error message repeated with multiple reboots and the multiple choices of the boot menu.

Having multiple computers, I just left the computer and error message running on the computer, 
while I chose to Google the error message.
I found your messages.
When going back to the [apparently] failed boot of the Ubuntu 7.04,
I found the boot sequence had continued. (!)

I suggest the RSDP search has a timeout or a recovery routine.  
I suspect the timeout is approximately one minute.

The proof?  
I have just started into manual disk partitioning on the subject machine.

Once again, my thanks for your error messages, which delayed me enough for the recovery / timeout to act successfully.

James.

---

