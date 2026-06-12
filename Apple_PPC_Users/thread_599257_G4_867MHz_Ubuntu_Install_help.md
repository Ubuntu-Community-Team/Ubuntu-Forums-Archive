---
title: "G4 867MHz Ubuntu Install help"
date: 2007-11-01
forum: Apple PPC Users
---

### Post by ClownyShoes on 2007-11-01
Hi all, 
I have been trying for a couple of days now to install 7.04 on a G4 867MHz machine without success.
I have a pre-existing Tiger install on the drive that I wish to install Ubuntu on.
After searching and reading a few threads, it seemed that I *should* be able to boot into 7.04 Live CD, shrink my OSX partition and install.

I tried both the live CD and alt install versions on Feisty  - both fail at some point.
Live CD goes to white screen of death on default "live" - or just hangs when using live-nosplash-powerpc video=ofonly.

The Alt install gets as far as the partitioner and then hangs.

I was reading another thread where someone had success installing 5.10.
Indeed I can boot and run from Live CD - all works under 5.10.
So I then tried the install version and got as far as the guided partitioning and then I just don't know what to do. Seems all the options will just completely wipe my OSX install. 

I ran the system update thingy under live CD (5.10) and got the message that 5.10 is unsupported so couldn't upgrade over the net.
I'm wondering though - if I just go ahead and install 5.10 - will I be able to upgrade to 7.04 using the CD? 

I have two other machines that will both boot into 7.04 Live CD - no problem.
Is there a way I could install to the G4 machine from one of the others?
Thanks for your time

---

### Post by oswaldkelso on 2007-11-01
I have a  G4 867 also and have experianced the white screen problem. Althought I hear it is posible to repartition from the linux side I would not advise it. here is a link to a tryde and tested method I use
[URL="http://forums.debian.net/viewtopic.php?t=18193"]
http://forums.debian.net/viewtopic.php?t=18193[/URL]

scroll to the bottom

With that method if you have not got an install disk  use  (from memory command+T) to boot off your cloned system then partition your G4.

---

### Post by ClownyShoes on 2007-11-01
Thanks oswaldkelso, 
I will give that a go and report back.

Yay - booted into Target Disk mode on the G5 and the G4 sees both drives.
Now to clone.

---

