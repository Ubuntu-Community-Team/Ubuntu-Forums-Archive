---
title: "Uses for G4 455mhz and 600 mg ram."
date: 2012-07-10
forum: Apple Hardware Users
---

### Post by bartos on 2012-07-10
Hi
I just aquired a Mac G4 with 455mhz CPU and 600 mb ram. Managed to install Lubuntu PPC but it is to slow even for my 3 year old son who needs flash.

So I am looking for ideas as how to use this machine. The case is in really good shape. 
My idea is to use it a music server for the back yard. May be have it connect to a NFS share on my main server in the house and connect speakers to the G4. I would use mpd on the G4 and android remote software to control it ( can someone check if mpd is in PPC repo, I am at work)
My only other idea is to gut it and turn it into a pc.

Thanks

---

### Post by Caltac on 2012-07-11
I think that machine would be good for some sort of a home server, but probably nothing too resource-heavy since it's little old!

---

### Post by tormod on 2012-07-11
It is sad that Linux is (has become?) so ressource-intensive. I guess Mac OS 9 would fly on this computer. Maybe you can try out something like Haiku on it?

Well, I would have loaded Mac OS 9 on it and try to sell it to one of these Mac-enthusiasts :) You will be better off with something like $25 Raspberry Pi for performance and support. And energy efficiency! Maybe you can gut it and stuff a Raspeberry Pi or some Android (A10) device inside it...

---

### Post by 2blue on 2012-07-11
I have found som workarounds for youtube with the Firefox "flash video replacer" addon, on a similar specs computer.  It should run youtube, vimeo and other sites smoothly. With the gecko plugin I have aslo been able to stream live TV. It's really not only linux that are to blame for recourse intensiveness, flash streams like youtube have advanced in themselves, and adobe flash is even more heavy than the alternatives. You can also try the html.5 version of youtube and other sites where it is available, it might run. 

;- )

---

### Post by bartos on 2012-07-11
> **Caltac said:**
> I think that machine would be good for some sort of a home server, but probably nothing too resource-heavy since it's little old!

I already have a home server. Thanks
I've installed Lubuntu on it to have modern software but it is still slow as a sloth. Logout dialog takes 5 seconds to come up.

I don't want to get rid of it because it is a great looking case.

---

### Post by bartos on 2012-07-11
The server idea has me thinking to put my server motherboard into this. Since I don't need PCI cards it should be easier to swap in my server board without major mods.

---

### Post by cortman on 2012-07-11
Install Debian PPC. Use the command line installer; you will get the option whether to install a DE and other packages near the end. Select a CLI only and build a GUI from there- use openbox for a solid, lightweight WM, or even Awesome or JWM.
A lightweight WM on a Debian stable OS would fly on a computer like that, I'm guessing.

---

### Post by tormod on 2012-07-12
> **bartos said:**
> I've installed Lubuntu on it to have modern software but it is still slow as a sloth. Logout dialog takes 5 seconds to come up.
I have seen this is horribly slow on faster computers as well. It must be a bug (or bad design) in the LXDE logout function.

---

