---
title: "Dual boot ubuntu and Mandriva 2007"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-14
Hi all :D

Just want a simple(ish) answer to what SHOULD be simple to do but I haven't had the courage to try yet:

How do I dual-boot Mandriva Powerpack 2007 32bit and Ubuntu Edgy Eft Beta?!.

I have read various guides, but they often seem so so complex and in-depth, I have shyed away from continuing.

Please tell me it's not impossible - if I *can* do it, then what partitions do I need?

I know I need "/" and "/swap" and (optionally) "/home" but what do I do with my current system: -->

(A) I have "/" and "/swap" and "/home" on my system - taking up ALL drive space

(B) I wish to add Edgy Eft beta as a boot option, so I can fully test Mandriva 2007 *AND* Edgy, without having to wipe one, for the sake of installing the other.

Any help would be much appreciated - I can dual XP and Linux okay, but now I have killed MS off comletely, I have more room.

:) many thanks guys!!

---

### Post by Sef on 2006-10-14
Either you will have to shrink the / or the home partition.  Then you will have room for the other one.  What os is currently installed?

---

### Post by unlokia on 2006-10-14
Currently I have Mandriva Powerpack 2007 32bit but I wanna dual it with Edgy :D

here is a shot of what i got (LOL I am a poet!)

[IMG]http://i61.photobucket.com/albums/h48/unlokia/Screenshot.png[/IMG]

---

### Post by ReaderRat on 2006-10-14
> **unlokia said:**
> Currently I have Mandriva Powerpack 2007 32bit but I wanna dual it with Edgy :D
You could shrink your /home partition to 30 Gig and install Edgy on the remaining 32 Gigs. You do not need another /swap partition, one is enough.
Keep in mind that you can only have 4 Primary partitions.

---

### Post by unlokia on 2006-10-14
Okay got that - but what about LILO or grub etc what do I do then with that??

confused

Need Mandriva as first boot option
[edit]
would Edgy see Mandriva, and cater for it by installing the bootloader *WITH* Mandriva as a boot option???.

My this is confusing lol

---

### Post by ReaderRat on 2006-10-14
Grub should install at the end of your installation, but Ubuntu would be the first boot option. I have seen numerous posts here about how to change the boot order. It's not that hard.

---

### Post by ReaderRat on 2006-10-14
Here is a tag that describes changing boot order ==----> [http://ubuntuforums.org/showthread.php?t=275779](http://ubuntuforums.org/showthread.php?t=275779)

---

### Post by unlokia on 2006-10-14
Ahh great - so basically I just resize /home and tell Edgy Eft live installer to use the EXISTING /swap for its /swap and then use the unused (resized) space on my EXISTING /home, to install oooh bunt ooh :P?!.

Cool - and you think that the Edgy grub install will detect Mandy Riva okay?! heh!

---

### Post by ReaderRat on 2006-10-14
Sorry, your last post confused me. Can you be more clear as to what you plan to do.

---

### Post by unlokia on 2006-10-14
I'd confuse a shrink dude!! :D

Basically ALL I have is Mandriva ok?!

If I resize /home and install Ubuntu to the free bit and set the free space as / with ubuntu, will grub see Mandriva and set it as a bootable choice, even IF ubuntu is No.1 on list i dont care!.

Thanks

---

### Post by ReaderRat on 2006-10-14
Yes. I believe you will need to make a /home for the second distro as well as a / . But it uses the same /swap .

---

### Post by unlokia on 2006-10-14
Ahh ok thanks!!. So do I use the Ubuntu cd I take it, in LIVECD install mode to resize?? obviously I cannot resize a running OS!.

I think I had all of what u said, figured out, but was panicking that grub would mess up my Mandriva install.

I guess I could backup my MBR with dd tho...

**MIND TICKS LIKE BIG BEN ON NEW YRS EVE***

---

### Post by Sef on 2006-10-14
> Ahh ok thanks!!. So do I use the Ubuntu cd I take it, in LIVECD install mode to resize??

That is correct.

---

### Post by unlokia on 2006-10-14
Ahhh YES!!! All working perfectly (as expected) now.... to rename "Linux" to Mandriva :) in Grub


Stuff Wind0z3 this is WAY more fun and MUCH more ethical!!

YAY to Gnu/linux BOOOHISSS To M$ sHaMe 0n You!

....hmmm....

Now if I resize AGAIN... (Said in 'Dexter'-esque accent - [Dexter's Laboratory!]) Maybe I can squeeze good old Suse 10.2 beta in ALSO :D

---

### Post by unlokia on 2006-10-17
Now got a triple boot going - Ubuntu Edgy Knot3 - Kubuntu daily build 16-10-06 and Mandriva powerpack 2007. Talk about FREEDOM OF CHOICE!!! :D:D:D

---

### Post by ReaderRat on 2006-10-17
Ahm proud of yuh....enjoy !!!

---

### Post by unlokia on 2006-10-17
Out of interest, does the partition containing the distro, HAVE to be a primary one?. Obviously I can only have a max of 4 primaries - may try to install 4,5 or maybe 6 distros, in a multi-boot :mrgreen: now that would be FUN!!.

If I could make more logical drives and add the extra distros into that, I could theoretically do MORE :o hehe

---

### Post by ReaderRat on 2006-10-17
Only Primary partitions can be bootable.

---

### Post by unlokia on 2006-10-17
Are you absolutely sure?? how about an extended in a primary??. I read on google, of a guy who managed to get at LEAST 100 distros on multi-boot... goodness KNOW how :-? 

So are you saying that, basically 4 distros is the maximum I can do multi-boot with!?!?!

---

### Post by ReaderRat on 2006-10-17
I believe you are doing an amazing job with three distros. I haven't done that yet. (Oh, And I don't know if the /swap partition is a Primary. You may only have 3 to use.) You will have to find someone else for answers. I'm a newbie, and I'm out of them.

---

### Post by unlokia on 2006-10-17
Ahh okay well that's fair enough!. Hey listen, thanks for your time taken to reply mate - I appreciate it a lot, and I wish you all the very best.

Oh, and the triple boot was virtually automatic - no tweaking needed, just had to make sure mount points didn't conflict across distros, is all!.

:D :D have a great night/day :D

---

### Post by unlokia on 2006-10-18
Great info about partitions and booting etc:

[http://www.vsubhash.com/writeups/multiboot_os.asp]("http://www.vsubhash.com/writeups/multiboot_os.asp")

---

