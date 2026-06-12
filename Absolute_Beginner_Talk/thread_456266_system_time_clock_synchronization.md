---
title: "system time clock synchronization"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-05-27
If I have 2 Edgy machines and if I do a time and date synchronization on both of them, shouldn't they both have exactly the same time after performing that operation ???

Not a synchronization that I do manually but one in which it is supposed to synch with internet server.

They don't !!!

Thanks.

---

### Post by TheRingmaster on 2007-05-27
Are they both sync'd with the same servers?

---

### Post by wpshooter on 2007-05-27
Yes they were.

However I believe I have found the problem.

I was attempting to synch both machines to the one on the listing that is something like gov.cmr.virginia.usa

When I switched both machines to the one in Pennsylvania it worked perfectly.

Apparently the location in Virginia is either temporarily or permanent not working.

Does Ubuntu ever check to make sure that the servers on this listing are still valid ???

Thanks.

---

### Post by paparucino on 2007-05-27
> **wpshooter said:**
> 

Does Ubuntu ever check to make sure that the servers on this listing are still valid ???

I'm not sure, but I think that this is an "user problem". it's his faulty if he supplies wrong informations.
IMHO, of course

---

### Post by wpshooter on 2007-05-27
> **paparucino said:**
> I'm not sure, but I think that this is an "user problem". it's his faulty if he supplies wrong informations.
IMHO, of course

Are you saying that it is the O/S users responsibility to make sure that all of the servers that are on the listing in date & time section are still functional ?    

Thanks.

---

### Post by paparucino on 2007-05-27
> **wpshooter said:**
> Are you saying that it is the O/S users responsibility to make sure that all of the servers that are on the listing in date & time section are still functional ?    

Thanks.
What I mean is that if I (the user) pass the bad information to the OS, I cannot complain if the  OS gives me the wrong answer.
I use Acuweather for Firefox. If I pass informations about stations in Alaska (e.g.) I cannto complain that informations I get aren't related to my country.

---

### Post by wpshooter on 2007-05-27
Virginia is my state, USA is my country !!!

---

### Post by paparucino on 2007-05-27
> **wpshooter said:**
> Virginia is my state, USA is my country !!!
No doubt about it, but are you sure the service is active?

---

### Post by davef1m on 2007-05-27
I think that counts as a distro problem.  If the computer has a list of servers to connect to, and the user tries to pick the close one, you are trying to claim the user is at fault?  Why did the system offer a non-working site to choose?  Better yet, why is the system offering these at all?  It should have pool.ntp.org, and for advanced users, you can put in your own options.  But it doesn't even offer pool.ntp.org.

---

### Post by wpshooter on 2007-05-28
> **davef1m said:**
> I think that counts as a distro problem.  If the computer has a list of servers to connect to, and the user tries to pick the close one, you are trying to claim the user is at fault?  Why did the system offer a non-working site to choose?  Better yet, why is the system offering these at all?  It should have pool.ntp.org, and for advanced users, you can put in your own options.  But it doesn't even offer pool.ntp.org.

Thanks for getting it.

---

### Post by paparucino on 2007-05-28
> **davef1m said:**
> I think that counts as a distro problem.  If the computer has a list of servers to connect to, and the user tries to pick the close one, you are trying to claim the user is at fault?  Why did the system offer a non-working site to choose?  Better yet, why is the system offering these at all?  It should have pool.ntp.org, and for advanced users, you can put in your own options.  But it doesn't even offer pool.ntp.org.
Sorry, but I don't agree :-)
The OS offers the user a list of sites, in a no way it offers you a list of surely WORKING sites. E.g Feisty has been officially released on april. The packages have been released some time before april. The mantainer of that package may have tested all the sites, but, for some reason, one of thse if faulty, down, broken, whatever. 
You cannot complain against the OS nor the mantainer for this.
So it's a "user problem" look for a working site.
Suppose a server for ubuntu repos is down, is this a problem of the maintainer of apt-get, update-manager, synaptic... ?
I don't think so.

---

### Post by TheRingmaster on 2007-05-28
> **paparucino said:**
> Sorry, but I don't agree :-)
The OS offers the user a list of sites, in a no way it offers you a list of surely WORKING sites. E.g Feisty has been officially released on april. The packages have been released some time before april. The mantainer of that package may have tested all the sites, but, for some reason, one of thse if faulty, down, broken, whatever. 
You cannot complain against the OS nor the mantainer for this.
So it's a "user problem" look for a working site.
Suppose a server for ubuntu repos is down, is this a problem of the maintainer of apt-get, update-manager, synaptic... ?
I don't think so.
In no way shape or form is this a "user error". The guy lives in Virginia so out of common sense he would pick the Virginia time server. If that server happens to be faulty, HOW IN THE WORLD IS IT THE PERSONS FAULT???????? The only persons that is to blame here is the person that maintains that particular server. I am sure the maintainer will hear this and will have it fixed soon. There isn't any time frame as you said for a broken server to get fixed. We have no idea what you are talking about.

My 2 cents --- The Ringmaster.

---

### Post by graigsmith on 2007-05-28
if you are having it automatically keep time synced., then it wont be the same until later. linux doesn't suddenly change the clock, cause it would cause problems with logfiles and such.  what it does to change the clock is different.  linux uses a software clock, not the hardware clock.  it makes the seconds faster or slower so that it can reach the proper time.  once it reaches the proper time, it contiues to check, until it knows how much drift is on the clock, then once it knows the drift, it checks the internet less and less.   so basically, it uses the internet to make your system clock run at almost perfect accuracy.

---

### Post by paparucino on 2007-05-28
> **TheRingmaster said:**
> In no way shape or form is this a "user error". The guy lives in Virginia so out of common sense he would pick the Virginia time server. If that server happens to be faulty, HOW IN THE WORLD IS IT THE PERSONS FAULT???????? 

Got to the 2nd post of this thread and read the last line.
The user is complaining against Ubuntu which should have to check the list.
I'm trying to explain that it's no a problem of Ubuntu mantainers, of the package mantainer.
If you see, I wrote user error between signs which, in my country, doens't mean an absolute statement but means, in this case, that since responsability is out of our sight, he cannot complain against anyone, he only must hope the service will be restored asap and in the meanwhile he must use another server.
It's no so difficult

---

### Post by davef1m on 2007-05-28
It's bad design on the part of Ubuntu.  It should default to pool.ntp.org.  On the 'choose a server' list, it should be blank.  If the user thinks they know better, they should have to enter a address manually.  Then they can point it to a machine on their local net, or (with permission) another site on the net.  But otherwise, it should use pool.ntp.org.  Don't even make the user try to pick from a possibly outdated site.  Besides, Ubuntu doesn't even have ntp installed by default - it gets installed when the user tries to select the sync. option.  So now, your telling us that a list that was downloaded from the updated repositories 2 minutes ago, shouldn't be expected to be accurate?  How is a new user expected to deduce that?

---

